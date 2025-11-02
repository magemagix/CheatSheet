# UV Cheat Sheet🚀

## UV Package Manager Guide 📦🎉

Welcome to the **UV Cheat Sheet**! If you're diving into the world of managing projects and Python versions like a pro, you're in the right place. Let's make things *fun* and *easy*, so you can spend less time fiddling with setups and more time coding!🖥️✨

--- 

## Project, Environment, and Python🐍

### Initialize a Project 🚧

Getting started with a new project? It’s as simple as 1-2-3!

```bash
# Create a folder "project" 
uv init project
```

The `uv init` command in UV doesn’t create a virtual environment by default. Instead, it helps you set up your project structure within the chosen directory 🗂️, including a `pyproject.toml` file and other important project files 🔧.

But don’t worry, if you want to create a virtual environment, you can easily do that with the `uv venv` command 🐍! Just specify the Python version if you need (e.g., `uv venv --python 3.10`) and voila! 🎉 You can then activate it like any other virtual environment and get to work! 🚀


```bash
uv venv --python 3.12
```


Now, take a peek at the content of your shiny new project folder! If you have the tree command installed, go ahead and run:

```bash
cd project 
tree  -La 1 ./
```
Output should look like this:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
./
├── .git
├── .gitignore
├── main.py
├── pyproject.toml
├── .python-version
├── README.md
├── uv.lock
└── .venv

3 directories, 6 files
</code>
</pre>


Nice, right? You’ve got a **.git** folder for version control, **pyproject.toml** for Python project settings, and, of course, a **.venv** folder for your virtual environment! 👏


You’ve got an existing project? No problem! Let’s jump right in. Head to your project folder and run this:

```bash
uv init .
```

This will initialize UV in your project and get everything set up in a flash! ⚡


---

### Activate and Deactivate 🧙‍♂️

Activating and deactivating your environment is just like working with venv. Here’s the magic:

```bash
# Activate your environment
source .venv/bin/activate  

# Deactivate it when you're done
deactivate 
```

Now you’re ready to code in your virtual environment like a true wizard! 🪄✨


---


### List Available Python Versions 🧙‍♂️

Wondering what Python versions you can use? No problem:

```bash
uv python list
```

And if you're curious about what Python versions you already have installed, check this out:

```bash 
uv python list --only-installed
```
This is what you'll see if you've got **Python 3.12** installed:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
cpython-3.12.3-linux-x86_64-gnu    /usr/bin/python3.12
cpython-3.12.3-linux-x86_64-gnu    /usr/bin/python3 -> python3.12
</code>
</pre>


--- 

### Install Python 3.14 🎉

Want to try out the shiny new **Python 3.14**? It’s just one command away:

```bash
uv python install 3.14
```
You'll see something like this:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Installed Python 3.14.0 in 4.51s
 + cpython-3.14.0-linux-x86_64-gnu (python3.14)
</code>
</pre>


Boom! **Python 3.14** installed in under 5 seconds—talk about speed! ⚡

--- 

### Switch to the New Python Version 🔄

Now that **Python 3.14** is installed, let's **pin** it as your default:

```bash
uv python pin 3.14
```
Output:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Updated `.python-version` from `3.12` -> `3.14`
</code>
</pre>


You’re now rocking **Python 3.14** 🎸!

---

### Check Python Path 🕵️‍♂️

Want to check where Python is located in your project? Easy peasy:

Check the python path:
```bash 
uv run which python 
```

Output will look something like:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
project/.venv/bin/python
</code>
</pre>

Looks like your virtual environment is ready to go!

---

### Check Python Version 🔍

Finally, let's confirm you're running the version you want:

```bash
uv run python --version
```

And the output?

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Python 3.14.0
</code>
</pre>


Note that if you want to change the version of Python in your project, just manually change "requires-python" into e.g. `>=3.14` in **pyproject.toml**.

Yay, you’re good to go! 🎉

---

## Package, Install and Remove 📦🎉

