# Updates - Native mobile apps

[native-mobile-app-versions.md](../steves-helper-apps/native-mobile-app-versions.md "mention")

#### February 5

* Published an update; fixes a room issue. On Apple and Google App stores

#### January 26

* Updated the Android native app and iOS native app, which finalizes the password support
  * Available on the Play Store and App Store
  * This includes the addition of client-side encryption for handshake messaging
  * Passwords will work with just the VDO.Ninja hosted site at the moment, unless you adjust your salt in your self-hosted index.html to match

#### January 8

* Released the native Android version of VDO.Ninja to the Google Play store. (It's rolling out slowly; 20% roll out completed, with the rest expected in the next 24hr)
  * Also includes password support, as mentioned above for iOS
  * Also includes some screen share fixes, but more might still exist.
* Also updated the Google Drive hosted APK for those looking to sideload instead
* Also the GitHub repo for the code is updated (vdon\_flutter), for those looking to contribute or self-build
* I pushed an update for the iOS VDO.Ninja native app to the Apple app store. It was approved, so should be available. If you have problems with it, let me know. The main change is the option to use passwords now, but I made some minor fixes to the screen sharing workflow also. I'm hoping it fixes some screensharing issues as well, but that might be too hopefully.

#### January 5

* I've built a test version of the VDO.Ninja Android native app, which now should support passwords. I've yet to do proper testing of it, but if you want to give it a shot, I welcome feedback as to whether it worked or not for you:
  * [https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view?usp=drive\_link](https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view?usp=drive_link)

### 2023

#### September 13

* A new version of VDO.Ninja for iOS has finally been published to the Apple App Store\
  \-- Has the recent camera-zoom support added\
  \-- Also has forced-landscape mode support (I had to wait until iOS 17 launched to be able to release it)\
  [https://apps.apple.com/app/vdo-ninja/id1607609685?platform=iphone](https://apps.apple.com/app/vdo-ninja/id1607609685?platform=iphone)

![](<../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)

#### September 10

* Zoom-in/out support added to the native VDO.Ninja app, however this change still needs to be rolled out. Available on Google Play; the App Store update may be a couple weeks however. (once iOS 17 launches)\
  \-- Zoom is controlled with up/down swipe gestures; similar to how it is with the web app, but maybe a bit more stable.

#### August 30

* Updated the Android app with a "[force landscape](../advanced-settings/mobile-parameters/and-forcelandscape.md)" option\
  ![](<../.gitbook/assets/image (10) (1) (1).png>)\
  [https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view](https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view)\
  \-- I'll submit it to the Google play store in a little bit. The iOS version might be a while tho.

#### August 23

* The Android native app has been updated to allow a custom turn server to be specified. It's live on the play store now.\
  \-- Also added geo-routing for the official turn servers to the native app, so the closest turn server to you will be used if possible now (if needed).\
  \-- General framework updates applied as well, including a higher minimum android target that was required.\
  \-- An update to the iOS version will take longer to get out; the code's updated, but I can't publish to the store just yet.

#### July 23

* I pushed out v19 of the Android native app version of VDO.Ninja (its live now).\
  \-- Fixed some menu bugs related to scrolling\
  \-- Stream ID and room ID will now replace spaces and special characters with underscores\
  \-- Added a button that will show users a "Help Guide" page, with basic instructions\
  \-- The "stream ID" field now says "stream ID (optional)", to help with avoiding some user confusion about how to get a stream ID\
  \-- And as previously mentioned with the Android version, other features now include an optional web-view version of VDO.Ninja, fixed Discord support link, fixed scrolling support, and the stream/room IDs are parsed now to correct reject special characters.

#### July 17

* Updated the Android native app client. It should be live on google play?\
  \-- Added an option to load the VDO.Ninja web client from within the native app; no tabs or URL bar. (it stops working tho if you background the app.)\
  \-- Made the Discord Support link open Discord directly, if installed, to make it easier to use.\
  ![](<../.gitbook/assets/image (5) (4).png>)![](<../.gitbook/assets/image (6) (7).png>)

#### July 13

* This week the Android and iOS apps were updated; mainly fixing errors, including the screen sharing on iOS not working correctly. iOS update specifically just went live.

#### July 1

*   I pushed an update to the Google Play store with a BETA (open test) release of the android native app (for VDO.Ninja).

    \--- It fixes an issue where if more than 5 cameras listed, additional cameras are blanked out and not available. This also often blocks the mic-only option, as its typically listed last.\
    \--- Some additional library and null-safety updates applied to this beta build also, so it might be buggy -- hence why its going to beta testing first.\
    \--- I'm not sure when the beta will be "approved" for download, but it should be available soon if you've signed up for the beta in the App Store. Please report issues and I'll try to have it available for mass production download shortly after.

\*\*\* seems to be live now

#### May 7

* I have updated the **iOS** native app to have **system-wide screen sharing support**, rather than just in-app screen sharing. (Android already had it).\
  \
  The iOS beta here: [https://testflight.apple.com/join/KnzvY7JO](https://testflight.apple.com/join/KnzvY7JO) (version 2.0.13)\
  \
  Audio for both android and iOS is still from the microphone, and not the internal system audio. I'll try to fix that, but it's quite the challenge for me. It probably wouldn't be too challenging for a more experienced mobile developer to get working though, along with perhaps HDMI support.\
  \
  The app code's repo is here, [https://github.com/steveseguin/vdon\_flutter](https://github.com/steveseguin/vdon_flutter), if you wanted to pull and build it yourself. Ill continue to work on it this weekend, improving the UI/UX, and maybe have whatever progress I make then be pushed to the public live app store during the work week. There's some additional features and polish I want to get in before doing the final app submission.\
  \
  \[update; the beta link should be live now]

#### April 9

* Updated builds of the VDO.Ninja native app for Android and iOS are now LIVE on both Google Play and iOS App stores. These new versions allow for use with fully self-hosted deployments, a mic-only mode, and general WebRTC lib updates.

#### April 3

* Added an audio-only option to the VDO.Ninja native app. For now, it's available for Android via sideloading, with the app store versions being updated later on.\
  [https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view?usp=share\_link](https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view?usp=share_link)\
  \
  ![](<../.gitbook/assets/image (180).png>)\


#### March 21

* Updated the Android app to support offline/fully-self-hosted deployments of VDO.Ninja, by request.\
  \-- just click the "Advanced" toggle on it setup page, then enter your custom WSS address in the field.\
  \
  Until I push this into the Google Play / App store, you can grab the sideloadable APK here: [https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view?usp=share\_link](https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view?usp=share_link) \
  \
  (btw, I am very much welcoming any experienced help in adding USB/HDMI support to the native app)

#### January 31

* &#x20;The v3 update for the iOS native app has been approved and is now available.

#### January 30

* Updated the iOS/Android version with a newer version 2.0.9, which contains some improvements for manual disconnection/reconnection. (also disconnects faster now when using alpha)\
  The Android update is live now, while the Apple update is still pending store approval.\
  ![](<../.gitbook/assets/image (7) (1) (1) (3).png>)

#### January 21

* I pushed an update for the iOS native app of VDO.Ninja earlier and it just got approved. Mainly added reconnection fixes, along with publish-to-room support.\
  ![](<../.gitbook/assets/image (2) (10).png>)

### 2022

#### December 8

* Updated the android native app to have better re-connection smarts; if you lose the peer connection due to an IP address change or such, it should now reconnect. Can't promise it will handle more aggressive networking issues though.

#### November 14

* I updated the native Android app for VDO.Ninja to include support for publishing into a VDO.Ninja room, and fixed a couple UI bugs, along with improved 1080p toggle support.\
  \-- Note: If using a room, you will need to still add [`&password=false`](../advanced-settings/setup-parameters/and-password.md) (`&p=0`) to all the guests/scenes, as I haven't added password support to the native app yet.\
  \-- You can download it directly here: [https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view?usp=share\_link](https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view?usp=share_link)\
  or in the Google Play Store:\
  [https://play.google.com/store/apps/details?id=flutter.vdo.ninja\&hl=gsw\&gl=US\&pli=1](https://play.google.com/store/apps/details?id=flutter.vdo.ninja\&hl=gsw\&gl=US\&pli=1)\
  ![](<../.gitbook/assets/image (6) (5).png>)&#x20;

#### May 27

* Got the native iOS app into the app store. (crude, but finally got it accepted.) [https://apps.apple.com/us/app/vdo-ninja/id1607609685](https://apps.apple.com/us/app/vdo-ninja/id1607609685)
* The native iOS app has the ability to turn the torch light on, and it _might_ support more than two cameras, but that's untested. It also has "screen share" support, but currently it only works within the VDO.Ninja app itself -- switching apps stops the screen capture. Overall, there's not a lot of reason to use the native app, but I'll keep it updated with new features as they become available to me.

#### May 12

* Forgot to mention this, but I did get around to pushing the Android native app version of VDO.Ninja onto the Google Play store. (took a few days for approval) [https://play.google.com/store/apps/details?id=flutter.vdo.ninja](https://play.google.com/store/apps/details?id=flutter.vdo.ninja)
* I may re-release it at some point, but I'll keep this updated until then. Please note -- this is not a feature complete version of VDO.Ninja; its bare bones.

#### February 23

* Updated the android app to android 12, added flashlight support to the android app, and patched some crashing causes. (not published yet; still have another couple things to do before that)

#### February 20

* Android app will save the last stream ID used automatically (not yet uploaded)
* Android app will show the camera preview before a user joins (not yet uploaded.) I'll upload the new android app once I finish up a few other features with it

#### February 2

* The android app was updated; minor stuff updated in the code, such as updated API endpoints, and it's been built with an updated code framework, so hopefully better support and fewer bugs. Functionality wise, the app is the same though -- camera and screen share support, but pretty basic. Same install link as before. [https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view](https://drive.google.com/file/d/1M0kv5nWLtcfl2JOnsAGiG1zUmkeIVLyZ/view)

#### January 14

* Added stats back into the iOS app, so they will appear in the header.
