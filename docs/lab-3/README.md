---
title: Getting Started with InstructLab
description: Steps to get ilab working on a Mac
logo: images/ilab_dog.png
---

# Getting Started with InstructLab

!!! tip
    We are jumping in the deep end here, don't hesitate to raise your hand and ask questions.
    We also assume you have a good _foundational_ (heh) knowledege of `python` if not, ask
    one of the TA's to run through this on the overhead screen.

Now that we have a working VSCode instance working with the granite model, lets talk about more
things you can do with an Open Source AI system. This is where the [InstructLab](https://instructlab.ai/)
project comes into play.

Now that we've used the foundation model from upstream, lets add some knowledge to our model that we want
it to have.

## Steps

### Install `ilab`

1) Open up `iTerm2` or `Terminal` (assuming you're on a Mac and we'll continue assuming this) and create a new directory called `instructlab` to store the files the `ilab`
CLI needs when running and `cd` into the directory by running the following command:

```shell
mkdir instructlab
cd instructlab
```

!!! note
    The following steps in this document use [Python venv](https://docs.python.org/3/library/venv.html) for virtual environments.

2) There are a few ways you can locally install the `ilab` CLI. Select your preferred installation method from the following instructions. You can then install `ilab` and activate your `venv` environment.

!!! note
    ⏳ `pip install` may take some time, depending on your internet connection. In case installation fails with error ``unsupported instruction `vpdpbusd'``, append `-C cmake.args="-DLLAMA_NATIVE=off"` to `pip install` command.

3) Install with Apple Metal on M1/M2/M3 Macs

!!! note
    Make sure your system Python build is `Mach-O 64-bit executable arm64` by using `file -b $(command -v python)`,
    or if your system is setup with [pyenv](https://github.com/pyenv/pyenv) by using the `file -b $(pyenv which python)` command.

```shell
python3 -m venv --upgrade-deps venv
source venv/bin/activate
pip cache remove llama_cpp_python
pip install 'instructlab[mps]' # yes you will need the 's
```

4) From your `venv` environment, verify `ilab` is installed correctly, by running the `ilab` command.

```shell
ilab --version
ilab, version 0.19.3
```

!!! important
    Every `ilab` command needs to be run from within your Python virtual environment. You can enter the Python environment by running the `source venv/bin/activate` command.

### 🏗️ Initialize `ilab`

1) Initialize `ilab` by running the following command:

```shell
ilab config init
```

*Example output*

```shell
Welcome to InstructLab CLI. This guide will help you to setup your environment.
Please provide the following values to initiate the environment [press Enter for defaults]:
```

2) When prompted by the interface, press **Enter** to add a new default `config.yaml` file.

3) When prompted, clone the `https://github.com/instructlab/taxonomy.git` repository into the current directory by typing **y**.


4) When prompted, provide the path to your default model. Otherwise, the default of a quantized [Merlinite](https://huggingface.co/instructlab/merlinite-7b-lab-GGUF) model will be used - you can download this model with `ilab model download` (see below).

   ```shell
   Welcome to InstructLab CLI. This guide will help you to setup your environment.
   Please provide the following values to initiate the environment [press Enter for defaults]:
   Path to taxonomy repo [/Users/USERNAME/.local/share/instructlab/taxonomy]:
   `/Users/USERNAME/.local/share/instructlab/taxonomy` seems to not exist or is empty. Should I clone https://github.com/instructlab/taxonomy.git for you? [Y/n]:
   Cloning https://github.com/instructlab/taxonomy.git...
   Path to your model [/Users/USERNAME/.cache/instructlab/models/merlinite-7b-lab-Q4_K_M.gguf]:
   Generating `/Users/USERNAME/.config/instructlab/config.yaml`...
   ```

5) When prompted, please choose a train profile. Train profiles are GPU specific profiles that enable accelerated training behavior. **YOU ARE ON MacOS**, please choose `No Profile (CPU-Only)` by hitting Enter. There are various flags you can utilize with individual `ilab` commands that will allow you to utilize your GPU if applicable.

   ```shell
   Please choose a train profile to use.
   Train profiles assist with the complexity of configuring InstructLab training for specific GPU hardware.
   You can still take advantage of hardware acceleration for training even if your hardware is not listed.
   [0] No profile (CPU, Apple Metal, AMD ROCm)
   [1] Nvidia A100/H100 x2 (A100_H100_x2.yaml)
   [2] Nvidia A100/H100 x4 (A100_H100_x4.yaml)
   [3] Nvidia A100/H100 x8 (A100_H100_x8.yaml)
   [4] Nvidia L40 x4 (L40_x4.yaml)
   [5] Nvidia L40 x8 (L40_x8.yaml)
   [6] Nvidia L4 x8 (L4_x8.yaml)
   Enter the number of your choice [hit enter for hardware defaults] [0]: 0
   No profile selected - any hardware acceleration for training must be configured manually.
   Initialization completed successfully, you're ready to start using `ilab`. Enjoy!
   ```

### `ilab` directory layout after initializing your system

After running `ilab config init` your directories will look like the following on a MacOS system:

```shell
├─ ~/.cache/instructlab/models/ (1)
├─ ~/.local/share/instructlab/datasets (2)
├─ ~/.local/share/instructlab/taxonomy (3)
├─ ~/.local/share/instructlab/checkpoints (4)
```

1) Contains all downloaded large language models, including the saved output of ones you generate with ilab.

2) Contains data output from the SDG phase, built on modifications to the taxonomy repository.

3) Contains the skill and knowledge data.

