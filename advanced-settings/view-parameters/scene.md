---
description: Defines the link to be treated like a scene
---

# \&scene

Viewer-Side Option! ([`&room`](../../general-settings/room.md))

## Aliases

* `&scn`

## Options

Example: `&scene=2` or `&scene=choosethename`

| Value                   | Description                                             |
| ----------------------- | ------------------------------------------------------- |
| `0` \| (no value given) | auto-add all videos to the scene; they can't be removed |
| `1`                     | empty by default; manually add videos in                |
| (string)                | like `&scene=1`, but videos are not preloaded           |

## Details

{% hint style="info" %}
Must be used in conjunction with the [`&room`](../../general-settings/room.md) parameter.&#x20;
{% endhint %}

By adding `&scene` to a room URL, it tells VDO.Ninja that this is no [`&push`](../../source-settings/push.md) connection.

`&scene=0` by default has all videos in the room automatically added to the scene. They cannot be removed.

* `&scene=1` by default has no videos added to the scene. Videos need to be added manually by the director. Videos not yet added to the scene are connected, and streaming at around 400-kbps, so when they become active they appear immediately. Bitrate will ramp up after a second to the target bitrate of, normally, 2500-kbps or whatever is set via the URL.\
  ![](<../../.gitbook/assets/image (106) (1).png>)
* `&scene=2` is like `&scene=1`, except the video streams that are not yet added to the scene are disabled with 0-bitrate used. They are connected, but not actively streaming any video data, so it takes a moment longer for videos to appear once added.
*   `&scene=N`, where `N` is a string or integer - it's just like `&scene=2`. There are buttons marked S3, S4, .. S8 in the director's room to control these scene types. If they are not already there, new buttons for them will be created automatically when used. See the video below.\


    <img src="../../.gitbook/assets/image (1) (2) (1) (1) (2).png" alt="" data-size="original">
* When using a scene, if you manually specify a video via the [`&view`](view.md) parameter, it automatically is added to the scene.
* Audio of videos in scenes can be controlled by the director: volume and mute are options.
* In [v17.2](broken-reference) of VDO.Ninja, if using [`&view`](view.md) in a scene link, the director won't be able to remotely control the scene. This applies to solo links.
* In [v18](../../releases/v18/), you can create custom scenes, as per the video below.

{% embed url="https://www.youtube.com/embed/axgIqPcHExQ" %}

### Optimize scene performance using \&optimize=0&#x20;

If using a normal manual scene, such as \&scene=3, you can add [\&optimize=0](scene.md#alternative-using-and-optimize-0) to the scene URL to enable a mode that is similar to \&solo. It's one of a few different ways to have permanent generic scene links that you can place specific guests into with varying stream IDs. There's also slots, however \&optimize=0 is tweaked for low CPU and network usage, at the cost of a slight added delay in adding a guest to the scene

## Related

{% content-ref url="../../general-settings/room.md" %}
[room.md](../../general-settings/room.md)
{% endcontent-ref %}

{% content-ref url="../mixer-scene-parameters/and-solo.md" %}
[and-solo.md](../mixer-scene-parameters/and-solo.md)
{% endcontent-ref %}

{% content-ref url="../video-bitrate-parameters/optimize.md" %}
[optimize.md](../video-bitrate-parameters/optimize.md)
{% endcontent-ref %}
