# Building a local AI co-pilot

## Overview

Success! We're ready to start with the first steps on your AI journey with us today.
With this first lab, we'll be working through the steps in this [blogpost using Granite as a code assistant](https://developer.ibm.com/tutorials/awb-local-ai-copilot-ibm-granite-code-ollama-continue/).

In this tutorial, I will show how to use a collection of open-source components to run a feature-rich developer code assistant in Visual Studio Code while addressing data privacy, licensing, and cost challenges that are common to enterprise users. The setup is powered by local large language models (LLMs) with IBM's open-source LLM family, [Granite Code](https://github.com/ibm-granite/granite-code-models). All components run on a developer's workstation and have business-friendly licensing.

There are three main barriers to adopting these tools in an enterprise setting:

- **Data Privacy:** Many corporations have privacy regulations that prohibit sending internal code or data to third party services.
- **Generated Material Licensing:** Many models, even those with permissive usage licenses, do not disclose their training data and therefore may produce output that is derived from training material with licensing restrictions.
- **Cost:** Many of these tools are paid solutions which require investment by the organization. For larger organizations, this would often include paid support and maintenance contracts which can be extremely costly and slow to negotiate.

## Fetching the Granite Models

Why did we select Granite as the LLM of choice for this exercise?

Granite Code was produced by IBM Research, with the goal of building an LLM that had only seen code which used enterprise-friendly licenses. According to section 2 of the Granite Code paper ("[Granite Code Models: A Family of Open Foundation Models for Code Intelligence][paper]),the IBM Granite Code models meticulously curated their training data for licenses, and to make sure that all text did not contain any hate, abuse, or profanity.

Many open LLMs available today license the model itself for derivative work, but because they bring in large amounts of training data without discriminating by license, most companies can't use the output of those models since it potentially presents intellectual property concerns. Granite 

Granite Code comes in a wide range of sizes to fit your workstation's available resources. Generally, the bigger the model, the better the results, with a tradeoff: model responses will be slower, and it will take up more resources on your machine. I chose the 20b option as my starting point for chat and the 8b option for code generation. Ollama offers a convenient pull feature to download models:

Open up your terminal, and run the following commands:
```bash
ollama pull granite-code:20b
ollama pull granite-code:8b
```

## Set up Continue

Now we need to install [continue.dev](https://continue.dev) so VSCode can "talk" to the ollama instance, and work with the
granite model(s). There are two different ways of getting `continue` installed. If you have your `terminal` already open
you can run:

```bash
code --install-extension continue.continue
```

If not you can use these steps in VSCode:

1. Open the Extensions tab.
2. Search for "continue."
3. Click the Install button.

Next you'll need to configure `continue` which will require you to take the following `json` and open the `config.json`
file via the command palette.

1. Open the command palette (Press Ctrl/Cmd+Shift+P)
2. Select Continue: Open `config.json`.

In `config.json`, add a section for each model you want to use. Here, we're registering the Granite Code 20b model we downloaded earlier. Replace the line that says `"models": []` with the following:

```json
  "models": [
    {
      "title": "Granite Code 20b",
      "provider": "ollama",
      "model": "granite-code:20b"
    }
  ],
```

For inline code suggestions, we're going to use the smaller 8b model since tab completion runs constantly as you type. This will reduce load on the machine. In the section that starts with `"tabAutocompleteModel"`, replace the whole section with the following:

```json
  "tabAutocompleteModel": {
    "title": "Granite Code 8b",
    "provider": "ollama",
    "model": "granite-code:8b"
  },
```

## Sanity Check

Now that you have everything wired together in VSCode, let's make sure that everything works. Go ahead and open
up `continue` on the extension bar:

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/lKHl3FNCegebKYdHuXR-GA/continue-sidebar.png)

And ask it something! Something fun I like is:

```text
What language should I use for backend development?
```

If you open a file for editing, you should also see possible tab completions to the right of your cursor.

It should give you a pretty generic answer, but as you can see, it works, and hopefully will help spur a thought
or two.

Now let's continue on to Lab 2, where we are going to actually try this process in-depth!

[paper]: https://arxiv.org/pdf/2405.04324?utm_source=ibm_developer&utm_content=in_content_link&utm_id=tutorials_awb-local-ai-copilot-ibm-granite-code-ollama-continue

<img src="https://count.asgharlabs.io/count?p=/lab1_opensource_ai_page">

