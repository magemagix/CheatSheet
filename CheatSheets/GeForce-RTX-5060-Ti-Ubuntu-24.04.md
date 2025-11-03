# 🎮 To Be or Not to Be (GeForce RTX 5060 Ti 16G)

> “A tale of triumph, tears, and terminal commands.” 🖥️⚔️ 

---


### 🧠 Introduction

Greetings, brave GPU traveler! 👋

This document is my honest, slightly chaotic, and hopefully helpful guide to installing and configuring an **NVIDIA GeForce RTX 5060 Ti 16GB** on **Ubuntu 24.04 LTS**.

I wrote this because — well — I suffered. A lot. 😅
And if my struggle can save even one soul from reinstalling Ubuntu several times in a row, my job here is done.

While this is written for **Ubuntu 24.04**, much of it applies to **other Linux distributions** as well — because the real enemy is not Ubuntu itself, but **drivers**, **kernels**, and maybe the mysterious thing called **Wayland**.

---

### 🧩 My Hardware Setup

For reference (and empathy), here’s my setup:

| Component | Specification |
|------------|---------------|
| **Motherboard** | Micro-Star International Co., Ltd. — MAG B660M MORTAR WIFI DDR4 (MS-7D42) — Version 1.0 |
| **CPU** | Intel® Core™ i5-12400F (12th Gen) |
| **Target GPU** | NVIDIA GeForce RTX 5060 Ti (16GB) |
| **Monitors** | Dual monitors (HDMI + DisplayPort) |
| **Target OS** | Ubuntu 24.04 LTS |
| **Previous GPU** | GTX 1080 8GB (a legend, gone but not forgotten 🪦) |

---


### ⚙️ The Mission

**Goal**:
With my i5-12400F, MAG B660M motherboard, and RTX 5060 Ti, I wanted to:

 * ✅ Install Ubuntu 24.04 cleanly.

 * ✅ Have both monitors working.

 * ✅ Install NVIDIA driver, CUDA, and cuDNN properly.

 * ✅ Verify PyTorch sees the GPU (torch.cuda.is_available() returns True).

Sounds simple? Spoiler: it’s not. But we’ll get there. 💪

---


### 😬 Challenges (a.k.a. “Boss Fights”)

Here’s the series of unfortunate events that occurred:

 1. **Ubuntu 24.04** wouldn’t install when the RTX 5060 Ti was connected — it froze mid-installation. I tried fiddling with the BIOS/UEFI settings like a mad scientist 🧪, but alas… no magic happened. 😅

 2. If I somehow managed to install Ubuntu, **only one monitor** worked (the other was out cold).

 3. `nvidia-smi` **returned nothing** on GPU — the GPU was invisible to the system.

 4. Even after victory, an **Ubuntu update** could suddenly break everything again (one monitor gone, drivers corrupted, and sadness restored).

None of this happened with my old GTX 1080. 🙏 God bless the 1080, may its frames be ever high. RTX 5060 Ti apparently wanted more *attention*. 🙃

---




### 🪄 Trick 1 — Installing Ubuntu 24.04 (The Sneaky Path)

After many failed attempts, I realized that the RTX 5060 Ti doesn’t like installing Ubuntu 24.04 **directly**. The trick?
Take a **detour** via **Ubuntu 22.04**.

#### 🧩 Step-by-Step:

 1. Install Ubuntu **22.04 LTS** as usual — it should detect your hardware just fine (though your GPU might still be shy 😅). One monitor will work perfectly and show your desktop..

 2. Run all updates:
   ```bash 
   sudo apt update && sudo apt upgrade -y && sudo apt dist-upgrade -y
   ```
 3. Once the system is stable, **upgrade** to **Ubuntu 24.04**:

 ```bash
 sudo do-release-upgrade
 ```

 4. Before rebooting, disable **Wayland** because… Wayland is sometimes the “final boss” of NVIDIA issues.

 ```bash
 sudo nano /etc/gdm3/custom.conf
 ```
 Change:

 ```ini
WaylandEnable=false
 ```
Reboot and enjoy your fresh Ubuntu 24.04 installation.

🎉 **Challenge #1 defeated!**

---

