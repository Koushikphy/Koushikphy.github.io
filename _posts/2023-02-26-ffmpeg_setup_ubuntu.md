---
title: "Setting up ffmpeg recording on ubuntu terminal"
tags: 
    - ffmpeg
    - linux
    - webcam
    - recording
category:
    - Linux
date: 2023-02-26
toc: false
layout: single
classes: wide
excerpt: Linking libraries during building executable
---

Setting up ffmpeg in ubuntu to record audio and video is a bit complicated. In windows we can easily get the sources with 
```bash
ffmpeg -list_devices true -f dshow -i dummy
``` 
But this won't work for linux system as it does not support `dshow` and  have to get the video and audio sources separately. First use 
```bash
ffmpeg -sources
```
and it will list the video sources. Look for it closely to get the proper sources. For my case I found these (among a long list of unavailable options) are available for me,
```bash
Auto-detected sources for video4linux2,v4l2:
/dev/video1 [GENERAL WEBCAM: GENERAL WEBCAM]
/dev/video0 [GENERAL WEBCAM: GENERAL WEBCAM]
```
Now look for available codec/format in that source with available resolution with 
```bash
ffmpeg -f v4l2 -list_formats all -i /dev/video0
```
which shows 
```bash
[video4linux2,v4l2 @ 0x558c5c7d06c0] Compressed:       mjpeg :          Motion-JPEG : 1920x1080 1280x720 800x480 640x480 640x360 320x240 176x144 800x600 1920x1080
[video4linux2,v4l2 @ 0x558c5c7d06c0] Raw       :     yuyv422 :           YUYV 4:2:2 : 640x480 640x360 320x240 176x144 640x480
```
So wrapping it altogether, to record video I should be using 
```bash
ffmpeg -f video4linux2 -vcodec mjpeg -video_size 1920x1080 -i /dev/video0
```
Now this won’t record any audio as the input `/dev/video0` does not have any audio stream, now to get the audio source, use 
```bash
arecord --list-devices
```
For my system it shows, 
```bash
*** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC897 Analog [ALC897 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: ALC897 Alt Analog [ALC897 Alt Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: WEBCAM [GENERAL WEBCAM], device 0: USB Audio [USB Audio]
Subdevices: 1/1
Subdevice #0: subdevice #0
```
So my audio source is card number 1, in ffmpeg term its `hw:1` and the format is `alsa` so the ffmpeg audio options, `ffmpeg -f alsa -i hw:1`. But it shows the error 
```bash
[alsa @ 0x564e28c23700] cannot set channel count to 2 (Invalid argument)
```
This is because the input hardware in this case does not support 2 channels, but ffmpeg by default try to record from 2 channel. To prevent that explicitly use 1 channel
`ffmpeg -f alsa -ac 1 -i hw:1`
So wrap it all in, to record video in this case (ignoring other flags like frame rate etc.),
```bash
ffmpeg -f video4linux2 -vcodec mjpeg -video_size 1280x720 -i /dev/video0 -f alsa-ac 1 -i hw:1 video.mp4
```
Remember the order of the arguments in this case matter