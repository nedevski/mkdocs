---
title: Current setup
---

## Networking

Since my apartment is hardwired with CAT6, I decided to go overkill and go full Ubiquiti. This might be an overkill for simpler setups, but as my network grew I saw how limited standard routers are and how complicated something like OpenWRT could get once you dive a bit deeper.

So I settled on this stack.
- [Cloud Gateway Ultra](https://eu.store.ui.com/eu/en/products/ucg-ultra)
- [Switch Lite 16 PoE](https://eu.store.ui.com/eu/en/category/switching-utility/products/usw-lite-16-poe)
- [U6+ Access Points](https://eu.store.ui.com/eu/en/category/all-wifi/products/u6-plus)

This allows me to connect all 12 in-wall cables, 2 servers and 1 Powerline adapter with no spare ports, which is all I need.

With Unifi's powerful software I can easily create VLANs, multiple SSIDs and set-up an in-router Wireguard VPN which turned out to be the single most valuable thing over my upgrades.

## Main server

As my main server I'm using a Dell OptiPlex 3080

- OS: Proxmox VE
- CPU: Intel i5-10600T (6 core, 12 thread)
- RAM: 2x32GB DDR4 RAM
- Storage: Samsung 980 1TB NVMe
- LAN - Gigabit
- Idle draw: 10-12w

## NAS

For my NAS I'm using a custom build PC

- OS: Unraid
- Motherboard: MSI PRO Z690-A
- CPU: Intel i5-12600 (6 core, 12 thread, no e-cores)
- RAM: 2x32GB DDR5 RAM
- Storage: 4x6TB Seagate Ironwolf, 500GB Samsung 860 EVO SSD
- LAN - 2.5G
- Idle draw: 20-24w

## UPS

[Eaton Ellipse PRO UPS](https://www.eaton.com/bg/en-gb/skuPage.ELP1600DIN.html)

- 4 battery powered outlets
- 4 surge-only protected outlets (no battery)
- USB connection

## Apps and services

- Networking overview
- Mini PC overview
  - Home Assistant
  - Ubuntu + Docker
- NAS Overview
  - Immich
  - Media stack - Plex, *arr, qBit
  - Dev stack - Gitea, Gitea Runner, Sonarqube
  - Dawarich (Location Timeline)

## Topics
- Using Hypervisor instead of Bare Metal OS
- Choosing the right hardware
- Using Dockerized apps
- Setting up the file structure
- Tracking configuration with Git
- Core - VS Code Server
- Core - DDNS
- Core - Wireguard VPN
- Exposing apps to the internet
- Core - Nginx vs Cloudflare Tunnels
- Personal blog - Wordpress, Ghost
- Media server - Plex, Torrent, *arr
