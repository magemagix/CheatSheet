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


## 🍗 The Secret Sauce: Installing ChromeDriver

Alright, now let’s get to the meat of this recipe: **ChromeDriver**. The steps are simple, but not without their little quirks. 🐉

🔥 Install ChromeDriver:

```bash
sudo apt install chromium-driver -y
```

Now, if you try to install **Chromium**:


```bash
sudo apt install chromium -y
```

You’ll get something like this:

```bash
chromium is already the newest version (1:141.0.7390.122-1~deb13u1+rpt1).
chromium set to manually installed.
Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
```

Looks like you're all set with the latest version! ✨


---



## 🌱 Create Your Project (With UV, of course)

Let’s start a new project, shall we? We’ll call it `test`. 🌟

```bash
uv python pin 3.13  # We’ll use Python 3.13 for this project
uv init test
cd test
```



Now, check out the contents of your **pyproject.toml** file:

```bash
nano pyproject.toml
```

You should see something like this:

```toml
[project]
name = "test"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.13"
dependencies = []
```

Now let’s add all the necessary dependencies. It’ll look like this after your edits:


```toml
[project]
name = "test"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.13"
dependencies = [
    "attrs==25.4.0",
    "certifi==2025.10.5",
    "cffi==2.0.0 ; implementation_name != 'pypy' and os_name == 'nt'",
    "h11==0.16.0",
    "idna==3.11",
    "outcome==1.3.0.post0",
    "pycparser==2.23 ; implementation_name != 'PyPy' and implementation_name != 'pypy' and os_name == 'nt'",
    "pysocks==1.7.1",
    "selenium==4.38.0",
    "sniffio==1.3.1",
    "sortedcontainers==2.4.0",
    "trio==0.32.0",
    "trio-websocket==0.12.2",
    "typing-extensions==4.15.0",
    "urllib3==2.5.0",
    "webdriver-manager>=4.0.2",
    "websocket-client==1.9.0",
    "wsproto==1.2.0",
]
```

Run this magic spell to install all dependencies:

```bash
uv sync
```

Boom! Now your environment is all ready to launch into the **web scraping universe**. 🛸


---


## 🌐 Connecting Selenium and Chromium (The Fun Part 🎉)

Before we dive into the coding realm, we need to figure out where **Chromedriver** is hanging out on your system. You can do that with:

```bash
which chromedriver
```

For me, it was located here:

```bash
/usr/bin/chromedriver
```

Make sure to remember this path, because you’ll need it when setting up **Selenium**. 🧠


---

## 🧑‍💻 Writing the Script (Let’s Scrape Some Quotes! 💬)

In your `test` project, open the **main.py** file and add this magic code to scrape quotes from a website:


```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.chrome.service import Service

URL = "http://quotes.toscrape.com"

def scrape(url):
    """
    Scrape a given URL for quotes.
    """
    chrome_options = Options()

    chromedriver_path = "/usr/bin/chromedriver" 

    # Use the new headless mode (recommended for Chrome/Chromium v109+)
    chrome_options.add_argument("--headless=new") 
    chrome_options.add_argument("--no-sandbox")
    chrome_options.add_argument("--disable-dev-shm-usage")
    chrome_options.add_argument("--disable-gpu") 

    webdriver_service = Service(executable_path=chromedriver_path)

    with webdriver.Chrome(service=webdriver_service, options=chrome_options) as driver:
        driver.get(url)
        print(f"Scraping {driver.title}...")

        time.sleep(2)

        quotes = driver.find_elements(By.CLASS_NAME, "quote")
        for quote in quotes:
            text = quote.find_element(By.CLASS_NAME, "text").text
            author = quote.find_element(By.CLASS_NAME, "author").text
            print(f'"{text}" - {author}')

if __name__ == "__main__":
    scrape(URL)
```

<br>

### 🧙‍♂️ The Moment of Truth: Run Your Script!

Once you run your script, you should see a glorious output like this:

```bash
Scraping Quotes to Scrape...
"“The world as we have created it is a process of our thinking. It cannot be changed without changing our thinking.”" - Albert Einstein
"“It is our choices, Harry, that show what we truly are, far more than our abilities.”" - J.K. Rowling
"“There are only two ways to live your life. One is as though nothing is a miracle. The other is as though everything is a miracle.”" - Albert Einstein
"“The person, be it gentleman or lady, who has not pleasure in a good novel, must be intolerably stupid.”" - Jane Austen
"“Imperfection is beauty, madness is genius and it's better to be absolutely ridiculous than absolutely boring.”" - Marilyn Monroe
"“Try not to become a man of success. Rather become a man of value.”" - Albert Einstein
"“It is better to be hated for what you are than to be loved for what you are not.”" - André Gide
"“I have not failed. I've just found 10,000 ways that won't work.”" - Thomas A. Edison
"“A woman is like a tea bag; you never know how strong it is until it's in hot water.”" - Eleanor Roosevelt
"“A day without sunshine is like, you know, night.”" - Steve Martin
```

<br>

And there you go, **web scraping magic** in full swing! 🧙‍♀️✨


---


## 🎉 Conclusion: You've Conquered the Web Scraping Galaxy! 🌍

Congratulations, brave adventurer! 🏆

 You've successfully installed Selenium, Chromedriver, and created a working scraper on your Raspberry Pi 4. All that’s left is to **scrape the internet**, and **take over the web** (in the most ethical way, of course 😉). Good luck, and may the quotes always be with you! 🚀🌟
