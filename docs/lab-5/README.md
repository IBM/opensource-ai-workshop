---
title: Building a Local AI Assistant
description: Build a Granite coding assistant
logo: images/ibm-blue-background.png
---

Do you use LLMs in an enterprise-setting? There are usually three main barriers to adopting its use in an enterprise setting:

- **Data Privacy:** Corporate privacy regulations that prohibit sending internal code or data to third party services.
- **Generated Material Licensing:** Many models, even those with permissive usage licenses, don't disclose their training data and may produce output that is derived from material with licensing restrictions.
- **Cost:** Many tools are paid solutions that require investment. For larger organizations, this would often include paid support and maintenance contracts which can be extremely costly and slow to

In this lab, we'll use a collection of open-source components to run a feature-rich developer code assistant in Visual Studio Code. Previously, we used `granite3.1-dense`, for general use cases like summarization, question-answering, and classification. Now, we'll try IBM's [Granite Code](https://github.com/ibm-granite/granite-code-models), which are geared towards code generation tasks.

This lab is a rendition of this [blogpost](https://developer.ibm.com/tutorials/awb-local-ai-copilot-ibm-granite-code-ollama-continue/).

!!! note
    The following labs assume some programming experience/knowledge. If you don't have any, don't fret! Raise your hand and ask a TA for help! They'll be more than happy to.

## Download the Model

[Granite Code](https://github.com/ibm-granite/granite-code-models) was produced by IBM Research, with the goal of building an LLM that has only seen code which used enterprise-friendly licenses. According to section 2 of the , the IBM Granite Code models meticulously curated their training data for licenses, and to make sure that all text did not contain any hate, abuse, or profanity. You can read more about how they were built in its [paper](https://arxiv.org/pdf/2405.04324).

Many open LLMs available today license the model itself for derivative work, but because they bring in large amounts of training data without discriminating by license, most companies can't use the output of those models since it potentially presents intellectual property concerns.

Granite Code comes in a wide range of sizes to fit your workstation's available resources. Generally, the bigger the model, the better the results, with a tradeoff: model responses will be slower, and it will take up more resources on your machine. In this lab, we'll try the 8b option for code generation. You could also use the `20b` version, if the wifi connection speed allows for it.

Open up a terminal, and run the following command:

```bash
ollama pull granite-code:8b
```

## Set up Continue in VS Code

Assuming you've already [installed `continue`](/docs/pre-work/README.md#installing-continue), you'll need to configure it.

Open the extension in the sidebar and find the Local Assistant's gear icon.

To open this config.yaml, you need to open the assistant's dropdown in the top-right portion of the chat input. On that dropdown beside the "Local Assistant" option, select the cog icon. It will open the local config.yaml.

![](/docs/images/continue.png)

*The config.json can usually be found in `~/.continue/config.yaml`*

You can add a section for each model you want to use in this file. For this lab, we'll register the Granite Code model we downloaded earlier. Replace the line `"models": []` with the following:

```json
  "models": [
    {
      "title": "Granite Code 8b",
      "provider": "ollama",
      "model": "granite-code:8b"
    }
  ],
```

For inline code suggestions, it's generally recommended that you use smaller models since tab completion runs constantly as you type. This will reduce load on the machine. In the section that starts with `"tabAutocompleteModel"`, replace the whole section with the following:

```json
  "tabAutocompleteModel": {
    "title": "Granite Code 8b",
    "provider": "ollama",
    "model": "granite-code:8b"
  },
```

## Sanity Check

Now that you have everything configured in VSCode, let's make sure that it works. Ensure that `ollama` is running in the background either as a status bar item or in the terminal using `ollama serve`.

Open the Continue exension and test your local assistant.

```text
What language is popular for backend development?
```

Additionally, if you open a file for editing you should see possible tab completions to the right of your cursor (it may take a few seconds to show up).

## Conclusion

With your AI coding assistant set up, move on to [Lab 6](/docs/lab-6/README.md) and actually use it!
