# Updates - VDO.Ninja

### 👉 Recent updates for VDO.Ninja can be found at [https://updates.vdo.ninja](https://updates.vdo.ninja/)

#### Audio Enhancements

* **Director Volume Control:** The director's volume slider is now logarithmic, allowing for significantly louder guest audio (up to 800% max loudness).
* **Privacy Muting:** Embedded YouTube videos played via other guests/directors are muted by default when audio is disabled.
* **Speaker Output Mute Hotkey:** ALT + A toggles speaker-output audio mute on/off when the browser tab is in focus.
* **Per-Instance Audio Output Destinations:** Multiple unique audio output destinations can be set per VDO.Ninja instance by right-clicking a video.
* **Noise Gate:** A new noise gate option for local audio controls automatically lowers mic volume when no significant sound is detected.

#### Video and Display

* **Remote Pan-Tilt-Zoom (PTZ) Control:** Full PTZ control is now available remotely for cameras that support it via an IFrame API wrapper.
* **360-Video Support:** Equirectangular 360-video can be viewed via a standalone player page (Chrome/Chromium only, single stream at a time).
* **Transparent Streaming Video:** Supports alpha channels with `&webp` + `&codec=webp` + `&alpha` for transparent streaming video.
* **Viewer-Side Slideshow:** A new viewer-side option decodes incoming video and plays it back as a series of full-window images, with the ability to save single frames as PNGs.
* **Motion Detection:** Triggers feature highlighting, IFrame API events, and OBS scene switching when motion is detected in a video (viewer-side).
* **Window Rotation:** Rotates the entire contents of the VDO.Ninja window.
* **Director Mirror Guest Video:** The director can now globally mirror a guest's video.
* **Fake Guests:** Creates simulated guest videos to help visualize and position layouts.
* **Picture-in-Picture for Self-Preview:** Your self-video preview can pop out into its own draggable Picture-in-Picture window.
* **Floating Picture-in-Picture for Entire Mix:** A new mode allows popping out the entire video mix as a pinned window overlay, or by right-clicking any video and selecting "Picture in picture all".
* **Locked Mixer Output:** Forces the mixer output to maintain a specific aspect-ratio regardless of the browser window size.
* **New Screen Share Layouts:** Screen-share layouts now target an average of 80% screen real-estate for the main screen share and support up to 20 videos.
* **Drawing on Screen:** A full-window transparent canvas overlay allows drawing on the screen, useful for notes or highlights. Toggle with CTRL + ALT + D.
* **Manual Zoom in Effects Menu:** `&effects=7` (or `&effects=zoom`) provides a manual zoom option in the effects menu.
* **Face Tracking/Auto-Centering:** `&effects=1` (or `&effects=facetracking`) auto-centers the user's face in their video, zooming as needed (requires Chromium experimental face detection API).
* **Tap-to-Focus:** When a camera supports focusing, you can tap on the screen to auto-focus on that spot after switching the camera to manual focus.
* **Screenshot to Clipboard/Disk:** Right-click a video and select "Snapshot to Clipboard" to save the current video frame as a PNG, or "Save to Disk".
* **Headless RTMP Streaming:** The Browser-to-RTMP docker project now uses Chromium, improving A/V sync for headless or cloud-hosted streaming to YouTube/Kick/Mp4.

#### API and Integration

