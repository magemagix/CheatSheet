# 🚀 Raspberry Pi 4 + Selenium + Chromedriver: A Journey to the Web Scraping Galaxy 🌌


So, you want to take on the **mighty quest** of installing **Selenium** and **Chromedriver** on your **Raspberry Pi 4**? 🛸 Well, buckle up, because this journey is a bit of a rollercoaster ride! 🎢 Even the wisest AI couldn't guide me properly, so I took matters into my own hands. But don't worry, brave traveler, I've got you covered! Ready to embark on this adventure? Let's goooo! 😎


---


## 🖥️ My Configuration (The Beginning)

First things first! Let's start by making sure your Raspberry Pi 4 is prepped and ready for action. I’m running the **latest recommended Raspberry Pi OS** (64-bit) straight from the **Debian Trixie** branch. 🌟

<br><br>

### 🖱️ System Configuration:

Here’s what I used:

  * Raspberry Pi OS (64-bit)

  * A port of Debian Trixie with the Raspberry Pi Desktop (Recommended)


After flashing the OS image onto my **microSD card**, I popped it into my Pi, hit power, and... boom! Time to update the system to make sure everything is fresh and spiffy. 💻✨

<br><br>



### 🚀 Updating Your System:

```bash
sudo apt update && sudo apt dist-upgrade && sudo apt clean && sudo apt autoremove && sudo reboot
```

Once your Pi restarts, you can check your system info with the following command:

```bash
lsb_release -a
```

And the output should look something like this:

```bash
No LSB modules are available.
Distributor ID:	Debian
Description:	Debian GNU/Linux 13 (trixie)
Release:	13
Codename:	trixie
```

Or you can go a little more fancy and use:

```bash
cat /etc/*-release
```

Which will give you more deets like:

```bash
PRETTY_NAME="Debian GNU/Linux 13 (trixie)"
NAME="Debian GNU/Linux"
VERSION_ID="13"
VERSION="13 (trixie)"
VERSION_CODENAME=trixie
DEBIAN_VERSION_FULL=13.1
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```
<br><br>



### 🐍 Python Version Check:

I’m rocking **Python 3.13**, so let’s check it:

```bash
python -V
```
Output:

```bash
Python 3.13.5
```

---

<br>
