---
title: "ffmpeg 常用指令筆記"
date: "2025-02-20T15:59:48+08:00"
tags: ["ffmpeg",]
#title_images: ["/photo1.png", "/photo2.png",]
#ending_images: ["/photo3.png", "/photo4.png", "/photo5.png",]
author: "holla"
slug: "ffmpeg-cmds-note"
draft: false
---

## 影片加速
以下指令將影片加速 60 倍 (加入 -an 移除聲音)
<!--more-->
```bash
ffmpeg -i input.mp4 -filter:v "setpts=PTS/60" out.mp4
```
---
## 移除重覆或相似的 frame
```bash
ffmpeg -i input.mp4 -vf mpdecimate,setpts=N/FRAME_RATE/TB out.mp4
```
---
## 1080p to 720p
```bash
ffmpeg -i input.mp4 -vf scale=-1:720 -c:v libx264 -crf 0 -preset veryslow -c:a copy out.mp4
```
- `-vf scale=-1:720` 調整影片解析度
  - `-1` 表示在維持影片的寬高比的情況下，自動計算寬度
  - `720` 是指定高度
- `-crf` 是畫質設定 (越低保留越多細節)
- `-preset` 控制編碼過程的速度和最終壓縮效率
  - ultrafast, superfast, veryfast, faster, fast, medium, slow, veryslow, placebo
- `-c:a copy` 直接複製音軌
---
想到再加。