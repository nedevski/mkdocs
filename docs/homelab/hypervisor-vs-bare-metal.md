---
title: Hypervisor vs Bare metal
---

## 🧠 What Is a Hypervisor (and Why Use One)?

## Simple Explanation
When you self-host, you can either install your services directly on your computer (**bare metal**) or use something called a **hypervisor**. A hypervisor lets you run multiple mini-computers (called **virtual machines**) on one physical machine.

Think of it like having several separate rooms inside one house - each room can have its own setup, and if something breaks in one room, the others stay safe.

---

## 🛠️ Why Use a Hypervisor?

- **Keeps Things Separate**  
  You can run different operating systems (Windows, Ubuntu, HomeAssistant) in their own spaces. If one crashes, the others keep working.

- **Easy Backups**  
  You can take a "snapshot" of a virtual machine and roll back if something goes wrong.

- **Flexible Setup**  
  You can test new things without messing up your main system.

- **Better Organization**  
  It’s easier to manage updates, security, and troubleshooting when services are split.

---

## 🧪 When Bare Metal Might Be Better

- You only want to run one thing (like just a NAS).
- Your hardware is very limited (not much RAM or CPU).
- You want the simplest setup possible.

---

## 🧰 Good Hypervisors to Try

- **Proxmox VE** - Free, beginner-friendly, and great for home labs.
- **VirtualBox** - Easy to use for testing on your desktop.
- **Hyper-V** - Built into Windows Pro and Enterprise editions; good for Windows users who want to try virtualization without installing extra software.

---

## 🧭 Summary

If you're just starting out and want flexibility, safety, and room to grow - a hypervisor is a great choice. It adds a bit of complexity at first, but makes your setup much easier to manage in the long run.