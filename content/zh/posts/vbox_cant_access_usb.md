---
title: "解決 Arch Linux 下 VirtualBox 「Can't enumerate USB devices」錯誤"
date: "2025-05-07T12:57:00+08:00"
tags: ["vbox", "usb"]
author: "holla"
slug: "vbox_cant_access_usb"
draft: false
---

最近在 Arch Linux 上用 VirtualBox，結果跳出「Can't enumerate USB devices」的錯誤，記錄一下解決的過程，免得下次又忘。
<!--more-->

## 解決步驟

檢查用戶組 VirtualBox 要把用戶加到 vboxusers 組，不然沒權限碰 USB。

```bash
groups
```

沒看到 vboxusers，就加進去：
```bash
sudo usermod -aG vboxusers $USER
```

然後重開機（登出可能不夠，~~arch 有時候就是這麼 hardcore~~）

希望這筆記能幫到下次踩坑的自己（或你）！
