---
title: Open Source AI Workshop Pre-Work or Setup
description: Setup or Pre-Work for the Open Source AI Workshop
logo: images/ibm-blue-background.png
---

These are the required applications and general installation notes for this workshop.

**Ollama** and **Python** are required for this workshop, but you can choose an IDE and GUI interface from the options provided. If you don't know what to select, just go with the recommended options!

*Remember, you can **always** ask the teacher for help if you get stuck on any step!*

## Required Software

- [Python](#installing-python)
- [Ollama](#installing-ollama) - Allows you to locally host an LLM model on your computer.
- An IDE - either [Visual Studio Code](#installing-visual-studio-code) **(Recommended)** or [any Jetbrains IDE](#installing-jetbrains). This workshop uses VSCode.

- A GUI - either [AnythingLLM](#installing-anythingllm) **(Recommended)** or [Open WebUI](#installing-open-webui). AnythingLLM is a desktop app while Open WebUI is browser-based.

## Installing Python

There are multiple ways to install Python, you can follow their [beginner's guide](https://wiki.python.org/moin/BeginnersGuide/Download) or try one of the options below:

### On a Mac

#### Via the Terminal

Install [Homebrew](https://brew.sh/) using the following command:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then, install Python via `brew`:

```bash
brew install python@3.11
```

Please confirm that your `python --version` is at least `3.11+` for the best experience.

## Installing Ollama

### On a Mac

#### Via the Desktop

Simply download Ollama from its [website](https://ollama.com/download), unzip the folder and move it into your applications folder.

#### Via the Terminal

Install [Homebrew](https://brew.sh/) using the following command:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then, install [Ollama](https://ollama.com) via `brew`:

```bash
brew install ollama
```

### On Windows

You can download and install Ollama from its [website](https://ollama.com/download).

## Installing Visual Studio Code

You can download and install VSCode from their [website](https://code.visualstudio.com/Download) based on your operating system..

!!! note
    You only need one of VSCode or Jetbrains for this lab.

## Installing Jetbrains

Download and install the IDE of your choice [here](https://www.jetbrains.com/ides/#choose-your-ide).
If you'll be using `python` (like this workshop does), pick [PyCharm](https://www.jetbrains.com/pycharm/).

## Installing AnythingLLM

Download and install it from their [website](https://anythingllm.com/desktop) based on your operating system. We'll configure it later in the workshop.

!!! note
    You only need one of AnythingLLM or Open-WebUI for this lab.

## Installing Open-WebUI

Assuming you've set up [Python](#installing-python) above, use the following commands to install Open-WebUI:

```bash
cd ~
mkdir openweb-ui
cd openweb-ui
python3.11 -m venv --upgrade-deps venv
source venv/bin/activate
pip install open-webui
open-webui serve
```

**Now that you have all of the tools you need, let's start the workshop!**
