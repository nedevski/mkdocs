---
title: Choosing your hardware
---

## Getting started

When you're starting out, it's likely you don't know what your needs are going to be. You might be scared of using Docker, Linux or the console. This is why I always recommend to start experimenting on your current PC. This will give you some insight on the workflow and if you need a dedicated server at all.

Download Docker and learn how to install a containerized application. Find apps that you might find useful and install something simple like Wordpress or Mealie. You will need to learn about how containers work, how to open ports, using networks and volumes. It might be a steep learning curve, so it's best to get familiar with the software before buying a dedicated machine.

## How to approach choosing the hardware

Choosing your hardware will always depend on your needs and budget. The approach if you want a server just for hosting apps or if you need storage is different.

If you only need to host your apps and websites - nothing beats a good Micro PC. It has low idle power consumption (usually ~10w) and the used market is full of them, so you can get one for really cheap.

The most important thing for me is always the idle power consumption. Your machine(s) will be on 24/7 and every watt saved will accumulate over time and a bit of planning here can save you a lot in the long run.

I also have an UPS and lower consumption means my machines will be able to run longer on battery. This is also why I prefer to use two machines - one micro PC with the most important things and one NAS for heavier applications and storage that I can turn off if I lose power and extend my time on battery.

## 📝 Introduction
Picking the right hardware is one of the most important steps in self-hosting. Whether you're building a simple automation hub or a full-featured NAS, your choices will affect performance, power usage, expandability, and long-term reliability. This guide breaks down the key components and helps you choose what fits your needs — without overspending or overcomplicating things.

---

## 🧳 Form Factor: Micro PC vs Tower

### 🧊 Micro PC (Mini PC, NUC, SFF)
- ✅ Small, quiet, and low power.
- ✅ Great for basic services or light workloads.
- ❌ Limited expandability (fewer SATA ports, no PCIe slots).
- ❌ Harder to cool under heavy load.

### 🏗️ Tower (ATX/mATX)
- ✅ More room for drives, RAM, and expansion cards.
- ✅ Easier to cool and upgrade over time.
- ❌ Takes more space and may use more power.

💡 Tip: If you're building a NAS or plan to expand later, a tower gives you more flexibility.

---

## 🖥️ CPU: Brains of the Operation
- **Low Power CPUs** (like Intel i3/i5 non-K or AMD Ryzen 5) are great for 24/7 uptime.
- **More Cores** help if you plan to run multiple services or virtual machines.
- **Avoid Overkill** — you don’t need a gaming CPU for a NAS or automation hub.

💡 Tip: Look for CPUs that support **low C-states** to save power when idle.

---

## 🧠 RAM: Memory Matters
- **8GB** is fine for basic setups.
- **16/32GB** is better if you use containers, VMs, or heavier services.
- **64GB or more** is useful if you're running multiple virtual machines or lots of heavy containers.

---

## 💾 Storage: Speed vs Capacity
- **SSD (NVMe or SATA)** for fast boot and app performance.
- **HDDs** for bulk storage (media, backups, etc.).

💡 If you need a lot of storage — for things like movies, photos, backups, or shared folders — you're probably heading toward a **NAS (Network Attached Storage)** setup. A NAS is designed to hold multiple drives and serve files reliably across your network.

---

## 🧭 Summary
Pick hardware based on your real needs — not hype. Start small, build smart, and leave room to grow. A well-balanced setup will save you headaches, power, and money.
