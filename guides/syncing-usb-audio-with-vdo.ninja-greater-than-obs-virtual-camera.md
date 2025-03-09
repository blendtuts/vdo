---
description: >-
  Syncing your USB microphone in OBS with the incoming VDO.Ninja stream is
  pretty straight forward.
---

# Syncing USB audio with VDO.Ninja -> OBS Virtual Camera

## Connecting OBS to a Virtual Audio Cable with Delay

Here's how to sync your audio in OBS Studio with an incoming VDO.Ninja video source, along with how to route the audio through a virtual audio cable into other applications.\
\
Combined with the OBS Virtual Camera output, you can use VDO.Ninja (eg: via iPhone), OBS Studio, and a USB microphone as a wireless camera in other applications.

### Step 1: Install a Virtual Audio Cable

We need a virtual audio to route the audio from OBS to our external application

There are a few free options for macOS:

* **BlackHole** (recommended): Open-source virtual audio driver
  * Download from: [https://github.com/ExistentialAudio/BlackHole](https://github.com/ExistentialAudio/BlackHole)
  * Install via Homebrew: `brew install blackhole-2ch`
* **Soundflower**: Another free option, though less actively maintained
  * Download from: [https://github.com/mattingalls/Soundflower](https://github.com/mattingalls/Soundflower)

For Windows:

**BlackHole** (recommended): Open-source virtual audio driver

* Virtual Audio Cable: Popular onationware for Windows
  * Download from [https://vb-audio.com/Cable/](https://vb-audio.com/Cable/)

### Step 2: Configure OBS Monitor Output

1. Open OBS
2. Go to **OBS Preferences** (or Settings) → **Audio**
3. Under "Advanced," find the "Monitoring Device" dropdown
4. Select your virtual audio cable (e.g., "BlackHole 2ch")
5. Click "Apply" and "OK"

### Step 3: Enable Monitoring for Your Audio Source

1. In OBS, locate your audio source in the "Audio Mixer" panel
2. Right-click the audio source → **Advanced Audio Properties**
3. Find your audio source in the list. (eg: a USB microphone.)
4. Set "Audio Monitoring" to "Monitor Only" or "Monitor and Output"
5. Click "Close"

### Step 4: Add Audio Delay (200ms)

1. In OBS, locate your audio source in the "Audio Mixer" panel
2. Right-click the audio source → **Advanced Audio Properties**
3. Find your audio source in the list
4. Look for the "Sync Offset" column
5. Enter "200 ms" in the field for your audio source
6. Click "Close"

### Step 5: Verify the Setup

Your audio should now be:

1. Captured in OBS
2. Routed through the virtual audio cable
3. Delayed by approximately 200ms, but you may need to adjust this to ensure perfect sync.
4. Available as an input source in other applications

You can select the virtual audio cable (VAB, BlackHole, or Soundflower) as an input in any other application to receive the delayed OBS audio. Works to sync your audio with an incoming VDO.Ninja video stream.