4) Contains the output of the training process

### 📥 Download the `granite-7b-lab` model

- Run the `ilab model download` command.

```shell
ilab model download --repository instructlab/granite-7b-lab-GGUF --filename=granite-7b-lab-Q4_K_M.gguf
```

!!! note
    When you run this command, this can take a while, we have put this file in `~/Downloads` for you
    so please `ctrl-c` out of the download, and check there. If not raise your hand and TA will bring
    you a copy of the file.

`ilab model download` downloads a compact version of the [granite-7b-lab model](https://huggingface.co/instructlab/granite-7b-lab) (~4.4G) from HuggingFace:

```shell
ilab model download --repository instructlab/granite-7b-lab-GGUF --filename=granite-7b-lab-Q4_K_M.gguf
Downloading model from Hugging Face: instructlab/granite-7b-lab-GGUF@main to /Users/USERNAME/.cache/instructlab/models...
Downloading 'granite-7b-lab-Q4_K_M.gguf' to '/Users/USERNAME/.cache/instructlab/models/.cache/huggingface/download/granite-7b-lab-Q4_K_M.gguf.6adeaad8c048b35ea54562c55e454cc32c63118a32c7b8152cf706b290611487.incomplete'
INFO 2024-10-17 12:01:31,702 huggingface_hub.file_download:1908: Downloading 'granite-7b-lab-Q4_K_M.gguf' to '/Users/USERNAME/.cache/instructlab/models/.cache/huggingface/download/granite-7b-lab-Q4_K_M.gguf.6adeaad8c048b35ea54562c55e454cc32c63118a32c7b8152cf706b290611487.incomplete'
granite-7b-lab-Q4_K_M.gguf: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 4.08G/4.08G [00:44<00:00, 92.2MB/s]
Download complete. Moving file to /Users/USERNAME/.cache/instructlab/models/granite-7b-lab-Q4_K_M.gguf
INFO 2024-10-17 12:02:16,191 huggingface_hub.file_download:1924: Download complete. Moving file to /Users/USERNAME/.cache/instructlab/models/granite-7b-lab-Q4_K_M.gguf
```
#### Listing downloaded models

All downloaded models can be seen with `ilab model list`.

```shell
ilab model list
```

*Example output of `ilab model list` after `ilab model download`*

```shell
ilab model list
+------------------------------+---------------------+--------+
| Model Name                   | Last Modified       | Size   |
+------------------------------+---------------------+--------+
| granite-7b-lab-Q4_K_M.gguf   | 2024-10-17 12:02:16 | 3.8 GB |
+------------------------------+---------------------+--------+
```

### 🍴 Serving the model

- Serve the model by running the following command:

```shell
ilab model serve --model-path ~/.cache/instructlab/models/granite-7b-lab-Q4_K_M.gguf
```

Once the model is served and ready, you'll see the following output:

```shell
ilab model serve --model-path ~/.cache/instructlab/models/granite-7b-lab-Q4_K_M.gguf

INFO 2024-10-17 12:05:55,634 instructlab.model.serve:136: Using model '/Users/USERNAME/.cache/instructlab/models/granite-7b-lab-Q4_K_M.gguf' with -1 gpu-layers and 4096 max context size.
INFO 2024-10-17 12:05:55,635 instructlab.model.serve:140: Serving model '/Users/USERNAME/.cache/instructlab/models/granite-7b-lab-Q4_K_M.gguf' with llama-cpp
INFO 2024-10-17 12:05:55,950 instructlab.model.backends.llama_cpp:232: Replacing chat template:
 {% for message in messages %}
{% if message['role'] == 'user' %}
{{ '<|user|>
' + message['content'] }}
{% elif message['role'] == 'system' %}
{{ '<|system|>
' + message['content'] }}
{% elif message['role'] == 'assistant' %}
{{ '<|assistant|>
' + message['content'] + eos_token }}
{% endif %}
{% if loop.last and add_generation_prompt %}
{{ '<|assistant|>' }}
{% endif %}
{% endfor %}
INFO 2024-10-17 12:05:55,951 instructlab.model.backends.llama_cpp:189: Starting server process, press CTRL+C to shutdown server...
INFO 2024-10-17 12:05:55,951 instructlab.model.backends.llama_cpp:190: After application startup complete see http://127.0.0.1:8000/docs for API.
```

### 📣 Chat with the model

Because you're serving the model in one terminal window, you will have to create a new window and re-activate your Python virtual environment to run `ilab model chat` command:

```shell
source venv/bin/activate
ilab model chat
```

Before you start adding new skills and knowledge to your model, you can check its baseline performance by asking it a question such as `what is the capital of Canada?`.

```shell
ilab chat
╭────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── system ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ Welcome to InstructLab Chat w/ GRANITE-7B-LAB-Q4_K_M.GGUF (type /h for help)                                                                                                                                                                                               │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
>>> what is the capital of Canda?                                                                                                                                                                                                                                 [S][default]
╭──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── granite-7b-lab-Q4_K_M.gguf ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ The capital of Canada is Ottawa. It's one of the country's three national capitals, along with Yellowknife in the Northwest Territories and Iqaluit in Nunavut. Established as the capital in 1867, Ottawa is located in the eastern province of Ontario and serves as an  │
│ important political center for Canada. If you have any more questions about Canada or other countries, feel free to ask!                                                                                                                                                   │
╰──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── elapsed 1.585 seconds ─╯
>>> /q
```

Nice! Now that we have InstructLab set up correctly, and we're talking to the model, now lets fine tune it with Lab 4!
