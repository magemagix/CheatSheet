# UV Cheat Sheet🚀

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


Yay, you’re good to go! 🎉

---

## Package, Install, Update, and Remove 📦

Alright, let's move on to managing packages! Whether you're installing a new package, updating an old one, or removing something you don’t need, uv's got your back.

Continue ...
