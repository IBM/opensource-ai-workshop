---
title: Workshop Pre-Work
description: Install pre-requisites for the workshop
logo: images/ibm-blue-background.png
---

These are the required applications and general installation notes for this workshop.

**Ollama** and **Python** are required for this workshop, but you can choose an IDE and GUI interface from the options provided. If you don't know what to select, just go with the recommended options!

*Remember, you can **always** ask the teacher for help if you get stuck on any step!*

## Required Software

- [Python](#installing-python)
- [Ollama](#installing-ollama) - Allows you to locally host an LLM model on your computer.
- [Open WebUI](#installing-open-webui)

## Installing Python

There are multiple ways to install Python, you can follow their [beginner's guide](https://wiki.python.org/moin/BeginnersGuide/Download) based on your operating system.

### Using Homebrew (Mac)

Install [Homebrew](https://brew.sh/) using the following command:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then, install Python via `brew`:

```bash
brew install python@3.11
```

Please confirm that your `python --version` is at least `3.11+` for the best experience.

!!! note
    python 3.11 and 3.12 work best.  Python 3.13 has trouble with Open-WebUI at the moment.

## Installing Ollama

Most users can simply download Ollama from its [website](https://ollama.com/download).

### Using Homebrew (Mac)

Install [Homebrew](https://brew.sh/) using the following command:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then, install [Ollama](https://ollama.com) via `brew`:

```bash
brew install ollama
```

!!! note
    You can save time by starting the model download used for the lab in the background by running `ollama pull granite4:micro` in its own terminal. You might have to run `ollama serve` first depending on how you installed it.


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

## Conclusion

Now that you have all of the tools you need, head over to [Lab 1](https://ibm.github.io/opensource-ai-workshop/lab-1/) if you have AnythingLLM or [Lab 1.5](https://ibm.github.io/opensource-ai-workshop/lab-1.5/) for Open-WebUI.
