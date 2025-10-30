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
This is what you'll see if you've got Python 3.12 installed:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
cpython-3.12.3-linux-x86_64-gnu    /usr/bin/python3.12
cpython-3.12.3-linux-x86_64-gnu    /usr/bin/python3 -> python3.12
</code>
</pre>


--- 

### Install Python 3.14 🎉

Want to try out the shiny new Python 3.14? It’s just one command away:

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


Boom! Python 3.14 installed in under 5 seconds—talk about speed! ⚡

--- 

### Switch to the New Python Version 🔄

Now that Python 3.14 is installed, let's **pin** it as your default:

```bash
uv python pin 3.14
```
Output:

<pre style="background-color: #381d47ff; padding: 10px; border-radius: 5px;">
<code>
Updated `.python-version` from `3.12` -> `3.14`
</code>
</pre>


You’re now rocking Python 3.14 🎸!

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

<br><br>

So, to sum up:

 * **pyproject.toml** = your project’s blueprint 🏗️

 * **lock file** = your version control superhero 🦸‍♂️

With this combo, you're guaranteed a portable, stable, and reproducible environment! ✨

---
