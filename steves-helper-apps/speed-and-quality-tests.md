---
description: Video streaming quality test
---

# Speed and Quality Tests

{% embed url="https://vdo.ninja/alpha/check" %}
[https://vdo.ninja/alpha/check](https://vdo.ninja/alpha/check)
{% endembed %}

## VDO.Ninja Speed and Quality Testing Tools

VDO.Ninja offers specialized testing tools to evaluate your connection quality for video streaming, focusing on metrics critical for WebRTC performance that standard speed tests don't measure.

### Speed Test

**URL:** [**https://vdo.ninja/speedtest**](https://vdo.ninja/speedtest)

The Speed Test provides real-time feedback on your WebRTC connection quality:

* Tests your camera or screen-sharing streaming performance
* Visualizes critical metrics with live graphs:
  * Bitrate (kbps)
  * Buffer delay (ms)
  * Packet loss percentage
* Allows testing against different global regions
* Provides detailed logs of connection statistics
* Supports variable bitrate testing (low/high/default)

This tool is ideal for quick diagnostics and troubleshooting your own setup before important streams.

### Automated Check Test for pre-testing guests

**URL:** [**https://vdo.ninja/check**](https://vdo.ninja/check)

The Check Test runs comprehensive automated tests of a user's system and connection:

* Conducts network bandwidth measurements via Cloudflare
* Tests camera and microphone access
* Performs automated testing at increasing bitrates (2500 → 4000 → 6000 kbps)
* Takes approximately 90 seconds to complete
* Automatically stores results on the server for up to 7 days
* Generates shareable results links

Pre-checking guests days before a live stream is crucial for identifying and resolving technical issues in advance, preventing embarrassing on-air failures and giving production teams adequate time to implement solutions without the pressure of an imminent broadcast.

#### Key Features:

* **Shareable Results**: After completion, provides a link to results that can be shared with stream organizers
* **Pre-assigned IDs**: Use `?id=xxx` parameter to pre-assign test IDs (example: `https://vdo.ninja/check?id=exampleGuest123`)
* **Screening Tool**: Ideal as a pre-tech-check for guests before important streams

### Results Viewer

**URL:**[ **https://vdo.ninja/results?id=xxx**](https://vdo.ninja/results?id=xxx)

View comprehensive test results including:

* Average video bitrate
* Buffer delay (video latency)
* Packet loss statistics
* CPU/network limitation indicators
* Browser and device information
* Codec support details

### Why Packet Loss Matters

Packet loss is critical for WebRTC video quality but is not measured by standard speed tests. Even small amounts of packet loss can cause:

* Video freezing
* Audio dropouts
* Quality degradation
* Increased latency

The VDO.Ninja tests specifically measure packet loss percentages, with ideal results being under 0.1% and problematic levels exceeding 1%.

These tools are essential for properly evaluating streaming readiness, especially when screening multiple participants before important broadcasts.

<figure><img src="../.gitbook/assets/image (1) (1) (4).png" alt=""><figcaption></figcaption></figure>

Testing regions for VDO.ninja/check\
[https://vdo.ninja/regions](https://vdo.ninja/alpha/regions)

There is also another Speed Test option here:\
[https://vdo.ninja/speedtest](https://vdo.ninja/speedtest)

## Updates

{% content-ref url="../updates/updates-speed-test.md" %}
[updates-speed-test.md](../updates/updates-speed-test.md)
{% endcontent-ref %}
