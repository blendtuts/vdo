---
description: Lets you specify how many rows to use in the VDO.Ninja auto mixer.,
---

# \&rows

`&rows` lets you specify how many rows to use in the VDO.Ninja auto mixer.,



* eg: [https://vdo.ninja/?scene=0\&room=123123123333\&cover\&rows=1,1,1,2\&fakeguests=3](https://vdo.ninja/alpha/?scene=0\&room=123123123333\&cover\&rows=1,1,1,2\&fakeguests=3),
* you'll notice the parameter can take comma separated values, or just 1 value if needed,
* row=1 will be just one row, regardless of how many guests, and row=1,1,1,2 for example will be 1 row if 1 guest, 2 guest, or 3 guest, but two rows (2x2) if 4 guests. If more than than, the guests will squeeze into still just two rows.

<figure><img src="../../.gitbook/assets/image (265).png" alt=""><figcaption></figcaption></figure>

When using `&rows` a negative row value will now center the videos in the row if not a complete row.

* eg: `&rows=1,-2` vs `&rows=1,2`

<div align="left" data-full-width="false"><figure><img src="../../.gitbook/assets/image (264).png" alt=""><figcaption><p>Not-Centered: https://vdo.ninja/alpha/?fakeguests=3&#x26;room=XX&#x26;scene&#x26;rows=1,2</p></figcaption></figure></div>

<figure><img src="../../.gitbook/assets/image (263).png" alt=""><figcaption><p>Centered: https://vdo.ninja/alpha/?fakeguests=3&#x26;room=XX&#x26;scene&#x26;rows=1,-2</p></figcaption></figure>

```
Centered: https://vdo.ninja/alpha/?fakeguests=3&room=XX&scene&rows=1,-2

Not-Centered: https://vdo.ninja/alpha/?fakeguests=3&room=XX&scene&rows=1,2
```
