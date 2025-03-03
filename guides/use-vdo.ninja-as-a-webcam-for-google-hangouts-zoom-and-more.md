# How to use VDO.Ninja as a webcam for Google Hangouts, Zoom, and more

In this walk-through we demonstrate how to use VDO.Ninja and the OBS Virtual Camera to bring remote cameras, smartphones, and other media sources into third-party video software as a virtual webcam.

We will also be including audio in this guide, however that may not be needed in all situations. You can skip the audio-related portions if not needed for your application.

{% hint style="info" %}
Some third-party applications support Browser Sources as an input, negating the need for a virtual camera, as VDO.Ninja can be used directly in such scenarios.
{% endhint %}

\
**Requirements for this guide**

* OBS Studio V26 or newer
* Virtual Audio Cable Software               &#x20;
  * For Windows, use VB-CABLE Virtual Audio
    * This is recommended software as it enables proper audio support
    * The software is Donationware
    * [https://www.vb-audio.com/Cable/](https://www.google.com/url?q=https://www.vb-audio.com/Cable/\&sa=D\&source=editors\&ust=1651965669921223\&usg=AOvVaw32Nu8pxk1d3BG6A39I2slb)\

  * For macOS, you have a few choices:
    * &#x20;[https://github.com/steveseguin/vdo.ninja/wiki/FAQ#how-to-capture-audio-on-mac](https://github.com/steveseguin/vdo.ninja/wiki/FAQ#how-to-capture-audio-on-mac)

**Basic Workflow Diagram**

Please find below a diagram explaining the basic premise of what we are intending to do in this guide. We will go through it all, one step at a time.

![](<../.gitbook/assets/image (100) (1).png>)

### **Step 0. - Installing dependencies**

This guide assumes you have OBS installed, along with the other required software, though we shall briefly cover these initial installation steps now.

We also will assume you are using Windows. You will need to adapt accordingly for macOS, which likely is going to be more complicated.&#x20;

On the computer that will be using Zoom or Google Hangouts to broadcast, please do the following:

1. Install OBS Studio  h[ttps://github.com/obsproject/obs-studio/releases/](https://www.google.com/url?q=https://github.com/obsproject/obs-studio/releases/\&sa=D\&source=editors\&ust=1651965669925129\&usg=AOvVaw2y3_HZy3Sm_0aAQ7QRRX8K)
2. Install the VB-Cable Virtual Audio device.\
   [https://www.vb-audio.com/Cable/](https://www.google.com/url?q=https://www.vb-audio.com/Cable/\&sa=D\&source=editors\&ust=1651965669925809\&usg=AOvVaw3k4NHvzmWNnuxOnB2nnoYZ)

### **Step 1.** &#x20;

Generate an VDO.Ninja invite. You will get an Invite link and a Browser Source link.

The <mark style="color:red;">Guest Invite Link</mark> is what you send to a person who you wish to join your live stream in OBS.  We will also be calling this a PUSH link, as it contains \&push in the URL.&#x20;

The <mark style="color:green;">OBS Browser Source link</mark> is what we will be putting into OBS to capture our guest’s video stream with.  We will also be calling this a VIEW link, as it contains \&view in the URL.

<figure><img src="../.gitbook/assets/image (25) (2).png" alt=""><figcaption></figcaption></figure>

![A QR-code is provided to make connecting your phone as a camera source easy](<../.gitbook/assets/image (121) (1) (1).png>)

### Step 2.

For ease of setup, the "Generate Invite Link" button found at [VDO.Ninja](https://vdo.ninja) can provide you with both a <mark style="color:red;">PUSH (</mark><mark style="color:red;">**Guest Invite**</mark><mark style="color:red;">) link</mark> and an <mark style="color:green;">VIEW (</mark><mark style="color:green;">**OBS Source**</mark><mark style="color:green;">) link.</mark> &#x20;

We will want to send the PUSH link to our guest, or if using a mobile phone, use the QR code to open the link. We can select our camera, microphone, and then click START.

![](<../.gitbook/assets/image (101) (1) (1).png>)

### Step 3.

Once we have our PUSH link setup to stream our camera, we can move on to pulling that video stream into OBS using the VIEW link.

To setup our OBS Studio, create a Scene and then add a Browser Source in OBS Studio. Give it a name and we will fill out the details in the next step.

![We want to load our VIEW link in OBS as a Browser source](https://lh3.googleusercontent.com/piBkBuRIVMOmOQ35CisMz-cq0WUxdqKMxQhptnKFwUGAUT75eDZkoRXE52f1KFOpBFQ5l6XkjzFQZXTzwGXJ152n0bDa7iVnDd_B8EIewpjiEEEsxJnADnaToOi391fPZQ9SUNxSaCLsvaA1DA)

### Step 4.

In the properties for the Browser Source, we need to fill out a few fields and then hit OK.

* The URL we add to OBS needs to be set to the VIEW address we created earlier,  \
  Just as example: `https://vdo.ninja/?view=q3QCScW`\
  You will of course need to use your own link, with its own unique view ID, which was given to you at the end of Step #1.  The view ID should exactly make the push ID; case-sensitive.
* Width can be set to 1280
* The height be set to 720
* "<mark style="color:green;">**Control audio via OBS**</mark>" should be checked. This is quite important, else the audio will not work correctly or you will get a terrible echo / feedback.

![When you hit OK, you should see your remote camera source appear in OBS](<../.gitbook/assets/image (108) (1).png>)

{% hint style="info" %}
_SECRET TIP_: Some links in VDO.Ninja can be dragged and dropped directly into OBS from the Chrome browser, avoiding the tedious parts of step 2 and 3. You will still need to select “Control audio via OBS” however, if you wish audio to function.
{% endhint %}

### Step 5.

The video should appear and auto-play. There should be no audio feedback if you selected the Control audio via OBS option.

Now we just need to stretch the video to fill the full scene. It should snap into place when full.

<figure><img src="https://lh6.googleusercontent.com/e5RL8KoBiICqkUWzhawTwXfZrnaiG_NYbmOyIyjRD24Z07ePD2zv-iLB3t_8xb6HMv5FVh99W7WhREFyEQavUPzsZ0Ybrf6iIzs5Vkj59tSYrsRawf0EW1_kexAk0B3zoKzBUoc-auK6TIvfmw" alt=""><figcaption></figcaption></figure>

### Step 6.

Start the OBS Virtual camera ; located under the Start Recording button

<div align="left"><figure><img src="https://lh3.googleusercontent.com/zOShyv0F0uvhQ3PlI7mjCe8C6vZsGRUpq2mhFEuZzl8wGUvFkz1od6wYtSHsoPR8aXlG-oRHI9MTlFiOoouvJUtl0Bs96SrOwnug9MpuyYUE9sYJTAsJPAByYwG4we-cMenOQ79DBf_PO233sg" alt=""><figcaption></figcaption></figure></div>

### Step 7. (optional)

We will now configure OBS to output audio from the Browser Source to the Virtual Audio Cable.  In the OBS settings, under Advanced, we select the Monitoring Device to be our Virtual Audio device. (CABLE Input). &#x20;

We also want to disable Windows audio ducking.

![](https://lh6.googleusercontent.com/JVL8m6M4M3r3VUBKbas9-7plk2hiozPz9q4ZkooARU639q2j9JHZjzqJrFv8V9znfe9uybgDJCdcdJ1hN-N0HzDTZxS2bQH3K2hpIqq5DmmFRDpdW180ILVL2C11OFzbQX11xRWEH-U150YPuQ)

### Step 8. (optional)

In our last configuration step, we want to go into the Advanced Audio Properties in OBS. When there, we want to set the audio sources we want to output have its Audio Monitoring setting be set to Monitor and Output.

If you intend to feed audio from OBS back into an VDO.Ninja group call, you can use this step to also mix-minus the audio; selecting just the audio sources you want the remote guests to hear, excluding their own audio to prevent echo.

<div align="left"><figure><img src="https://lh5.googleusercontent.com/qQGwkh0oeKLgaBcz24L79Zv7UiDZ2igWYYEkkVgiQZXjQ_Q95qBuFMl5-e2XMc-uZLzvQECYpBGNXS_n3_qlyS9IDHBCV3aCDkllplh519Q4pI4rs738Vcgryc4t2axygQYGzqO-BAEeFcCdWg" alt=""><figcaption></figcaption></figure></div>

<figure><img src="https://lh3.googleusercontent.com/Y0KGvcDsbj-X4KP0S8HQNGo3IbPvRSr7XYlqK4Yoj916XFLZXWeAcYNKJUFQzA2APuSaWfiBPhyjzjcXX1JnLr2LIR3CztDYeatNEoPtYj4minUkIXf1HhVDjYZW1jLZFmwt8146pU-gAu0yGQ" alt=""><figcaption></figcaption></figure>

### Step 9.

We’re READY to go!  Using this setup in VDO.Ninja or Zoom or Google Hangouts is just like selecting a second Webcam and microphone.

If you are already in the Zoom / Google Hangout call, you can switch between your webcam and the virtual camera and normal camera in the settings.

It is important to remember that you need to select the VB-Audio Virtual Cable in the call as well, if you also want to share the audio from it that is.

If publishing to VDO.Ninja, remember that you can select multiple audio sources in VDO.Ninja by holding down CTRL (or command) when selecting them. You could include the VB Audio Cable and your local microphone together, for example.

<div align="left"><figure><img src="https://lh6.googleusercontent.com/u8qy24hWB8gqCObTfmZXoNQJebutm08SzyjuYRaN55oaIzK3mb0igE22QZymMVqdQiZbMDHUyzk45_V0enlCzLiOnWEJCMvVEz8NfHB6eshVmB3AKBGecgJZQiBnjayAGEnx5Tr6EA5TpvNkLA" alt=""><figcaption></figcaption></figure></div>

<div align="left"><figure><img src="https://lh5.googleusercontent.com/uVrtV18j6fyGt6DS9-iKmvp5-k8ps-6hICvB1wdJEZyIoM-I6CVtRnT5VGS72Q1pTygzH7iWbBzuAXyTIC18PbkH_Hb9jf0DROj0tnrGbbVz-JE8vUcu4B5RJv6ZpgutwhvP4Be5N6b8XWnVMQ" alt=""><figcaption></figcaption></figure></div>

### All done!

And that should be it! You can switch between the webcam and the OBS live video as needed.

If you need to increase the video quality from the defaults, all that is possible in the next section, linked below:

{% content-ref url="how-do-i-control-bitrate-quality.md" %}
[how-do-i-control-bitrate-quality.md](how-do-i-control-bitrate-quality.md)
{% endcontent-ref %}
