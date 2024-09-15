# python-hello-world 🐍

## Purpose 💖

Try Python install on Mac and running a simple python program

## Install Python on Mac 🪴

I followed [these instructions](https://www.freecodecamp.org/news/how-to-install-python-on-a-mac) for using [Rye](https://rye.astral.sh/) to install Python on a mac

Summary of steps

1. Pre-reqs: Check MacOS up to date, check python installed by XCode `python3 --version` (Python 3.9.6), check no other python installed `python --version` (Not found)

1. Install Rye

```
# Install Rye
curl -sSf https://rye.astral.sh/get | bash

# Options selected at prompts:

# Select y
Continue? (y/n)

# Select pip-tools
Select the preferred package installer

# Select this option
Run a Python installed and managed by Rye


# ENTER to select this as default
Which version of Python should be used as default toolchain? (cpython@3.12)

# n to set PATH manually
Should the installer add Rye to PATH via .profile? (y/n)
```

1. Set path for Rye

```
nano ~/.zprofile

# Add to last line in file

source "$HOME/.rye/env"
```

1. Quit terminal and re open to apply changes, or run this to pick up latest changes `source ~/.zprofile`

1. Verify versions

```
rye --version

# Should return new version installed, eg Python 3.12.5
python --version


# Should ALSO now return new version installed, eg Python 3.12.5
python3 --version
```

1. Note:

The which command shows the Rye shims directory when you try to see where Python is installed.
Keep in mind that you've set the ~/.zprofile file to use Rye shims to intercept the python command and deliver the Rye-installed versions.

```
$ which python
/Users/username/.rye/shims/python
```

## Create Python project 🎬

1. Create directory `python-hello-world` for files and repo
1. In the directory specify python version for project `rye pin 3` which creates a .python-version file specifying the newest Python version
1. Create a project specific pyproject.toml file in your project root directory `rye init`. Now it is possible to fetch a Python version and install packages.
1. Install a specific version `rye fetch` - if not newest specific in .python-version file
1. Install a package from the [Python Package Index](https://pypi.org/) `rye add cowsay` - first ensure `pyproject.toml` file was created in previous step
1. Sync to update lockfiles and install the dependencies into the virtual environment `rye sync`

## Run Python 🐮

Start python on the command line

1. `python`

At the prompts type

1. `import cowsay`
1. `cowsay.cow('Hello World')`

To quit

1. `quit()`

## Provide and run an executable python script 🤖

1. Add the following to `pyproject.toml´ file

```
[project.scripts]
"python-hello-world" = "python_hello_world:hello"
```

1. Create file `__main__.py` with

```
import python_hello_world
import sys

sys.exit(python_hello_world.hello())
```

1. Run `rye sync`
1. Run the script `rye run python-hello-world`

Note: Otherwise init an exectuable project from the start `rye init --script my-project` as per [Executable projects](https://rye.astral.sh/guide/basics/#executable-projects)

## Development 🤓

Add software libraries to project

1. Add Requests HTTP library `python -m pip install requests`
1. Add Requests to `pyproject.toml` file `rye add requests`
1. Sync packages `rye sync`

Tip for beginners:

- When see `pip install` in a tutorial, use `rye add` and `rye sync` instead, without additional commands for a virtual environment.

## Not done 😬

- Have not run the `python_hello_world/__init__.py` file that was created
- Only have run the command `print("Hello World")` in the context of python running in the terminal