Ready to manage your project dependencies like a boss? Let’s go! Whether you're installing, upgrading, or removing packages, uv makes it super easy. 🎯



### Adding Packages✨

Need to add a new package? It’s as simple as:

```bash
uv add pandas matplotlib 
```
Here, we’ve added two popular packages: pandas (for data manipulation) and matplotlib (for data visualization). 🎨📊

Pretty fast, right? 🚀 You just ran this command and *boom*, the packages are in your environment! It's just like `pip install pandas matplotlib`, but way cooler. 😎

But wait, you can also use `pip`-style commands if you like the old ways:

```shell
uv pip install pandas matplotlib
```

🌱 Want to dive into your project's dependencies? Just run this simple command:

```bash
uv tree
```
🌳 It will give you a cool, tree-like view of all the packages and their dependencies! 📦✨

Check out the example below to see how it looks:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Resolved 15 packages in 1ms
project v0.1.0
├── matplotlib v3.10.7
│   ├── contourpy v1.3.3
│   │   └── numpy v2.3.4
│   ├── cycler v0.12.1
│   ├── fonttools v4.60.1
│   ├── kiwisolver v1.4.9
│   ├── numpy v2.3.4
│   ├── packaging v25.0
│   ├── pillow v12.0.0
│   ├── pyparsing v3.2.5
│   └── python-dateutil v2.9.0.post0
│       └── six v1.17.0
└── pandas v2.3.3
    ├── numpy v2.3.4
    ├── python-dateutil v2.9.0.post0 (*)
    ├── pytz v2025.2
    └── tzdata v2025.2
(*) Package tree already displayed
</code>
</pre>


If you’re feeling fancy and need to install a specific version, just follow this pattern:

```bash
uv add numpy==2.3.4
```

And if you want to downgrade or upgrade the package version, no worries! Just run the same command with your desired version. For example, if you want to switch numpy from version `2.3.4` to `2.3.1`:

```bash
uv add numpy==2.3.1
```

And the output is somthing like:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Resolved 12 packages in 275ms
      Built numpy==2.3.1
Prepared 1 package in 1m 19s
Uninstalled 1 package in 4ms
Installed 1 package in 5ms
 - numpy==2.3.4
 + numpy==2.3.1
</code>
</pre>

💡 Pro Tip: When switching versions, you might notice your CPU fan spinning up a little. Don't panic! 😱 It’s just uv working its magic at full speed by employing threads! 🔥


Want to check out all available versions of a package? Simple! Run this:

```bash
uvx pip index versions numpy  # get the list of numpy versions
```

And here’s an example of the output:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Installed 1 package in 18ms
numpy (2.3.4)
Available versions: 2.3.4, 2.3.3, 2.3.2, 2.3.1, 2.3.0, 2.2.6, 2.2.5, 2.2.4, 2.2.3, 2.2.2, 2.2.1, 2.2.0, 2.1.3, 2.1.2, 2.1.1, 2.1.0, 2.0.2, 2.0.1, 2.0.0, 1.26.4, 1.26.3, 1.26.2, 1.25.2, 1.25.1, 1.25.0, 1.24.4, 1.24.3, 1.24.2, 1.24.1, 1.24.0, 1.23.5, 1.23.4, 1.23.3, 1.23.2, 1.23.1, 1.23.0, 1.22.4, 1.22.3, 1.22.2, 1.22.1, 1.22.0, 1.21.1, 1.21.0, 1.20.3, 1.20.2, 1.20.1, 1.20.0, 1.19.5, 1.19.4, 1.19.3, 1.19.2, 1.19.1, 1.19.0, 1.18.5, 1.18.4, 1.18.3, 1.18.2, 1.18.1, 1.18.0, 1.17.5, 1.17.4, 1.17.3, 1.17.2, 1.17.1, 1.17.0, 1.16.6, 1.16.5, 1.16.4, 1.16.3, 1.16.2, 1.16.1, 1.16.0, 1.15.4, 1.15.3, 1.15.2, 1.15.1, 1.15.0, 1.14.6, 1.14.5, 1.14.4, 1.14.3, 1.14.2, 1.14.1, 1.14.0, 1.13.3, 1.13.1, 1.13.0, 1.12.1, 1.12.0, 1.11.3, 1.11.2, 1.11.1, 1.11.0, 1.10.4, 1.10.2, 1.10.1, 1.10.0.post2, 1.9.3, 1.9.2, 1.9.1, 1.9.0, 1.8.2, 1.8.1, 1.8.0, 1.7.2, 1.7.1, 1.7.0, 1.6.2, 1.6.1, 1.6.0, 1.5.1, 1.5.0, 1.4.1, 1.3.0
</code>
</pre>

