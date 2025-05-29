---
description: Attempts to show the mouse cursor on screen shares
---

# \&screensharecursor

Sender-Side Option! ([`&push`](push.md))

## Aliases

* `&cursor`

## Details

Adding `&screensharecursor` to a source link attempts to show the mouse cursor on screen shares.

This flag is introduced in [v18.4](../releases/v18/), but it's largely useless currently due to lack of support from most browsers.

The default cursor state in VDO.Ninja is to not show a cursor, but Chrome/Firefox will still add a cursor overlay in regardless.

If sharing a Chrome tab, Chrome adds the cursor in only when that tab is active.

According to the web spec, we should be able to control the visibility of a cursor, but we can't. Not yet.

You can see this link to tinker with different settings easily, to validate the problem:\
[https://www.webrtc-experiment.com/getDisplayMedia/](https://www.webrtc-experiment.com/getDisplayMedia/)

Generally, to have better control of the cursor, maybe instead capture the screen with OBS and bring the video into VDO.Ninja as a virtual camera.\
For information on alternative ideas on how to hide or show the cursor, you can see the following article.

{% content-ref url="../common-errors-and-known-issues/cursor-shows-when-screen-sharing.md" %}
[cursor-shows-when-screen-sharing.md](../common-errors-and-known-issues/cursor-shows-when-screen-sharing.md)
{% endcontent-ref %}

If none of this is working you might try [YoloMouse](https://store.steampowered.com/app/1283970/YoloMouse/) on Steam:\
[https://store.steampowered.com/app/1283970/YoloMouse/](https://store.steampowered.com/app/1283970/YoloMouse/)

## Related

{% content-ref url="../general-settings/and-nocursor.md" %}
[and-nocursor.md](../general-settings/and-nocursor.md)
{% endcontent-ref %}
