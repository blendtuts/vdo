---
description: Disables screen-sharing as an option
---

# \&webcam

Sender-Side Option! ([`&push`](push.md))

## Aliases

* `&wc`

## Details

Automatically selects the Share your Camera option and hides the screen-share button in the control bar.\
![](<../.gitbook/assets/image (38).png>)

{% hint style="danger" %}
Do not use while on a director page to autostart a camera; `&autostart&vd=video_device` should handle that.
{% endhint %}

If you would still like the guest to have access to the screen-sharing button once they have joined the call, you can force it to appear with the [`&ssb`](../advanced-settings/settings-parameters/and-screensharebutton.md) option. The [`&webcam`](and-webcam.md) option by default will hide the screen-share button otherwise.

Starting with [v19](../releases/v19/) of VDO.Ninja, there is also the [`&webcam2`](../newly-added-parameters/and-webcam2.md) option; a minor UI variant that requires an additional button press, but more clearly preps the guest to the fact they will be sharing their webcam.

## Related

{% content-ref url="screenshare.md" %}
[screenshare.md](screenshare.md)
{% endcontent-ref %}

{% content-ref url="../newly-added-parameters/and-webcam2.md" %}
[and-webcam2.md](../newly-added-parameters/and-webcam2.md)
{% endcontent-ref %}