If you’re into version constraints, say you only want plotly version `5.x` (not picky on patch versions), use this:

```bash 
uv add plotly==5.*
```

And here’s what the output looks like after installation:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Resolved 17 packages in 942ms
Prepared 3 packages in 3.46s
Installed 5 packages in 106ms
 + pandas==2.3.3
 + plotly==5.24.1
 + pytz==2025.2
 + tenacity==9.1.2
 + tzdata==2025.2
</code>
</pre>


To see what packages are installed in your environment, just run:

```bash 
uv pip list
```

Check out an example of the output:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Package         Version
--------------- -----------
contourpy       1.3.3
cycler          0.12.1
fonttools       4.60.1
kiwisolver      1.4.9
matplotlib      3.10.7
numpy           2.3.1
packaging       25.0
pandas          2.3.3
pillow          12.0.0
plotly          5.24.1
pyparsing       3.2.5
python-dateutil 2.9.0.post0
pytz            2025.2
six             1.17.0
tenacity        9.1.2
tzdata          2025.2
</code>
</pre>



Got a requirements.txt file? No worries! Installing packages is just like using pip:

```bash 
uv add -r requirements.txt
```
Boom! All your packages will be installed in one go. Easy, right? 😎

---


### Removing Packages 🧹


Okay, now let's clean up! To remove a package from your environment, just run:

```bash
uv remove plotly
```

And poof, the package is gone, along with its dependencies (it’s so fast it feels like magic 🧙‍♂️):

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Resolved 15 packages in 19ms
Uninstalled 2 packages in 86ms
 - plotly==5.24.1
 - tenacity==9.1.2
</code>
</pre>


If you want to remove multiple packages at once,

```bash 
uv remove plotly matplotlib
```

---

### TOML File📄

