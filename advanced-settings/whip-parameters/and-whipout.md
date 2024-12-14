---
description: Publish directly from OBS (or other) to VDO.Ninja without a virtual camera
---

# \&whipout

Sender-Side Option! ([`&push`](../../source-settings/push.md), [`&room`](../../general-settings/room.md))

## Aliases

* `&whippush`
* `&pushwhip`

## Options

Example: `&whipout=bearertoken`

| Value          | Description           |
| -------------- | --------------------- |
| (string value) | bearer token from OBS |

## Details

Added experimental "WHIP" support to VDO.Ninja, which means in the near future you'll be able to publish directly from OBS to VDO.Ninja without a virtual camera. There's some big caveats to it all, so I don't recommend it over the normal method to most users, but we'll see how it evolves.

To publish use: [https://whip.vdo.ninja/bearertoken](https://whip.vdo.ninja/bearertoken)\
To view use: [https://vdo.ninja/?whip=bearertoken](https://vdo.ninja/?whip=bearertoken)

You can also go to [https://vdo.ninja/alpha/whip](https://vdo.ninja/alpha/whip) for a page to help auto-generate basic VDO.Ninja WHIP links for you.

You have to use a version of OBS that contains WHIP support to get OBS to WHIP working. As of April 2023, these are some builds of OBS that support WHIP:\
[https://github.com/obsproject/obs-studio/suites/12263428876/artifacts/649328007](https://github.com/obsproject/obs-studio/suites/12263428876/artifacts/649328007) win (x64)\
[https://github.com/obsproject/obs-studio/suites/12263428876/artifacts/649328001](https://github.com/obsproject/obs-studio/suites/12263428876/artifacts/649328001) mac (arm)\
[https://github.com/obsproject/obs-studio/actions/runs/4711358202?pr=7926](https://github.com/obsproject/obs-studio/actions/runs/4711358202?pr=7926) (others here)

Hopefully WHIP support will be in OBS officially sometime soon. WHIP support is already added to many other applications and services, and VDO.Ninja will do its best to ensure compatibility as the situation evolves.\
\
**UPDATE**: While it's possible OBS v31 fixes this WHIP firewall issue, I do have a custom version of OBS that also has proper VDO.Ninja WHIP support [available for Win64 here.](https://backup.vdo.ninja/OBS_VDO_Ninja.zip) \[[fork](https://github.com/steveseguin/obs-studio)]  This version should let you publish WHIP via VDO.Ninja across the Internet, regardless of Firewall. (This OBS binary was last built November 2024.)

See this video for details how to set up OBS WHIP to VDO.Ninja:

{% embed url="https://youtu.be/ynSOE2d4Z9Y" %}
Publishing from OBS directly to VDO.Ninja
{% endembed %}

A goal for a while has been to allow anyone to drop-in their own Meshcast replacement, using a third-party WHIP/WHEP server/service. That is, publish to a whip-service, and have viewers of the stream get the WHEP-view link, so they can view via WHEP instead of p2p. I've achieved this finally; close enough at least.

There's a few requirements to make it work though, so either an API wrapper is needed or a set of rules needs to be followed:\
\-- If your WHIP server returns an exposed "WHEP" field in the POST response header, with the URL to the WHEP view link, it will use that WHEP link. You just need to then specify the `&whipout` URL on the sender side then.\
\-- This should let you make your own Meshcast service with minimal work; the open-source WHIP API code I released the other day further makes it pretty easy.

I've refined the WHIP service on `vdo.ninja/alpha/?whipview=xxx`, making it as robust as I can I think, so if some third-party WHIP client/app doesn't work with it, it may not an issue with VDO.Ninja. In those cases it will be up to the client to ensure full support of the WHIP specification, else it may not work with VDO.Ninja.

## Related

{% content-ref url="../../steves-helper-apps/whip-and-whep-tooling.md" %}
[whip-and-whep-tooling.md](../../steves-helper-apps/whip-and-whep-tooling.md)
{% endcontent-ref %}

{% content-ref url="and-whip.md" %}
[and-whip.md](and-whip.md)
{% endcontent-ref %}
