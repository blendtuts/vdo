# Updates - Speed Test

[speed-and-quality-tests.md](../steves-helper-apps/speed-and-quality-tests.md "mention")

#### October 29

*   Added a new check to the vdo.ninja/check page that will detect if the browser is blocking direct p2p by means of blocking IP leaking.

    * This will help identify users ahead of time who might end up going thru a TURN relay server, when they don't need to be.
    * This won't detect if there is a corporate firewall or VPN is blocking a direct connection, rather if its due to a browser setting or privacy-focused extension.

    <figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### April 21

* Added a max bandwidth (upload / download) test\
  \-- unlike the video test, this just is a classic test looking at network bandwidth\
  \-- it does add another step to the test, so it's overall about 30-seconds longer to complete now (\~4 minutes long)\
  ![](<../.gitbook/assets/image (17).png>)

#### April 13

* Added the number of CPU threads (logical cores) to the stats in VDO.Ninja, as well as the check/results testing page.. (update on alpha & GitHub)\
  ![](<../.gitbook/assets/image (13) (5).png>)

#### January 19

* Speed Test now includes a timestamp, so you can see when the test started.

### 2022

#### October 3

* Fixed a couple issues with the speedtest and [vdo.ninja/alpha/check](https://vdo.ninja/alpha/check) pages -- a recent chrome update deprecated (broke) some stats APIs I was using, along with a new race condition issue caused results to not always save. (It's funny how working code starts to 'rust' over time)

#### September 16

* Added more details to the tech-check test's result page (vdo.ninja/alpha/results?id=xxx), including system detail and the network type. WiFi is of course isn't advised, so if it detects that, it points it out as seen in the photo.\
  ![](<../.gitbook/assets/image (15) (2) (1).png>)![](<../.gitbook/assets/image (17) (2).png>)

#### September 14

* I put together a first version of a tool designed to help with automated tech-checking of guests. Tool is located here currently: [https://vdo.ninja/alpha/check](https://vdo.ninja/alpha/check), although I may move it at some point.\
  \
  The tool is based after the speedtest I have up still, but once the test is complete, it offers a link to the results that can be shared. The results are stored on a server, anonymously, for up to a week, after which they expire and auto-delete.\
  \
  A demo results page can be found here: [https://vdo.ninja/alpha/results?id=steve12345](https://vdo.ninja/alpha/results?id=steve12345)\
  \
  The results include the details found within the speedtest, but also the bandwidth is ramped up from 2500, to 4000, and then to 6000 -- 30-seconds each, for a total of 90-seconds. The test then takes about 90 seconds to complete, and the end it auto-uploads the results.\
  \
  While the guest can send you the link of the results, you can also send the guest a link with the ID pre-set, so you can check the results at a later date without needing the guest's feedback. To do so, just add `?id=xxxx` to the test link. ie: `https://vdo.ninja/alpha/check?id=exampleGuest123`\
  \
  You can create an excel sheet of different links, for different guests, and then email them out to guests, asking that they complete the test before a stream. If there are problems with the guests's connection/computer, you'll be able to resolve them sooner this way.\
  \
  I'd still recommend you do a proper tech check before the stream regardless, but this 'pre-tech-check' can help in cases of larger groups.\
  \
  At some point I'll add a dashboard or notification system to make managing invite links easier, but that will probably be for another day.\
  ![](<../.gitbook/assets/image (1) (2) (6) (1).png>)
