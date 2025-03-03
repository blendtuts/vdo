---
description: >-
  Maintaining a smooth 1080p60 can be tricky, but there are variety of options
  to achieve the desired results
---

# How to screen share in 1080p

### Bandwidth requirements

To maintain a high quality 1080p60 stream, especially if screen sharing game content, you'll want at least 12-mbps to 20-mbps of upload bandwidth.

You'll also need a pristine Internet connection to maintain a low-latency and smooth result; you can test your connect at [https://vdo.ninja/speedtest](https://vdo.ninja/speedtest). High packet loss will limit the possibility of maintaining both low-latency and high quality video; in such a case, you'll need to prioritize one over the other.

## How to create reusable screen-share links

### Push Link (Sender)

[`https://vdo.ninja/?push=SOMESTREAMID&screenshare&quality=0`](https://vdo.ninja/?push=SOMESTREAMID\&screenshare\&quality=0)\
\
Alias:  [`https://vdo.ninja/?push=SOMESTREAMID&ss&q=0`](https://vdo.ninja/?push=SOMESTREAMID\&ss\&q=0)\
\
Copy one of the two links above and **change&#x20;**_**SOMESTREAMID**_**&#x20;into a different name**. The name picked just needs to be a unique alphanumeric value is not already in active use.

You can also add [`&fps=60`](../advanced-settings/video-parameters/and-fps.md) to the link, to attempt to force 60-fps, but the default with [`&quality=0`](../advanced-settings/video-parameters/and-quality.md) is already 60-fps.

### View Link (Viewer)

[`https://vdo.ninja/?view=SOMESTREAMID&videobitrate=10000&scale=100`](https://vdo.ninja/?view=SOMESTREAMID\&videobitrate=10000\&scale=100)\
\
Alias:  [`https://vdo.ninja/?v=SOMESTREAMID&vb=10000&scale=100`](https://vdo.ninja/?v=SOMESTREAMID\&vb=10000\&scale=100)\
\
Copy one of the two links above and change SOMESTREAMID in the same name as you did for the Push Link. You can change [`&videobitrate=10000`](../advanced-settings/video-bitrate-parameters/bitrate.md) to another value if you want to change the bitrate.

### Explanation

| Parameter                                                                         | Explanation                                                                 |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Push Link                                                                         |                                                                             |
| [`&push=SOMESTREAMID`](../source-settings/push.md)                                | Sets a unique stream ID                                                     |
| [`&screenshare`](../source-settings/screenshare.md)                               | Selects screen sharing instead of webcam                                    |
| [`&quality=0`](../advanced-settings/video-parameters/and-quality.md)              | Sets the resolution to 1920x1080p                                           |
| View Link                                                                         |                                                                             |
| [`&view=SOMESTREAMID`](../advanced-settings/view-parameters/view.md)              | Selects the stream ID                                                       |
| [`&videobitrate=10000`](../advanced-settings/video-bitrate-parameters/bitrate.md) | Sets the video bitrate to 10,000-kbps, you can change the value if you want |
| [`&scale=100`](../advanced-settings/view-parameters/scale.md)                     | Tells the system to not scale down the screen share                         |

{% hint style="info" %}
If you have problems maintaining good video quality, you can add [`&codec=av1`](../advanced-settings/view-parameters/codec.md) to the viewer's side to see if it makes the screen share any better. AV1 is a newer codec with better compression efficiency. H264, VP8, and VP9 are other options to try.
{% endhint %}

### Framerate

Screen sharing at 60-fps is the default, but sometimes this does not always work.

You can try forcing 60-fps by adding [`&fps=60`](../advanced-settings/video-parameters/and-fps.md) to the source (sender-side link). If you get an error, you can try using [`&maxframerate=60`](../source-settings/and-maxframerate.md) instead.

Try disabling variable refresh rates, such as those offered by Freesync or G-Sync.

{% hint style="warning" %}
You may not achieve 60 FPS depending on your hardware, the browser or the type of screen share you use or the viewer uses.\
\
Sharing a chrome window or tab is the best way to get 60 FPS consistently. If you share your screen or any other window you might only get 30 FPS.\
\
Screen sharing a "Window" with Chrome (chromium) tends max out at \~42 FPS, while screen sharing via "Entire Screen" tends to make out close to 59 FPS.
{% endhint %}

### Frame rate or resolution

You can use the [`&contenthint`](../advanced-settings/video-parameters/and-contenthint.md) parameter in some browsers to suggestion whether to prioritize frame rate or resolution. Sometimes getting both high isn't possible.

[and-contenthint.md](../advanced-settings/video-parameters/and-contenthint.md "mention")\
[and-screensharecontenthint.md](../advanced-settings/screen-share-parameters/and-screensharecontenthint.md "mention")

These parameters take detail or motion as a value, based on whether you value resolution or frame rate.

### Versus.cam&#x20;

For an e-sports optimized version of VDO.Ninja, with many of the settings pre-configured for 1080p60 streaming, check out [Versus.cam](../steves-helper-apps/versus.cam.md).

It's free and uses VDO.Ninja, while adding a nifty management dashboard for monitoring inbound game streams. The management page makes it easy for you to remotely change resolution and bitrate without modifying the URL while live.

{% content-ref url="../steves-helper-apps/versus.cam.md" %}
[versus.cam.md](../steves-helper-apps/versus.cam.md)
{% endcontent-ref %}

## Still not getting 60-fps?

Using _Entire Screen_ or _Chrome Tab_ capture, instead of _Window_ capture, can increase the frame rate when screen sharing via the Chrome browser:

For some reason, when screen sharing a _Window_ with Chrome, the frame rate is limited to around 42-fps.

If you're needing exactly 60-fps, or are still having issues, continue on for more options:

### Using OBS Studio to capture

#### With the browser and a virtual camera

For the best screen-share results, you can use OBS Studio to capture the gameplay, and bring that into VDO.Ninja via the OBS Virtual Camera. This is an annoying added step, but OBS does a better job at capturing gameplay than the browser does.

Frame rates should be close to 60-fps in this mode, but may vary still vary a bit.

#### Using WHIP from within OBS

An alternative to using the Virtual Camera and browser though is to use a feature in OBS to publish directly to VDO.Ninja.

This is an newer feature it may require a special version of OBS at the moment to work, but WHIP support is now included in OBS v30, but it may be another version or two before OBS supports WHIP properly. \
\
If having issues with using OBS WHIP with VDO.Ninja over the Internet, I do have a custom version of OBS that has proper WHIP support [available for Win64 here.](https://backup.vdo.ninja/OBS_VDO_Ninja.zip) \[[fork](https://github.com/steveseguin/obs-studio)]  This version should let you publish WHIP via VDO.Ninja across the Internet, regardless of Firewall. This OBS binary was last built November 2024, but hopefully future releases of OBS make this custom version redundant. :)\


Check out a demo YouTube video of how to accomplish publishing WHIP into VDO.Ninja:\
[Publishing from OBS directly to VDO.Ninja](https://www.youtube.com/watch?v=ynSOE2d4Z9Y)

This mode should give OBS Studio control over frame rate and bitrate, so with a good connection it should be possible to lock in a solid 60-fps.

{% embed url="https://www.youtube.com/watch?v=ynSOE2d4Z9Y" %}
Using WHIP to publish to VDO.Ninja directly from OBS
{% endembed %}

### Using [\&chunked](../newly-added-parameters/and-chunked.md) mode

A fairly experimental, yet very exciting option to streaming over VDO.Ninja is the use of [\&chunked ](../newly-added-parameters/and-chunked.md)mode.

Chunked mode sends the video and audio over the data-channels, as if streaming via RTMP, rather than via the browser's default method of transmitting video. This provides VDO.Ninja more low-level control over the video, frame rate, and buffering.

This mode is more resistant to packet loss and will not vary the frame rate / resolution during the stream.  It does however mean that if you are connection hiccups or is having problems, it will not be able to react and dynamically reduce quality to continuing streaming.

Chunked mode also uses more CPU than the normal mode and so may not respond well to computers that are maxing out their CPU.

To ensure reliability as a result, a buffer is needed; upwards of 1-second buffer delay may be needed to ensure reliable performance.

To screen share using chunked mode, the following is a sample sender-side link:

```
https://vdo.ninja/alpha/?chunked=2000&screenshare&push=STREAMIDHERE
```

A unique part of chunked mode is that the sender sets the bitrate via `&chunked=N`, where N is the kilobits per second of the video.&#x20;

Viewing the stream is the same as normal:

```
https://vdo.ninja/alpha/?view=STREAMIDHERE&buffer=500
```

[`&buffer`](../advanced-settings/view-parameters/buffer.md) can be used to specify the default buffer delay, which accepts a value in milliseconds. The default may change depending on version of VDO.Ninja, but it's roughly between 500ms and 1s in most cases.  Going below 200ms is not advised unless using it over a LAN.

Please provide request/feedback if you use `&chunked` mode, as it's experimental and still being improved upon.

### Meshcast and servers

You can explore using [`&meshcast`](../newly-added-parameters/and-meshcast.md) and [`&relay`](../general-settings/and-relay.md) as options as well. While it is a server-based method of sending video, it can sometimes allow for 1080p video where network conditions are poor.

Meshcast in particular can help stream 1080p video to multiple viewers at once, if the sender does not have a computer and network capable of doing so on their own.

Meshcast may not always be able to achieve 20-mbps speeds, sometimes only 2 to 3-mbps is possible, so it may not always be the best option for those streaming e-sports.

{% content-ref url="../advanced-settings/screen-share-parameters/" %}
[screen-share-parameters](../advanced-settings/screen-share-parameters/)
{% endcontent-ref %}
