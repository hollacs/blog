---
title: "ffmpeg 將影片轉成 gif"
date: "2025-02-25T18:10:58+08:00"
tags: ["ffmpeg", "gif",]
author: "holla"
draft: false
---
# 如何用 FFmpeg 將影片轉成 GIF：從低品質到高品質
這個要說的東西有點多，所以我覺得可以獨立出一篇。 \
本文將介紹快速將影片製作成低品質 gif 的方法，再說明如何提升品質。
<!--more-->
---

## 低品質 GIF：簡單快速
如果只是想快速生成 GIF，不在意細節，可以用以下指令：
```bash
ffmpeg -ss 30 -t 3 -i input.mp4 \
    -vf "fps=10,scale=320:-1" \
    -loop 0 output.gif
```

### 指令解析
- `-ss 30`: 跳過影片前 30 秒
- `-t 3`: 擷取 3 秒內容
- `fps=10`: 每秒 10 幀，畫面流暢度普通
- `scale=320:-1`: 寬度縮到 320 像素，高度自動調整
- `-loop 0`: 無限循環（-1 不循環，1 循環一次播放兩次）

### 效果與用途
這種方法省略了複雜的優化，檔案小、生成快，但顏色可能失真（出現色塊或條紋），適合隨手分享或測試用。如果想更低品質，可以試試 fps=5 或 scale=160:-1，進一步壓縮大小。

---

## 高品質 GIF：畫面更精緻

若追求清晰畫質和豐富色彩，可以加入調色盤生成和優化濾鏡，試試這個指令：
```bash
ffmpeg -ss 30 -t 3 -i input.mp4 \
    -vf "fps=10,scale=320:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" \
    -loop 0 output.gif
```

### 指令解析
- `scale=320:-1:flags=lanczos`: 用高品質 lanczos 演算法縮放到 320 像素寬
- `split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse`: 分流處理，先從影片生成調色盤（[palettegen](https://ffmpeg.org/ffmpeg-filters.html#palettegen)），再應用到輸出（[paletteuse](https://ffmpeg.org/ffmpeg-filters.html#paletteuse)），提升色彩準確度

### 進階調整
- `stats_mode`: 控制調色盤生成方式，`full`（預設，整體畫面）、`diff`（僅移動部分）或 `single`（每幀獨立）。例如：`palettegen=stats_mode=single & paletteuse=new=1`
- `dither`: 選擇抖動演算法，`bayer`（確定性）、錯誤擴散（如預設 `sierra2_4a`）或 `none`（無抖動）。用 `bayer` 時可搭配 `bayer_scale` 測試效果。

### 效果與用途
這種方法生成的 GIF 畫質細膩，色彩自然，適合展示需要高視覺效果的場合。當然，檔案會稍大，處理時間也較長。