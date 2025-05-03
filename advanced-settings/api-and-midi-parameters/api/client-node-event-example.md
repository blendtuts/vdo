---
description: Simple VDO.Ninja API WebSocket Client Example
---

# Client (node) event example

While I'm a fan of just connecting and seeing what the API outputs, based on different events/actions, here's some code to get you started with basic incoming connection detection.

## Simple VDO.Ninja API WebSocket Client Example

Here's a NodeJS example that demonstrates how to:

1. Connect to the VDO.Ninja API via WebSocket
2. Detect when streams connect or disconnect
3. Periodically poll for stream details

```javascript
const WebSocket = require('ws');

class VDONinjaMonitor {
  constructor(apiKey) {
    this.apiKey = apiKey;
    this.apiServer = 'wss://api.vdo.ninja:443';
    this.ws = null;
    this.connected = false;
    this.streams = {};
    this.reconnectTimeout = null;
    this.pollInterval = null;
  }

  // Connect to the WebSocket server
  connect() {
    console.log(`Connecting to ${this.apiServer}...`);
    
    this.ws = new WebSocket(this.apiServer);
    
    this.ws.on('open', () => {
      console.log('WebSocket connection established');
      // Join with the API key
      this.ws.send(JSON.stringify({ join: this.apiKey }));
      this.connected = true;
      
      // Start polling for details periodically
      this.startPolling();
    });
    
    this.ws.on('message', (data) => {
      try {
        const message = JSON.parse(data);
        this.handleMessage(message);
      } catch (error) {
        console.error('Error parsing message:', error);
      }
    });
    
    this.ws.on('close', () => {
      console.log('WebSocket connection closed');
      this.connected = false;
      this.stopPolling();
      this.scheduleReconnect();
    });
    
    this.ws.on('error', (error) => {
      console.error('WebSocket error:', error);
      this.stopPolling();
      this.scheduleReconnect();
    });
  }
  
  // Handle messages from the WebSocket
  handleMessage(message) {
    // Log all messages for debugging
    console.log('Received message:', JSON.stringify(message, null, 2));
    
    // Handle connection events
    if (message.action === 'guest-connected') {
      const streamID = message.streamID;
      console.log(`Stream connected: ${streamID}`);
      
      // Store stream info
      this.streams[streamID] = {
        connected: true,
        label: message.value?.label || 'Unknown',
        connectTime: new Date()
      };
      
      // You could trigger additional actions here
    }
    // Handle alternative connection event
    else if (message.action === 'push-connection' && (message.value === true || message.value === "true")) {
      const streamID = message.streamID;
      console.log(`Stream connected (via push-connection): ${streamID}`);
      
      // Store stream info or update existing
      if (!this.streams[streamID]) {
        this.streams[streamID] = {
          connected: true,
          connectTime: new Date()
        };
      } else {
        this.streams[streamID].connected = true;
        this.streams[streamID].reconnectTime = new Date();
      }
    }
    // Handle disconnection events
    else if (message.action === 'push-connection' && (message.value === false || message.value === "false")) {
      const streamID = message.streamID;
      console.log(`Stream disconnected: ${streamID}`);
      
      if (this.streams[streamID]) {
        this.streams[streamID].connected = false;
        this.streams[streamID].disconnectTime = new Date();
        
        // Optional: Remove from active streams after a period
        setTimeout(() => {
          if (this.streams[streamID] && !this.streams[streamID].connected) {
            delete this.streams[streamID];
          }
        }, 60000);
      }
    }
    
    // Handle responses to our getDetails requests
    else if (message.callback && message.callback.action === 'getDetails') {
      console.log('Received stream details:');
      
      // The result contains detailed information about all connected streams
      const details = message.callback.result;
      
      if (details && details.guests) {
        // Update our local cache with the latest details
        Object.keys(details.guests).forEach(streamID => {
          if (!this.streams[streamID]) {
            this.streams[streamID] = {
              connected: true,
              connectTime: new Date()
            };
            console.log(`Discovered stream in poll: ${streamID}`);
          }
          
          // Update stream details
          this.streams[streamID] = {
            ...this.streams[streamID],
            ...details.guests[streamID],
            lastSeen: new Date()
          };
        });
        
        // Check for streams that are in our cache but not in the response
        Object.keys(this.streams).forEach(streamID => {
          if (this.streams[streamID].connected && !details.guests[streamID]) {
            console.log(`Stream not found in poll, marking as disconnected: ${streamID}`);
            this.streams[streamID].connected = false;
            this.streams[streamID].disconnectTime = new Date();
          }
        });
      }
    }
    
    // Handle action-specific events
    else if (message.action) {
      switch (message.action) {
        case 'remote-mute-state':
          // Handle remote mute state changes
          if (message.streamID && this.streams[message.streamID]) {
            this.streams[message.streamID].remoteMuted = message.value;
            console.log(`Stream ${message.streamID} remote mute state: ${message.value}`);
          }
          break;
          
        case 'remote-video-mute-state':
          // Handle remote video mute state changes
          if (message.streamID && this.streams[message.streamID]) {
            this.streams[message.streamID].videoMuted = message.value;
            console.log(`Stream ${message.streamID} video mute state: ${message.value}`);
          }
          break;
        
        case 'director':
        case 'codirector':
          // Handle director status changes
          if (message.streamID && this.streams[message.streamID]) {
            this.streams[message.streamID].isDirector = message.value;
            console.log(`Stream ${message.streamID} director state: ${message.value}`);
          }
          break;
      }
    }
  }
  
  // Send a command to the WebSocket
  sendCommand(action, value = null, target = null) {
    if (!this.connected) {
      console.warn('Cannot send command: WebSocket not connected');
      return false;
    }
    
    const command = { action };
    if (value !== null) command.value = value;
    if (target !== null) command.target = target;
    
    try {
      this.ws.send(JSON.stringify(command));
      return true;
    } catch (error) {
      console.error('Error sending command:', error);
      return false;
    }
  }
  
  // Request updated details about all streams
  requestDetails() {
    return this.sendCommand('getDetails');
  }
  
  // Start polling for stream details
  startPolling(intervalMs = 10000) {
    this.stopPolling();
    this.pollInterval = setInterval(() => {
      this.requestDetails();
    }, intervalMs);
    
    // Initial request
    this.requestDetails();
  }
  
  // Stop polling
  stopPolling() {
    if (this.pollInterval) {
      clearInterval(this.pollInterval);
      this.pollInterval = null;
    }
  }
  
  // Schedule reconnection attempt
  scheduleReconnect(delayMs = 5000) {
    if (this.reconnectTimeout) {
      clearTimeout(this.reconnectTimeout);
    }
    
    this.reconnectTimeout = setTimeout(() => {
      console.log('Attempting to reconnect...');
      this.connect();
    }, delayMs);
  }
  
  // Get a summary of connected streams
  getStreamSummary() {
    const connectedStreams = Object.keys(this.streams).filter(id => this.streams[id].connected);
    
    console.log(`\n=== Stream Summary ===`);
    console.log(`Total tracked streams: ${Object.keys(this.streams).length}`);
    console.log(`Currently connected: ${connectedStreams.length}`);
    
    console.log(`\nConnected streams:`);
    connectedStreams.forEach(streamID => {
      const stream = this.streams[streamID];
      console.log(`- ${streamID} (${stream.label || 'Unlabeled'})`);
    });
    
    return {
      total: Object.keys(this.streams).length,
      connected: connectedStreams.length,
      streams: this.streams
    };
  }
  
  // Close the connection
  disconnect() {
    this.stopPolling();
    if (this.reconnectTimeout) {
      clearTimeout(this.reconnectTimeout);
      this.reconnectTimeout = null;
    }
    
    if (this.ws) {
      this.ws.close();
      this.ws = null;
    }
    
    this.connected = false;
  }
}

// Usage example
const API_KEY = 'YOUR_API_KEY_HERE'; // Replace with your actual API key
const monitor = new VDONinjaMonitor(API_KEY);

// Connect to the API
monitor.connect();

// Periodically print a summary of streams (every 30 seconds)
setInterval(() => {
  monitor.getStreamSummary();
}, 30000);

// Handle application shutdown
process.on('SIGINT', () => {
  console.log('Shutting down...');
  monitor.disconnect();
  process.exit(0);
});
```

