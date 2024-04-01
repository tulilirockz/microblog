+++
author = "Tulip"
title = "A pure development environment with NixOS"
date = "2024-05-24T00:34:27-03:00"
description = "My personal development NixOS environment that prioritizes purity"
tags = [
    "NixOS",
    "Linux",
    "Personal"
]
+++

So! Ive been messing around with NixOS for a while now and I feel like I got a pretty decent little environment for my development purposes right now after refactoring my configuration many times.


## Definitions

But like, what _purity_ even means in this context? For me, purity would mean pretty much just a priority hierarchy between correctness, needs, and my personal philosophy when managing my systems

My current priorities with my systems are:

- Using as much FOSS software as possible (avoiding something like VSCode would be best)
- Leveraging the systemd ecossystem as much as possible (since my system will have systemd, why shouldn't I use it as much as I possibly can?)
- Having the least attack surface possible (wiping as much of the system on reboot and containerizing/sandboxing things as much as possible too)
- Have reasonable performance (using TMPFS as root for quick caching for desktop programs, using a tiling window manager, TUI apps and whatever else)
- Have as much control and possibilities as I can (actually have software I want to have, without needing to use esoteric bad programs for stuff that I want, like, lynx over chromium or something dumb like that)
- Be easily redeployable once anything happens (make rootfs tarballs easily for flashing)

## What the system even looks like

My entire system is defined in my [rose.nix](https://github.com/tulilirockz/rose.nix) (pronouced as "rosê"), all my packages are just nix packages, no flatpaks, no snaps, nothing, really.

- Nushell as my shell (without bash or any other shell installed at all) for oxidizing and modernizing my userspace shell experience.
- Wezterm for the terminal (rust + its super new + super fast)
- TMPFS on root for ephemeral environment
- `/etc` as overlayFS instead of writing on every boot (less SSD usage + its a really elegant solution for the TMPFS problem)
- Systemd-Nspawn container for development environment (although I bind most of my system onto it, like my user's `$env.HOME` and whatever else)
- Rootless Docker for environments where I strictly need a valid FHS (with distrobox) (thinking about moving to containerd + nerdctl + youki)
- Virtual machines with Libvirt for developing when I cant use anything else
- Single stateful partition (`/nix`, which contains `/nix/persist` and `/nix/store` for literally the entire system state n storage)

## Obligatory fastfetch at the end

```
/home/tulili: fastfetch
          ▗▄▄▄       ▗▄▄▄▄    ▄▄▄▖             tulili@studio
          ▜███▙       ▜███▙  ▟███▛             -------------
           ▜███▙       ▜███▙▟███▛              OS: NixOS 24.05.20240521.57108524
            ▜███▙       ▜██████▛               Kernel: Linux 6.9.1
     ▟█████████████████▙ ▜████▛     ▟▙         Uptime: 14 mins                                                                                                                               )
    ▟███████████████████▙ ▜███▙    ▟██▙        Shell: nushell 0.93.0
           ▄▄▄▄▖           ▜███▙  ▟███▛        Display (LG FULL HD): 1920x1080 @ 75Hz [External]
          ▟███▛             ▜██▛ ▟███▛         WM: niri (Wayland)
         ▟███▛               ▜▛ ▟███▛          Theme: adw-gtk3-dark [GTK2/3/4]
▟███████████▛                  ▟██████████▙    Icons: Adwaita [GTK2/3/4]
▜██████████▛                  ▟███████████▛    Cursor: Fuchsia (16px)
      ▟███▛ ▟▙               ▟███▛             Terminal: WezTerm 20240203-110809-5046fc22
     ▟███▛ ▟██▙             ▟███▛              Terminal Font: JetBrains Mono
    ▟███▛  ▜███▙           ▝▀▀▀▀               CPU: AMD Ryzen 3 2200G with Radeon Vega Graphics (4) @ 3.50 GHz
    ▜██▛    ▜███▙ ▜██████████████████▛         GPU: AMD Radeon Vega 8 Graphics @ 0.40 GHz [Integrated]
     ▜▛     ▟████▙ ▜████████████████▛          Memory: 2.46 GiB / 5.70 GiB (43%)
           ▟██████▙       ▜███▙                Swap: 0 B / 4.28 GiB (0%)
          ▟███▛▜███▙       ▜███▙               Disk (/): 88.89 MiB / 2.00 GiB (4%) - tmpfs
         ▟███▛  ▜███▙       ▜███▙              Disk (/nix): 134.47 GiB / 446.13 GiB (30%) - btrfs
         ▝▀▀▀    ▀▀▀▀▘       ▀▀▀▘              Local IP (wlan0): 192.168.1.229/24 *
                                               Locale: en_US.UTF-8
```

> NixOS rocks!
