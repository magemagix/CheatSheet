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


## 🧰 Set the Environment (UV Magic ✨)

For managing this project and its packages, I use **uv**—it's like a **magic wand** for your Python environments. 🪄 You can find all the details in its [official repository](https://github.com/astral-sh/uv), if you want to learn more. 🌱

To install **uv**, just follow the instructions in the repository—easy peasy! 🍋 But don’t forget this important step: you need to add `$HOME/.local/bin` to your **PATH** so **uv** can do its magic ✨. To do this, you can either restart your **shell**, or if you’re feeling bold, just run:

```bash
source $HOME/.local/bin/env
```
Now you’re all set to roll with **uv**! 🏎️ Ready to zoom ahead? Let’s do this! 🚀


As we journey through this setup, you’ll see that I’m using **uv** to manage the project environment and dependencies. 🌱 Now, **uv** is just a trusty tool in our toolbox for this adventure, but if you find yourself curious about it (because, trust me, you’ll want to know more!), don’t worry—I’ve got you covered. 📚

Simply check out the **current repository** and open the **uv.md** file for a full guide. 📜 It’s like a *treasure map* 🗺️—detailed, and ready to help you unlock all the hidden secrets of **uv**!

But for now, let’s keep moving forward with the main quest. 🏃‍♀️ Onward!

Before we continue, let's make sure your system is fully updated and prepped with all the necessary dependencies. 🔧💻 Run the following commands to get everything in tip-top shape:

```bash
sudo apt-get update
sudo apt-get install -y libglib2.0-0 libnss3 libdbus-glib-1-2 libgconf-2-4 libfontconfig1 libgbm1 libu2f-udev udev
sudo apt --fix-broken install
sudo reboot
```

Once you’ve rebooted, you’ll be all set to continue with the next steps. 🛠️


---