---
description: Pre-configures the selected video device
---

# \&videodevice

Sender-Side Option! ([`&push`](push.md))

## Aliases

* `&vdevice`
* `&vd`

## Options

Example: `&videodevice=BRIO_4K`

<table><thead><tr><th width="150">Value</th><th>Description</th></tr></thead><tbody><tr><td><code>0</code></td><td>disable the video camera automatically. No option to change it during setup is provided.</td></tr><tr><td><code>1</code> | (no value given)</td><td>auto-select the default video camera. No option to change it will be allowed.</td></tr><tr><td>(string value)</td><td>auto-select a video device that has a label containing that same string specified. Whitespaces in names can be replaced with underscores.<br><br>Device IDs can also be used; exact match only in that case.</td></tr></tbody></table>

## Details

It can be changed after the connection has been established.\
![](<../.gitbook/assets/image (101).png>)

Useful for helping a remote guest skip-past the complex setup of their camera/audio.

You can use this option to also disable a guest's camera, potentially allowing for guest connections that have no video or audio. This is a great option if you want to use midi-only transport, add some hidden IFRAME control, or just wanted to text chat.

For a device like an iPhone, you can pass a string value such as `&videodevice=back` to specify the back camera by default. For Android, you might try `rear` instead of `back`, but it will depend on the name the manufacture gave the camera.

When combined with [`&webcam`](and-webcam.md) and [`&autostart`](and-autostart.md), you can have the camera start publishing instantly, often without any user interaction at all. Keep in mind that some browsers will still need to ask for permissions or require a user-gesture for things to function correctly though.

{% hint style="info" %}
See [vdo.ninja/devices](https://vdo.ninja/devices) to see the device IDs and device names. DeviceIDs are specific to VDO.Ninja's domain, while device names are not. The page will also auto-create links for  you, just by clicking on the respective device.
{% endhint %}

When using `&videodevice=videoDevice`, the name matching order sorts based on "NameStartsWith", then "ExactDeviceID", and then finally "NameIncludes". This should avoid the Streamlabs OBS Virtual Cam being selected when you actually want the OBS Virtual Camera being selected, as the two devices both contain `obs virtual camera` in their name.

#### Director's room toggles

Auto-selects the default camera of a guest by adding `&vd` to the guest's invite link.\
![](<../.gitbook/assets/image (126).png>)

Disables the guest's camera by adding `&vd=0` to the guest's invite link.\
![](<../.gitbook/assets/image (122) (2).png>)

## Related

{% content-ref url="../newly-added-parameters/and-vdo.md" %}
[and-vdo.md](../newly-added-parameters/and-vdo.md)
{% endcontent-ref %}

{% content-ref url="audiodevice.md" %}
[audiodevice.md](audiodevice.md)
{% endcontent-ref %}

{% content-ref url="and-nosettings.md" %}
[and-nosettings.md](and-nosettings.md)
{% endcontent-ref %}

{% content-ref url="and-webcam.md" %}
[and-webcam.md](and-webcam.md)
{% endcontent-ref %}

{% content-ref url="and-autostart.md" %}
[and-autostart.md](and-autostart.md)
{% endcontent-ref %}

{% content-ref url="and-device.md" %}
[and-device.md](and-device.md)
{% endcontent-ref %}