### How to Use This Example

1. Save this code as `vdo-ninja-monitor.js`
2.  Install the WebSocket dependency:

    ```
    npm install ws
    ```
3. Replace `'YOUR_API_KEY_HERE'` with your actual VDO.Ninja API key
4.  Run the script:

    ```
    node vdo-ninja-monitor.js
    ```

### Key Features

This script demonstrates:

1. **WebSocket Connection**: Establishes and maintains a connection to the VDO.Ninja API
2. **Event Handling**: Detects when streams connect and disconnect
3. **Auto-Reconnection**: Reconnects if the connection drops
4. **Periodic Polling**: Requests updated details every 10 seconds
5. **Stream Tracking**: Maintains a record of all seen streams with their status

You can extend this example to:

* Send notifications when streams connect/disconnect
* Log connection events to a database
* Trigger actions based on specific stream events
* Control streams or layouts based on connection patterns

### Usage on links

Any link type that connects to a stream can use the API parameter to detect the incoming media connection status:

1. **View link**: `https://vdo.ninja/?view=streamID&api=myapikey` - Detects when the broadcaster you're viewing connects/disconnects
2. **Scene link**: `https://vdo.ninja/?scene&view=streamID&api=myapikey` - Shows the video while monitoring connection status
3. **Director link**: `https://vdo.ninja/?director=roomname&api=myapikey` - Monitors all connections in a specific room

Each option enables the WebSocket API that sends events when streams connect or disconnect. The monitoring code works with any of these link types, though director links provide the most comprehensive monitoring if you're using rooms.\
\
The key difference is which connection events you'll receive - view links only report on the specific stream being viewed, while director links report on all room participants.\
\
You can also detect events from publishers, or those pushing media streams, however each publisher may need the `&api` added to detect when they go live. When they disconnect, you may or may not get a notification from them that they are hanging up — it depends on if they do a proper hang-up or a hard-close.
