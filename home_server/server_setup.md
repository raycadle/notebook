---
title: Server Setup
parent: Home Server
---

# Server Setup

For my operating system I'm running Rocky Linux 10 in a headless config.

I chose to use `podman` to run my apps in containers as it's just simpler to setup due to its availability on RHEL-based distros. I prefer to use scripts to automate the setup of my containers as I'm more familiar with shell scripting, as opposed to the compose spec of whatever else. I may dive into those in the future, but for now I just want my setup working and have it be out of the way.

My various setups for streaming, backups, and miscellaneous uses will be outlined in their own pages as time goes on.

## Future Upgrades

The main upgrade I want to make to the server is to upgrade the CPU to a quad-core variant. Due to being power limited in the micro-chassis, I am forced to use low-power CPUs. So, I chose to go with the 4c/8t i7-7700T. It comes with the UHD 630 iGPU which will be significantly better for transcoding, compared to the HD 530 in the 6100T (not that I do much transcoding right now). It also allows me to run my RAM at 2400 MT/s instead of 2133 MT/s. Currently I have mismatched speeds across both sticks with one being 2400 MT/s and the other being 3200 MT/s, but I couldn't pass up the incredible deal I got for the 3200 MT/s stick so "que sera sera".

Beyond the CPU upgrade, there aren't any other hardware upgrades that I can do to the chassis. The cooling solution is pretty much the same across all micro chassis, and it is already at max supported RAM. I've already repasted the CPU and cleaned the chassis properly. The only upgrade would be to upgrade the storage, but I would rather leave it as is and move my data over to a dedicated NAS. That will allow me to run my drives in a RAID config to protect against drive failure.