---
description: Some basic options to achieve higher quality video
---

# Even higher quality video

You can customize the capture resolution and playback quality of videos by adding parameters to the VDO.Ninja URL.

### Viewer side options

The default video bitrate of most modern browsers is around 2500-kbps, which is okay, but we can achieve higher video quality if we manually set this to something even higher.

[`https://vdo.ninja/?view=streamid&videobitrate=6000`](https://vdo.ninja/?view=streamid\&videobitrate=6000)

You’ll notice that we added [`&videobitrate=6000`](../advanced-settings/video-bitrate-parameters/bitrate.md) to the viewer’s side and not the publishing side. The viewer gets to control the bitrate; every viewer can set their own custom video bitrate in fact. (For some games, a bitrate of 20000-kbps may be needed, but normally that's overkill though, and can actually increase frame loss if it is higher than your connection can handle.)

You can also play with different video codecs; [`&codec=av1`](../advanced-settings/view-parameters/codec.md#av1) is a viewer side option and tends to offer better colors and quality than the default vp8 or h264 codecs, but av1 will use a up a lot more CPU.

Another viewer side option is [`&scale=100`](../advanced-settings/view-parameters/scale.md), which will disable dynamic fit-to-window scaling optimizations. This is especially valuable if wanting to downscale 4K to 1080p video, as otherwise VDO.Ninja would limit the resolution to the size of the OBS Browser source window. It can also help when there is more than one video on screen, but do note that disabling the auto-scale optimizations to achieve better quality will increase the CPU and network load for all parties.

Sometimes adding some sharpness to the video as a digital video effect in OBS can help improve video quality, especially for video containing fine-text, like a screen share or video overlay. By default text might look a bit soft with VDO.Ninja, and sharpening can resolve it.\
<img src="../.gitbook/assets/image (10) (7).png" alt="" data-size="original">![](<../.gitbook/assets/image (4) (1) (1) (1) (2).png>)

### Sender side options

On the publishing side, the _default_ target resolution is already 1280x720 @ 60-fps, but we can set this higher by adding [`&quality=0`](../advanced-settings/video-parameters/and-quality.md) to the push link. This will have the publisher’s side try to make available a 1920x1080 video stream, if their camera or video device supports it. If not, it will fall back to 1280x720p. [`https://vdo.ninja/?push=streamid&quality=0`](https://vdo.ninja/?push=streamid\&quality=0)

For 1080p60 gaming, you’ll want to set the video bitrate to 12000-kbps or higher, as lower bitrates might cause the frame rate to be quite low otherwise. Otherwise, for talking head-type videos, the default video bitrate is often going to be adequate.

Higher resolution streams, especially 1080p60, requires a LOT of CPU power. Having 4-CPU cores is generally recommend for 1080p60 video streams, and 6 to 8 cores are recommended if you are intending to game at the same time.

Up to 4K or beyond is possible as well, but you'll need to manually specify the capture resolution with [`&width`](../source-settings/and-width.md) and [`&height`](../source-settings/and-height.md) instead, and it will require significantly more CPU and network bandwidth than even 1080p. You can also gently ask for a specific frame rate with [`&maxframerate=60`](../source-settings/and-maxframerate.md), which is sometimes needed with certain iPhones to force 60-fps at 1080p.

### Connection Quality

As VDO.Ninja dynamically also adjusts video resolution and bitrate to match the available Internet connection bandwidth availability, sometimes 1280x720 video resolutions won’t be maintainable. You can run the [https://vdo.ninja/speedtest](https://vdo.ninja/speedtest) to see if you are able to hit at least 2000-kbps, which is about what is needed for smooth 720p video.

Using Ethernet instead of Wi-Fi will also help to ensure the quality and frame loss at these higher resolutions is obtainable. At higher resolutions, frame rates are more likely to be unstable and the resolution might be throttled to something lower. Packet loss will impact the quality of a video stream quite a bit, and in rare cases, you may need to use [`&relay`](../general-settings/and-relay.md) or [`&meshcast`](../newly-added-parameters/and-meshcast.md) mode to assist in overcoming network throttling or routing issues.

### Group Room Settings

When in a group room, specifically as a guest or director sharing video with another guest, the video will be limited to 500-kbps by default.

The director can increase the total room bitrate using a slider under the room settings menu; the button for is found in the director's lower menu bar.

You can also use [`&totalroombitrate=4000`](../advanced-settings/video-bitrate-parameters/totalroombitrate.md) to set a higher room bitrate via the URL, as well as experiment with other bitrate options or trying out [`&meshcast`](../newly-added-parameters/and-meshcast.md). Setting the room bitrate too high though can cause everyone in the room to have problems, specifically with overloaded CPUs or network bandwidth saturation. 500-kbps is the default for a reason.
