---
title: Configuring AnythingLLM
description: Set up AnythingLLM to start using an LLM locally
logo: images/ibm-blue-background.png
---

## Setup

Let's start by configuring [AnythingLLM installed](../pre-work/README.md#installing-anythingllm) and `ollama` to talk to one another. The following screenshots will be from a Mac, but this should be similar on Windows and Linux.

First, if you haven't already, download the Granite 3.1 model. Make sure that `ollama` is running in the background (you may have to run `ollama serve` in its own terminal depending on how you installed it) and in another terminal run the following command:

```bash
ollama pull granite4:micro
```
!!! note
    If the granite4:micro model isn't available yet, you can choose granite3.3:2b or granite3.3:8b

!!! note
    The download may take a few minutes depending on your internet connection. In the meantime, you can check out information about model we're using [here](https://ollama.com/library/granite3.3). Check out how many languages it supports and take note of its capabilities. It'll help you decide what tasks you might want to use it for in the future.

Open the AnythingLLM desktop application and either click on the *Get Started* button or open up settings (the 🔧 button). For now, we are going to configure the global settings for `ollama` but you can always change it in the future.

![wrench icon](../images/anythingllm_wrench_icon.png)

Click on the *LLM* section, and select **Ollama** as the LLM Provider. Select the `granite4:micro` model you downloaded. You'd be able to see all the models you have access to through `ollama` here.

![llm configuration](../images/anythingllm_llm_config.png)

Click the *Back to workspaces* button (where the 🔧 was) and head back to the homepage.

Click *New Workspace*.

![new workspace](../images/anythingllm_new_workspace.png)

Give it a name (e.g. the event you're attending today):

![naming new workspace](../images/anythingllm_naming_workspace.png)

## Testing the Connection

Now, let's test our connection AnythingLLM! I like asking the question, "Who is Batman?" as a sanity check. Every LLM should know who Batman is.

The first response may take a minute to process. This is because `ollama` is spinning up to serve the model. Subsequent responses should be much faster.

![who is batman](../images/anythingllm_who_is_batman.png)

You may notice that your answer is slighty different then the screen shot above. This is expected and nothing to worry about!

## Conclusion

**Congratulations!** Now you have AnythingLLM running and it's configured to work with `granite4:micro` and `ollama`. Move on to [Lab 2](https://ibm.github.io/opensource-ai-workshop/lab-2/) and have a chat with your model!

<script data-goatcounter="https://tracker.asgharlabs.io/count"
        async src="//tracker.asgharlabs.io/count.js"></script>
