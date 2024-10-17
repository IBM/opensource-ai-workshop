# Pre-work

These are the required applications and general installation notes for this workshop.

You'll need:

* [Ollama](#ollama) - This application allows you to locally host an LLM model on your computer.

* [Visual Studio Code](#visual-studio-code) - We'll be walking through an extension to VSCode in this workshop.

* [Python](#python) - Python is required because of InstructLab, and the demo code will be run on it.

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

<img src="https://count.asgharlabs.io/count?p=/prework_opensource_ai_page>
