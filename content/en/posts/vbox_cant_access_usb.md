---
title: "Fixing VirtualBox 'Can't enumerate USB devices' Error on Arch Linux"
date: "2025-05-07T13:22:00+08:00"
tags: ["vbox", "usb"]
author: "holla"
slug: "vbox_cant_access_usb-en"
draft: false
---

Recently ran into the "Can't enumerate USB devices" error while using VirtualBox on Arch Linux. Jotting down the fix here so I don’t forget next time.
<!--more-->

## Steps to Fix

Check User Group:
VirtualBox requires the user to be in the `vboxusers` group to access USB devices.
```bash
groups
```

If you don’t see `vboxusers`, add yourself:
```bash
sudo usermod -aG vboxusers $USER
```

Then reboot (logging out might not be enough, ~~Arch can be that hardcore sometimes~~).

Hope this note helps the next time I (or you) hit this snag!