* **IFrame API Updates:** New IFrame API commands (`setBufferDelay`, `getGuestList`) enhance external control and data retrieval. Advanced audio/video option changes are now announced over the IFrame API.
* **Server-Side Events (SSE):** The API now supports SSE for push notifications, offering a simpler listen-only alternative to WebSockets.
* **OBS Remote Control Example:** A new IFrame API example allows remote control of OBS without the built-in menu.
* **Cloudflare WHIP/WHEP Support:** Added direct Cloudflare WHIP/WHEP support for publishing multiple senders with unique WHIP/WHEP URLs.
* **Open-Sourced WHIP API Server:** The VDO.Ninja WHIP API server code is now open-source on GitHub.
* **Get Guest List API:** A new remote API query option (`getGuestList`) returns guest slot values, stream IDs, and labels.
* **Group Room Timer API:** Options to start/stop/pause the group room timer are available via remote HTTP/WSS API.
* **Website Function Enhancement:** The `&website` function now allows starting, stopping, and changing website sources, not just a single static site.
* **WSS API Expansion:** The WSS API now includes hang-up events for publishers and viewer-side events for incoming connections/streams, leading to richer StreamDeck integration.
* **Background Image for App:** A new option to set a URL-encoded image as the app's default background, scaling to cover the page.
* **Dynamic Video Scaling:** The IFrame API now supports dynamically changing the scale of a video.
* **Base64 JavaScript Execution:** Users can add raw JavaScript to the URL (Base64 encoded) to run on page load (`&base64js`).
* **Publisher/Viewer Mute Events:** The API sends push event notifications to WebSocket listeners when the local mic/speaker/camera is muted.
* **PowerPoint Remote Control:** Added support for remote PowerPoint slide control (previous/next slide) via AutoHotKey + VDO.Ninja + MIDI. Includes built-in basic controller and IFrame sample app.
* **Group View Mode:** `&groupview` allows viewing groups without needing to join them with your mic/camera. The HTTP/WSS API can now join and leave groups.
* **MIDI Delay:** Allows precise delay of MIDI play-out from VDO.Ninja to your MIDI device, useful for music jamming with latency.
* **Experimental WHIP Support:** Ability to publish directly from OBS to VDO.Ninja via WHIP.
* **Fullscreen Button Alternative:** A new fullscreen button (`&fullscreenbutton`) mimics F11, keeping chat and control bar overlays visible.
* **Offline/Local Deployment Guide:** A guide and script for deploying VDO.Ninja offline without Internet access.
* **Clear Saved Preferences:** A new option (`&clearstorage`) clears all saved user preferences, including director settings and camera/microphone settings. A button is also available in the User menu.
* **Remote URL Change with Consent:** When `&consent` is used on a guest's URL, the director can remotely change the guest's URL without additional permission.
* **Fake Guests:** Creates simulated guest videos based on a specified value, useful for visualizing `&cover`, `&portrait`, etc.
* **Auto Mute Microphone:** `&automute` automatically mutes a guest's microphone when not loaded in an active OBS scene.
* **Multiple Audio Devices:** The `&audiodevice` parameter now accepts multiple audio devices.
* **Dedicated Control Bar Space:** `&controlbarspace` forces the bottom control bar into its own dedicated space.
* **Local Audio Volume Control:** `&volumecontrol` shows a dedicated local audio-volume control bar for canvas or image elements.
* **Visually Impaired Meta Data:** More meta data added to help with assisted readers.
* **Label Suggestion:** `&labelsuggestion` asks the user for a name but provides a default if left blank or canceled.
* **Group Mode Behavior:** `&groupmode` changes how groups work when not in a group; users outside a group do not hear or see anything from others also in group mode.
* **Custom Layouts via URL:** `&layouts` accepts a URL-encoded array of layouts for remote activation via API.
* **Director's Microphone/Output Refresh:** A refresh option for the director's microphone/output change button can re-establish the audio pipeline without user permission.
* **HTTP/WSS API State Values:** The API can now return STATE values as replies to GET/POST/WSS requests.
* **Custom Groups in Director's View:** Custom groups used by remote guests now display in the director's view.
* **Welcome Image:** `&welcomeimage` specifies a URL for a welcome image that appears and fades after a guest joins.
* **Screen Share Layout Prioritization:** Screen-share layouts now prioritize screen real-estate for the main screen share.
* **Mono Mic Input for Guests:** A checkbox for guests to set their mic input to MONO mode, especially useful with `&stereo` or `&proaudio`.
* **Wait Image Fitting:** `&waitimage` now fits or covers the screen, and works with scene links.
* **P2P Connection Type in Stats:** Publisher's connection type is now available to the viewer's side stats.
* **Face Bounding Boxes via API:** `&getfaces` (or `{getFaces:true}` via IFrame API) requests a continuous stream of face bounding boxes for inbound videos.
* **Mobile Touch for Tap-to-Focus:** Added mobile touch support for tap-to-focus feature.
* **Scrollable Audio/Video Settings:** Audio/video director control settings are now scrollable for better visibility.
* **P2P Connections in Stats:** `&showconnections` displays the total number of p2p connections of a remote stream in the director's room and automixer.
* **Chat/DirectorChat API:** `showChat` and `showDirectorChat` HTTP/WSS API options for sending messages to guests.
* **Noise Gate Remote Control & Settings:** The noise gate can now be controlled remotely, and its variables can be tweaked.
* **Compressor Remote Control:** Option to remotely control the compressor with three states (Off/On/Limiter).
* **Preview/Director Layout Toggle:** A button in the director's room toggles between a Preview layout and the normal Director layout.
* **Content Hint Parameters:** New sender-side parameters (`&contenthint`, `&screensharecontenthint`, `&audiocontenthint`) to balance resolution vs. frame rate and optimize audio based on content type.
* **Custom Scenes Sorted:** Custom scenes are now sorted based on alphanumerical value.
* **Display Name Multi-Line:** Display names can be on multiple lines using .
* **Custom Grid Overlay:** The `&grid` effect can be customized by passing an image link.
* **User-Friendly Proxy:** `proxy.vdo.ninja/alpha/` offers a more user-friendly alternative to `&proxy`.
* **Active Speaker Modes:** `&activespeaker=3` and `4` will not switch to show audio-only sources.
* **Chunked Mode Camera/Audio Switching:** Chunked mode now allows switching cameras/audio without breaking.
* **Screen Share Tab Opening:** Right-clicking the screen-share icon offers an option to open the screen share in a new pre-configured tab.
* **Screen Share Aspect Ratio:** `&aspectratio` now works with screen shares, or `&screenshareaspectratio` for screen shares specifically.
* **Director Solo-Talk Volume Drop:** When the director talks in solo-talk mode, other guests' volume drops to 25%.
* **Hide Co-Directors:** `&hidecodirectors` hides co-directors from appearing in the director's room.
* **Clickable URLs in Chat:** Chat messages containing URLs will now have those URLs be clickable.
* **Director Screen Share as Second Stream:** Director's screen share now counts as a second video stream, allowing both camera and screen share by default.
* **Firefox Video Encoding Pause:** Firefox now supports fully pausing video stream encoding to a guest (v110+).
* **Director Video Stream Pause:** Director can now fully stop preview for Firefox v110+ guest streams.
* **Firefox Full-Window Preview:** Full-windowing own preview on Firefox v110+ no longer pauses video for other guests.
* **Guest Slot Preference:** `&slot` allows guests to specify a preferred slot for auto-assignment.
* **Queue Transfer:** `&queuetransfer` transfers a guest to another room in queue mode.
* **Activate Guest Button:** A director can now activate a guest in queue mode with a dedicated button.
* **Broadcast Transfer:** `&broadcasttransfer` sets the default for transferring guests in broadcast mode.
* **Multiple Unique Audio Output Destinations:** Allows routing different audio streams to different output devices.
* **Sensor Data Enhancements:** `&sensor` now includes speed and altitude data, and `&sensorfilter` allows explicit listing of sensor data to capture.
* **QR Code for Links:** Right-clicking a link offers the option to show it as a QR Code.
