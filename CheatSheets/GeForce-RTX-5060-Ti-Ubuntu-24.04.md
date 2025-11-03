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



### ⚡ Trick 2 — Installing the Right NVIDIA Driver, CUDA, and cuDNN

Here’s where things get serious.

Installing NVIDIA drivers for the RTX 5060 Ti **isn’t** the same as for older cards.

The **traditional** (and seemingly forward) way to install NVIDIA drivers is to use Ubuntu’s repositories — simple, clean, and normally rock-solid.

You’d first list all available NVIDIA drivers with:

```bash 
apt-cache search nvidia | grep -P '^nvidia-(driver-)?[0-9]+\s'
```
Then pick one version, say **550**, and install it like this:

```bash
sudo apt -y install nvidia-utils-550
sudo apt -y install nvidia-driver-550
sudo apt -y install nvidia-settings
```
Looks perfect, right?

Yeah… not this time. 😬

Unfortunately, this approach doesn’t work for the RTX 5060 Ti — the drivers in Ubuntu’s repos aren’t up to date (yet), so your shiny new GPU will just sit there, unrecognized and sad.

Using Ubuntu’s default repositories? ❌ Nope.
We’ll do it **manually** — like real Linux warriors.

Before diving in, remember: your NVIDIA driver should match the CUDA version — think of them as peanut butter and jelly 🥪, they just work better together!

---

### 🧱 Step 1 — Download the Correct NVIDIA Driver

Head to the official [NVIDIA Driver Download page](https://www.nvidia.com/en-us/drivers/). 🚀

Use these parameters for manual driver search:
| Setting          | Value                      |
| ---------------- | -------------------------- |
| Product Category | GeForce                    |
| Product Series   | GeForce RTX 50 Series      |
| Product          | NVIDIA GeForce RTX 5060 Ti |
| OS               | Linux 64-bit               |


At the time of writing, the latest driver was **580.95.05**.

Download it, then install it:

```bash
sudo sh NVIDIA-Linux-x86_64-580.95.05.run  --kernel-module-type=open
```

This `--kernel-module-type=open` flag is **the secret sauce** 🌟 — without it, nothing works properly.

During installation:
 * Accept every warning.
 * Choose **Continue installation**.
 * Enable **32-bit compatibility** when asked.
 * Allow **nvidia-xconfig** to update your **X configuration**.

When complete, reboot your system:

```bash
sudo reboot
```

---

### 🛠️ Step 2 — Verify Driver Installation
Once you’re back, open a terminal and type:

```bash
nvidia-smi
```


You should see something like:

```pgsql
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 580.95.05   Driver Version: 580.95.05   
| NVIDIA GeForce RTX 5060 Ti                                       |
+-----------------------------------------------------------------------------+
```

🎉 Both monitors should now be working.

---



### ⚙️ Step 3 — Install CUDA Toolkit 13.0

Go to the [CUDA Downloads](https://developer.nvidia.com/cuda-downloads).

Choose:

| Option         | Value           |
| -------------- | --------------- |
| OS             | Linux           |
| Architecture   | x86_64          |
| Distribution   | Ubuntu          |
| Version        | 24.04           |
| Installer Type | runfile (local) |

Then download and install:

```bash 
wget https://developer.download.nvidia.com/compute/cuda/13.0.2/local_installers/cuda_13.0.2_580.95.05_linux.run
chmod +x cuda_13.0.2_580.95.05_linux.run
sudo sh cuda_13.0.2_580.95.05_linux.run
```

When prompted the license, type `accept`, then **deselect “Driver”** since we already installed it.
(Use the **Spacebar** to toggle options.)

---

### 🧭 Step 4 — Configure CUDA Environment Variables

After installation, you’ll get a summary like this:

```ruby
Toolkit: Installed in /usr/local/cuda-13.0/
Please ensure PATH and LD_LIBRARY_PATH include the following:
  PATH=/usr/local/cuda-13.0/bin
  LD_LIBRARY_PATH=/usr/local/cuda-13.0/lib64
```

Let’s make it permanent:

```bash
echo 'export PATH=$PATH:/usr/local/cuda-13.0/bin' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-13.0/lib64' >> ~/.bashrc
source ~/.bashrc
```

Just to be sure:

```bash
echo "/usr/local/cuda-13.0/lib64" | sudo tee -a /etc/ld.so.conf
sudo ldconfig
```

---


