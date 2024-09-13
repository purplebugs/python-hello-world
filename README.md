# python-hello-world

## Purpose

Try Python install on Mac and running a simple python program

## Install

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
