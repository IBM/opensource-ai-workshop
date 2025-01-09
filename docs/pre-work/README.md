# Pre-work

These are the required applications and general installation notes for this workshop.

You'll need:

- [Ollama](#ollama) - This application allows you to locally host an LLM model on your computer.
- [Visual Studio Code](#visual-studio-code) - We'll be walking through an extension to VSCode in this workshop. OR
- [One of the Jetbrains IDEs](#jetbrains) - You can choose the one you want, if the wifi is bad, please reach out to a TA to give you a USB stick.
- [Python](#python) - If you don't already have a proficently in a languge, please follow the `python` steps.
- [AnythingLLM](#anythingllm) - This will be a GUI interface to your LLM(s).
- [Open WebUI](#open-webui) - This is a browser based GUI for your LLM(s).

## Ollama

#### Mac installation steps

##### Download via the Ollama website

[Download Ollama](https://ollama.com/download/Ollama-darwin.zip) via the website.

Unzip the folder, and move the Ollama app to your applications folder.

##### Terminal Installation

Open up a terminal, and install [homebrew](https://brew.sh/).

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After the installation is complete, install [ollama](https://ollama.com) via `brew`.

```bash
brew install ollama
```

### Windows installation steps

Install ollama via the website [here](https://ollama.com/download/windows).

## Visual Studio Code

#### Mac installation steps

Open up a terminal, and install [homebrew](https://brew.sh/), if you didn't install this during the Ollama step.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After the installation is complete, install [vscode](https://code.visualstudio.com/) via `brew`.

```bash
brew install --cask visual-studio-code
```

## Jetbrains

Head on over to [here](https://www.jetbrains.com/ides/#choose-your-ide) and
download the IDE if you haven't already. If you are leveraging `python` like
this workshop will be, you should pick
[PyCharm](https://www.jetbrains.com/pycharm/)

## Python

Python is a whole programming language. There are multiple ways to install it, and
[here is the official website](https://www.python.org). Please take a moment and if you can't run
the following command, reach out to a teaching assistant or instructor to help you
 get resolved.

!!! note
    If you have an older version of python, or default "OS" versions of python, you'll need to update.

```bash
python --version
Python 3.11.4
```

#### Mac installation steps

##### Terminal Installation

If you need to install Python via `brew` please do the following:
```bash
brew install python@3.11
```

Please confirm that your `python --version` is at least `3.11+` for the best experience.

With this you should have the applications you need, let's start the workshop!

## AnythingLLM

Head on over [here](https://anythingllm.com/desktop) choose the correct version
for your Operating System. We will configure it later in the workshop.

## Open-Webui

If you have decided to run the Web Based/Browser based way to interact with your LLM(s) [open-webui](https://github.com/open-webui/open-webui)
is a fine if not _the_ defacto choice.

!!! note
    You only need to pick one of AnythingLLM or Open-WebUI, though you could
    pick both, it's really up to you!

Assuming you've set up [Python](#python) above, you'll need the following commands
to get it installed.

```bash
cd ~
mkdir openweb-ui
cd openweb-ui
python3.11 -m venv --upgrade-deps venv
source venv/bin/activate
pip install open-webui
open-webui serve
```
