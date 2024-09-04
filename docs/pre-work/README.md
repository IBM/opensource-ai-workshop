# Pre-work

These are the required applications and general installation notes for this workshop.

You'll need:
* [Ollama](#ollama) - This application allows you to locally host an LLM model on your computer.
* [Visual Studio Code](#visual-studio-code) - We'll be walking through an extension to VSCode in this workshop.
* [Python](#python) - Python is required because...?? ## TODO

## Ollama

#### Mac installation steps

##### Download via the Ollama website

[Download Ollama](https://ollama.com/download/Ollama-darwin.zip) via the website.

Unzip the folder, and move the Ollama app to your applications folder.

##### -OR- Terminal Installation

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

### Windows installation steps

Install Code via the website [here](https://code.visualstudio.com/Download).

## Python

Python is a whole programming language. There are multpile ways to install it, and
[here is the offical website](https://www.python.org). Please take a moment and if you can't run
the following command, reach out to a teaching assissant or instructor to help you
get resolved.

```bash
python --version
Python 3.12.4
```

Please confirm that your `python --version` is at least `3.11+` for the best experiance.

With this you should have the applications you need, let's start the workshop!

<img src="https://count.asgharlabs.io/count?p=/prework_opensource_ai_page>
