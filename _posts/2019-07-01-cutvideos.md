---
layout: post
title: How to cut videos with ffmpeg?
published: true
tag: ffmpeg
---

Here is how to extract part of a video.

```bash
# extracts 5 minutes
ffmpeg -i input.mkv -ss 00:20:00 -c copy -to 00:25:00 output.mkv 
# extracts 25 minutes, if the video is long enough
ffmpeg -i input.mkv -ss 00:20:00 -c copy -t 00:25:00 output2.mkv 
```

Probably from [here](https://superuser.com/questions/138331/using-ffmpeg-to-cut-up-video) with tags explained and everything. Seems that the correct name is '[seeking](http://trac.ffmpeg.org/wiki/Seeking)'. 

