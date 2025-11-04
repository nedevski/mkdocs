---
draft: true
date: 2023-06-21
authors:
  - nedevski
categories:
  - General
title: Self hosted multi-purpose homelab - Full Guide
---

TLDR goes here.
<!-- more -->

## Intro

Why am I doing this?

## Choosing your hardware

TLDR - unless you want a full NAS, get a used mini-desktop like the Lenovo M900 Tiny with an i5 or i7, ideally 16GB of RAM, and an NVMe SSD (so the SATA slot is free for an additional 2.5 inch drive)

## Choosing your OS/Hypervisor

Use Proxmox for multiple VMs or if you have multiple physical servers. It also helps with management/backups in general, but has a learning curve.

Use Ubuntu bare-metal if all you want to do is host different Docker containers. You can back-up your containers individually, rather than your whole OS.

### Proxmox Install

### Ubuntu Install

### Enable Wake-on-LAN & Auto power-on

WoL = tricky to setup

Restore power after power loss = mandatory

## Ubuntu setup

Connect with SSH - find your IP or use your hostname

```shell
ssh username@192.168.1.69 # SSH by IP
ssh username@machinename  # SSH by Hostname
```

### Install Docker

Basically [RTFM](https://docs.docker.com/engine/install/ubuntu/)

### Set up Git/Github

- Connect GitHub to your local repo
- Add ssh keys
- Add .gitignore for the data directories!
- (optional) Utilize branches if you have separate machines
- (optional) Add root file with the name of the server

### Mount additional HDDs

A nice [tutorial](https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux#step-5-mount-the-new-filesystem)

```shell
# install parted
sudo apt update
sudo apt install parted

# find disk
sudo parted -l | grep Error
sudo lsblk -o NAME,FSTYPE,LABEL,UUID,MOUNTPOINT

# format disk
sudo parted /dev/sdb mklabel gpt
sudo parted -a opt /dev/sdb mkpart primary ext4 0% 100%
sudo mkfs.ext4 -L partition_label /dev/sdb1

# temporary mount
sudo mount -o defaults /dev/sda1 /mnt/data

#persistent mount & get UUID of drive

sudo lsblk -o NAME,FSTYPE,LABEL,UUID,MOUNTPOINT
# update mount file
sudo nano /etc/fstab

# append
UUID=4b313333-a7b5-48c1-a957-d77d637e4fda /mnt/data ext4 defaults 0 2

# if first mounting run:
sudo mount -a
#else
sudo reboot
```

## Core Docker containers

### Samba - Windows file share

TODO: insert link to docs

### VS Code Server

View all of your files in one place, plus easy access to the console from a Web UI. Can be a bit more resource intensive.

### Wireguard VPN

<https://hub.docker.com/r/linuxserver/wireguard>

<https://markontech.com/linux/install-wireguard-vpn-server-with-docker/>

- !!! Need to have access to port forwarding !!!
- Easy to set up
- Easy to add clients
- Desktop/Android/iOS clients available

### DDNS Updater

## Exposing the services to the internet

### Nginx Proxy Manager

- Simple UI to expose local machine & local network web apps
- No domain management
- Basic access controls - IP based restrictions only
- Need to have access to port forwarding
- The only option for exposing a media server

### Cloudflare tunnels

- No need to have access to port forwarding
- Not an option for exposing VPN/Media servers
- Free, but you are cloud dependent
- Powerful web portal with tons of options
- Easy domain/subdomain management
- Advanced access management, incl. a login page with Google/Facebook/Email PIN

### Docker networks for added security

- Put every service in its own network
- Don't expose container ports if possible
- Only the nginx/cloudflared container should have access to a service

### Using Nginx and Cloudflare tunnels at the same time

*/@/www bindings for the domain directly to the IP
Explicit bindings for cloudflare tunnels

## Self-hosted essentials

### NextCloud

Alternatives: OwnCloud / SeaFile / FileRun

Pros:

- Desktop/Mobile apps, file sync
- Self-hosted calendar, chat, contacts

Cons:

- Best to use it with a dedicated NAS
- Can be resource intensive

### VaultWarden

Password management

### Shlink

URL shortening & tracking solution with web UI

### AdGuard

No more ads!

### Wordpress blog

Self-hosted blog
Use php.ini initialization file

### MS SQL

Express version (free)

### Custom containers

If you are a developer - run your own services locally instead of using Azure/AWS

## Media center + TorrentBox

### qBitTorrent

### Plex/Jellyfin

### The *arr stack - Prowlarr/Radarr/Sonarr

Automatically fetch your favorite movies and tv shows

## Management containers

### Portainer

<https://install.portainer.io/be-standalone-linux>

Simple container management
Simple logs viewer
Can integrate with multiple docker instances

### Duplicati

Simple backup utility
Ability to backup files on different places
Customisable backup schedule

### Uptime Kuma

Track the availability of all of your services
Tons of notification options - email, pushbullet, telegram

## Cheatsheets

### Add Samba share

### Github SSH Login

### Initialize your repo

### Mount HDD