A **.toml** file (short for *Tom's Obvious, Minimal Language*) is a simple, human-readable configuration format that is often used to define settings, environment variables, and manage dependencies. It's like the roadmap of your project—guiding the tools and packages on where to go and what to do. 😎

In modern Python projects, you'll see it popping up with tools like *Poetry*, *Pipenv*, *FastAPI*, and even in systems like *Rust's Cargo*. You know, the cool kids of the dev world! 😁

#### Check Out Your TOML Before Adding Packages

Before we dive into adding any packages, let's take a peek at what’s inside your **pyproject.toml** file. Trust me, it’s like looking at the blueprint of your project! 🧐

To open the file:

```bash
nano pyproject.toml
```
And voilà! You'll see something like this:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[project]
name = "project"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = []
</code>
</pre>

Looks a bit plain right now, huh? But don’t worry—we’re about to jazz it up with some dependencies! 💥

#### Adding Packages to Your TOML File 🎉

Now, let’s add some packages to your project! We’re going to bring in **matplotlib** (for plotting and charting) and **pandas** (for data manipulation). Here's how:


```bash 
uv add  matplotlib==3.6.2   pandas
```

Check it out—your **dependencies** section will look like this now:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[project]
name = "project"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = [
    "matplotlib==3.6.2",
    "pandas>=2.3.3",
]
</code>
</pre>



Boom! 💥 Now your project knows exactly which versions of matplotlib and pandas it needs!


---



### Lock File 🔐

The **lock file** is your project’s secret weapon. Think of it as a safety net for your dependencies—ensuring that everyone, from your local setup to CI/CD pipelines, gets the same exact versions of all the packages. No surprises. 🎯

When you list dependencies in **pyproject.toml**, you might use version ranges like `uvicorn >=0.14,<0.17`. But guess what? The **lock file** locks it down to a specific version—like a super precise GPS 🧭. For example, it’ll save the version as `uvicorn==0.16.0` so no one else gets a random version of it. This guarantees no weird bugs or errors just because someone got a slightly different version. 🙅‍♂️

🔒 Keep your lockfile up to date with just one command:

```bash
uv lock
```


<br><br>

So, to sum up:

 * **pyproject.toml** = your project’s blueprint 🏗️

 * **lock file** = your version control superhero 🦸‍♂️

With this combo, you're guaranteed a portable, stable, and reproducible environment! ✨

<br><br>

#### 📤 Exporting and Sharing Your Lockfile 🗂️

When you want to **export** your **UV lockfile** to share it with others or for use in a different environment, you can easily do so with a couple of simple commands. UV offers flexibility in choosing the format and the output file name for your lockfile.

#### 🔒 1. Exporting in TOML Format (pylock)

To export your lockfile in **TOML format**, you'll use the `--format` flag with `pylock.toml` as the format. **It's important to note** that the output filename must start with `pylock.` and end with `.toml`. This ensures that the file is recognized correctly in subsequent commands.

For example:

```bash
uv export --format pylock.toml --output-file pylock.final.toml
```
This will generate a TOML-formatted lockfile named `pylock.final.toml`, which you can then share or use in your project. 😎

#### 💡 Important!:

Files like `my.toml` won’t be recognized as a valid `pylock.toml` file in future operations. Stick to the `pylock.*.toml` naming convention.



#### 📄 2. Exporting in TXT Format (requirements.txt)

If you prefer to work with **requirements.txt**, UV supports exporting your lockfile to the traditional `.txt` format, which is widely used in Python projects for specifying dependencies.

To export your lockfile in **requirements.txt** format, use this command:

```bash
uv export --format requirements.txt --output-file requirements.txt
```
This will generate a `requirements.txt` file that contains all your locked dependencies, ready to be shared or installed using pip.

To install the dependencies, use this command:

``bash
uv add -r requirements.txt
```

#### 🚀 Why Export and Share Your Lockfile?

🧑‍🤝Collaborate easily: Share your lockfile with teammates so that everyone uses the exact same versions of dependencies.

🛠️ Consistency: Ensure that your project dependencies are locked and consistent across different environments or deployments.



---

## Upgrade, Downgrade, and Synchronize 🔄

Sometimes, you need to jump to a specific version of a package—like going back in time for **numpy**. Whether it's to fix a bug or ensure compatibility, managing versions is part of the game. Here’s how you can upgrade, downgrade, or synchronize your project’s dependencies to make it behave just the way you want! 🎮

### Install a Specific Version ⬇️

```bash 
uv add "numpy<=2.1.0"
```

Now, when you peek inside your **pyproject.toml**, it will show:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[project]
name = "project"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = [
    "numpy<=2.1.0",
]
</code>
</pre>

And, in the **lock file**, you’ll see the exact version that’s installed:


<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[[package]]
name = "numpy"
version = "2.1.0"
.
.
.
</code>
</pre>



### Upgrade or Downgrade Without Changing Anything? 😬


You might try these commands to upgrade numpy:

```bash
uv add "numpy" --upgrade
uv add "numpy"
```
But guess what? **No change** happens here in either the **toml** or **lock** files. 😅 These commands don’t do what you expect!

So, how do you upgrade? Simple!


### How to Properly Upgrade 🆙

To upgrade **numpy** from version `2.1.0` to `2.3.2`, use this command:


```bash
uv add "numpy>=2.3.2"
```
Now, check your **pyproject.toml**, and it’ll look like this:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[project]
name = "project"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = [
    "numpy>=2.3.2",
]
</code>
</pre>

In your **lock file**, you’ll now see the exact version installed:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[[package]]
name = "numpy"
version = "2.3.4"
.
.
.
</code>
</pre>

### Downgrading? Just a Matter of Version 🎯

Want to downgrade? Use the same trick! Just specify the version you need, and you’re good to go. It’s as simple as that. 😉

**Upgrade** and **downgrade** (or let’s call it "**dupgrade**" for fun 😜) are straightforward. But remember: your package must have a release compatible with your Python version. Otherwise, no dice! 🙅‍♂️

<br><br> 

### The Magic of Synchronizing Your Project 🔄✨

Let’s say you have an empty project, and you want to install numpy:

```bash
uv add "numpy>=2.1.0"
```
Here’s what your **pyproject.toml** will look like after installing numpy:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[project]
name = "project"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = [
    "numpy>=2.1.0",
]
</code>
</pre>

Let’s say later, a newer version of **numpy** gets released. You decide to upgrade, but the **toml** file still shows the same:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
dependencies = [
    "numpy>=2.1.0",
]
</code>
</pre>

And before the upgrade, **numpy** in your **lock file** was at:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[[package]]
name = "numpy"
version = "2.2.4"
</code>
</pre>

If you want to upgrade **numpy** to the latest **compatible** version, simply run:

```bash 
uv sync --upgrade-package numpy
```
After syncing (= synchronizing), your **pyproject.toml** will stay the same (no changes here):

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[project]
name = "project"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = [
    "numpy>=2.1.0",
]
</code>
</pre>

But look at that **lock file**! It reflects the exact upgraded version:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
[[package]]
name = "numpy"
version = "2.3.4"
</code>
</pre>


<br><br>

### Upgrade Everything at Once 🚀


Want to upgrade all packages at once? Easy!

```bash
uv sync --upgrade
```
So, sync your project’s dependencies across both configuration files (**pyproject.toml** and the **lock file**).

This will ensure all packages are up-to-date, but be aware that when you sync, the **lock file** will reflect the exact versions after the process. So if any changes happened, the installed versions will be updated accordingly. 🔄

<br>
<br>

### Final Tip: Manual Upgrades and Downgrades 🛠️

You can totally tweak the versions in your **pyproject.toml** manually—whether you’re upgrading or downgrading—but if you want to keep everything nice and consistent, the syncing commands are your best friend. 👫 Run them to make sure all your dependencies are dupgraded in one go, and your environment stays perfectly in sync! 💥🔄

<br><br>

And that’s it! 🎉 Whether you’re upgrading, downgrading, or just keeping everything in sync, this is your go-to guide for managing dependencies like a pro!

---


## Run Python🐍, Scripts, and Jupyter 🚀

Introduction


Accessing Python in your environment is as easy as pie—two simple ways to get started!

#### 1️⃣ The Easy Way: Just Run Python with uv!

No fuss, no muss. Just type:

```bash
uv run python
```

#### 2️⃣ The Classic Way: Activate Your Environment and Run Python

Or, if you like the good ol' activation method, you can always go for:

```bash
source .venv/bin/activate && python
```

#### Run a Script? Easy Peasy 🍋

Same deal as above:

```bash 
uv run my_script.py
```
or, if you prefer to activate your environment first:

```bash
source .venv/bin/activate && python my_script.py
```

Of course, the first method is quicker, but hey—it's all about `choice` and what feels best for you! 😎


#### 📚 My Lovely Jupyter (Lab or Not!) 💻

So, you're a Jupyter fan, huh? Whether you love the classic Jupyter Notebook or you're all about that Jupyter Lab life, I've got you covered! 😁


Let's start with the easy method! To install and launch Jupyter Lab, just one line:

```bash
uvx jupyter lab
```
Boom! You're ready to go. 🔥

#### Want a Specific Python Version? No Problem! 🎯 

If you're feeling fancy and want to run Jupyter Lab with a specific version of Python (like 3.14), just do:

```bash
uvx --python 3.14 jupyter lab
```

Easy, right? 🙌

### Installing Packages Inside Jupyter 🛠️ 

Remember how we install packages in a notebook? Well, you can do the same thing here! 💡

```bash
uv pip install pandas
```
Simple, right? ✨

### Installing Jupyter Notebook with Widgets & Autocomplete 🧑‍💻

Okay, now let's talk about Jupyter Notebook with some extra goodies, like widgets and autocomplete support. It's super easy!

Here’s my secret recipe for Jupyter—easy, effective, and just a little bit magical! ✨

```bash
uv add notebook==6.1.5 && uv add  jupyter_contrib_nbextensions && uv run jupyter contrib nbextension install --user  && uv run jupyter nbextension enable varInspector/main && uv run jupyter nbextension enable spellchecker/main  && uv run jupyter nbextension enable codefolding/main 
```
I know, it's a lot, but don't worry—this will get your environment all set up with the cool features! 😎

#### Verify Installation in the pyproject.toml File 🧾

To make sure everything's set up right, check your `pyproject.toml`:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>                             
[project]
name = "proj"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.14"
dependencies = [
    "jupyter-contrib-nbextensions>=0.7.0",
    "notebook==6.1.5",
]
</code>
</pre>

### 🏃‍♂️ Running Jupyter Notebook

Once everything is installed, you can launch your Jupyter Notebook like a pro:


```bash
uv run jupyter notebook --ip='*' --NotebookApp.token='' --NotebookApp.password=''
```
Note: I added `--NotebookApp.token=''` and `--NotebookApp.password=''` because, well, Jupyter sometimes asks for a token. This way, you can just jump straight into your notebooks without any interruptions. 😅


#### Reveal the Secret of uvx 🔍 

So, what’s the deal with uvx? 🤔

Think of `uvx` as a super handy shortcut. When you use it, tools get installed in their own temporary, isolated environments. No mess, no fuss! 🎉

But, if you’re running a tool that needs your project to be installed first—like when you're using pytest or mypy—then you’ll want to use `uv run` instead of `uvx`. It’s that simple! ✌️


---


## Build Your Own Package: Let's Make Some Magic! 🪄

UV makes it easy to create a python package and share it with community. 

Ready to create your very own Python package and share it with the world? 🌍 Let's dive into building something useful—how about a package that computes square roots and sums of squares? We’ll call it **magic** ✨.

### Step 1: Set Up the Project 🏗️

To get started, we need to initialize our package. Just run this command:

```bash
uv init --lib magic
```

Once that’s done, let's take a look at the files in our new **magic** project! 📂

```bash
cd magic
tree -aL 2
```
This will give you an overview of your project structure. Here’s what it should look like:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>                             
.
├── .git
│   ├── branches
│   ├── config
│   ├── description
│   ├── HEAD
│   ├── hooks
│   ├── info
│   ├── objects
│   └── refs
├── .gitignore
├── pyproject.toml
├── .python-version
├── README.md
└── src
    └── magic

9 directories, 7 files
</code>
</pre>

### Step 2: Create Your Scripts ✍️

Next, let’s create the magic ✨. In our toy example, we’ll need **magic.py** and **magic_functions.py**.

#### 1. magic_functions.py: The Math Behind the Magic 🧮


In **magic_functions.py**, we'll define a class called `SimpleMath` with two main functions: 
 * `square_root`: To compute the square root of a number or numbers in vector.
 * `sum_of_squares`: To calculate the sum of squares of a list of numbers.

Here’s the code for **magic_functions.py**:

 ```python
class SimpleMath:
    def __init__(self):
        pass
    
    def square_root(self, value):
        """
        Returns the square root of the given number.
        """
        if value < 0:
            raise ValueError("Cannot compute the square root of a negative number.")
        return value ** 0.5
    
    def sum_of_squares(self, values):
        """
        Returns the sum of squares of the provided list of values.
        """
        return sum([value ** 2 for value in values])
```

#### 2. magic.py: Bringing the Magic to Life 🔮

Now, let’s create **magic.py**. This script will provide two useful functions:
 * `compute_square_roots`: Uses **magic_functions.py** to compute the square roots.
 * `compute_sum_of_squares`: Uses **magic_functions.py** to compute the sum of squares.

 Here’s what **magic.py** looks like:

```python
from .magic_functions import SimpleMath

def compute_square_roots(values):
    """
    Computes the square roots of a list of values
    using the helper function from magic_functions (SimpleMath).
    """
    math_helper = SimpleMath()
    return [math_helper.square_root(value) for value in values]

def compute_sum_of_squares(values):
    """
    Computes the sum of squares of a list of values.
    """
    math_helper = SimpleMath()
    return math_helper.sum_of_squares(values)
```

#### Step 3: Organize the Files 📂

Now, let’s put everything in the right place. Inside the main folder of your project, **magic**, you'll also find a folder named **magic** inside the **src** folder 🗂️. This is where the real magic happens! ✨ Go ahead and place both **magic.py** and **magic_functions.py** in that folder, like this:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>                             
.
└── src
    └── magic
        ├── __init__.py
        └── py.typed
</code>
</pre>

now you will have the following structure:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>                             
.
└── src
    └── magic
        ├── __init__.py
        ├── magic_functions.py
        ├── magic.py
        └── py.typed
</code>
</pre>

You should also have an `__init__.py` file inside the **magic** folder. In `__init__.py`, add the following code to expose the methods from **magic.py**:



```bash
from .magic import compute_square_roots, compute_sum_of_squares
```

This ensures that when someone imports your package, they can access the functions from **magic.py** and not directly from **magic_functions.py**. ✨


#### Step 5: Add Dependencies (If Needed) 📦

If your package needs any external dependencies, simply add them using `uv add package_name`. Don’t forget to check your **pyproject.toml** file afterward. For our **magic** package, we don’t have any external dependencies, so we’re good to go!



#### Step 6: Check the pyproject.toml 🧾


Take a moment to explore the pyproject.toml file. It should look something like this:

```bash
[project]
name = "magic"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.14"
dependencies = []

[build-system]
requires = ["uv_build>=0.9.5,<0.10.0"]
build-backend = "uv_build"
```

Feel free to modify the name, version, and description to fit your package. ✍️ And don’t forget to fill out your README.md to make your package extra user-friendly! 📄


#### Step 7: Build Your Package 🔨


Now for the fun part—building the package! 🎉 Use this command:

```bash 
uv build
```
You should see something like this in the output:

```bash
Building source distribution (uv build backend)...
Building wheel from source distribution (uv build backend)...
Successfully built dist/magic-0.1.0.tar.gz
Successfully built dist/magic-0.1.0-py3-none-any.whl
```
Now, check the **dist** folder for your newly created `.tar.gz` and `.whl` files. 🏆

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>                             
.
├── dist
│   ├── .gitignore
│   ├── magic-0.1.0-py3-none-any.whl
│   └── magic-0.1.0.tar.gz
</code>
</pre>


#### Step 8: Install Your Package 🎉

You’ve made it! Now you can install your newly created package wherever you want. Just run:

```bash
uv pip install magic-0.1.0-py3-none-any.whl
```
And if you’re still developing the package, you’ll want to install it in editable mode so you can work directly with the source code without rebuilding it:

```bash
pip install -e .
```


#### 🎉 Congrats! You Did It! 🎉

You’ve just built and released your very own Python package! 🌟 Whether you’re sharing it with others or just using it for personal projects, you’ve learned the steps to create a Python package from scratch. Keep building and making magic happen! ✨



