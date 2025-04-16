---
description: Some ideas on how to reduce total system load on a vMix system using VDO.Ninja
---

# vMix High CPU

## vMix CPU Load Optimization Guide

vMix is a powerful studio mixer software, although some users find the CPU load can get high during operation. This guide provides optimization techniques to reduce resource usage, primarily focused on vMix but potentially applicable to other studio mixing software.

### Browser Source Optimizations

* Browser sized at 1920x1080 can stress vMix out; try 1280x720 or lower to reduce the total load.
* Ensure GPU hardware acceleration is enabled; particularly for the browser source.
* Using the H264 codec may reduce CPU; adding `&codec=h264` to the view link may help.
* Disabling de-interlacing, sharpening, or aliasing of the browser source might free up some load.

### Alternative Capture Methods

* Electron Capture or Vingester.app can be used instead of the vMix browser source; they can use window capture, which can reduce the CPU load.
* If you have a spare computer, Vingester.app has a VDO.Ninja to NDI output option, which can perhaps help with distributing load if the browser source is causing issues.

### Frame Rate & Resolution Adjustments

* Lowering the frame rate of the browser source and incoming VDO.Ninja videos might help reduce CPU load. `&maxframerate=30`, for example, on the guest link can help cap the frame rate.
* The director of a room can adjust settings of incoming videos via the video settings options under advanced settings. This includes the max resolution, frame rate, and aspect ratio of incoming videos.

### Hardware & Driver Optimizations

* Updating your graphics card drivers can sometimes help.
* In the performance settings, if you enable advanced settings at the bottom, there is a "high output performance mode" option. For users with Nvida 1080 cards and above, it seems to significantly reduce both render time and GPU usage with no obvious drawback. I assume it uses features not available at all on older cards, but vMix doesn't document what it does, so hard to say for sure. (The only official word was a release note "Added "High Output Performance Mode" in Settings -> Performance. Improves render time when outputting 4K60 video when used with high end graphics cards. (GeForce 1080+)" but for myself and everyone else reporting trying it on forums, it had a big impact at 1080p and slower fps as well,)

### VDO.Ninja Specific Optimizations

* If acting as a VDO.Ninja director, consider hosting the director on a different computer than vMix. If not possible, consider using `&meshcast` with the director's link to use `&meshcast` to help reduce the CPU load when in larger group rooms.
* Try to use your local camera as a source in vMix, rather than bringing your local video into vMix with VDO.Ninja. Using a virtual camera, like Snapcamera, OBS Virtual Camera, Manycam, or such can allow a webcam to be accessed using the browser and vMix at the same time.
* Avoid using multiple group scene link, unless solo-view links. Instead, consider using the VDO.Ninja mixer app to use a single group scene link, switching between different layouts using the mixer interface. (The Mixer app is relatively new, as of May 2022, so still undergoing feature enhancements).

### Additional Techniques

* Consider using a dedicated streaming PC for more demanding productions
* Close unnecessary background applications to free up system resources
* If possible, run vMix from an SSD rather than a traditional hard drive
* Monitor resource usage with Windows Task Manager to identify bottlenecks
* For network-intensive setups, ensure you have adequate bandwidth and a stable connection

There are additional other options available to reduce CPU / GPU / Network load when using VDO.Ninja; this list is specific to vMix issues.
