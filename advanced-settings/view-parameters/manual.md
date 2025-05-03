---
description: Disables the auto-mixer, allowing for a custom mixer to be used
---

# \&manual

Viewer-Side Option! ([`&view`](view.md), [`&scene`](scene.md), [`&room`](../../general-settings/room.md))

## Details

This is an advanced feature, for primarily developers, who wish to utilize their own auto-mixing code or perhaps are not using VDO.Ninja for video/audio specifically.

`session.rpcs` is an object that can be queried for a list of active receiving peer sessions. `session.rpcs[UUID].videoElement.srcObject` contains video/audio data if available.

## Related

{% content-ref url="../../guides/iframe-api-documentation.md" %}
[iframe-api-documentation.md](../../guides/iframe-api-documentation.md)
{% endcontent-ref %}
