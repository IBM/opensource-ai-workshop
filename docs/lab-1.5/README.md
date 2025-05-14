---
title: Configuring Open-WebUI
description: Set up Open-WebUI to start using an LLM locally
logo: images/ibm-blue-background.png
---

Let's start by configuring [Open-WebUI](../pre-work/README.md#installing-open-webui) and `ollama` to talk to one another. The following screenshots will be from a Mac, but this should be similar on Windows and Linux.

First, if you haven't already, download the Granite 3.1 model. Make sure that `ollama` is running in the background (you may have to run `ollama serve` in its own terminal depending on how you installed it) and in another terminal run the following command:

```bash
ollama pull granite3.1-dense:8b
```

!!! note
    The download may take a few minutes depending on your internet connection. In the meantime, you can check out information about model we're using [here](https://ollama.com/library/granite3.1-dense). Check out how many languages it supports and take note of its capabilities. It'll help you decide what tasks you might want to use it for in the future.

Open up Open-WebUI (assuming you've run `open-webui serve`):

![default screen](../images/openwebui_open_screen.png)

If you see something similar, Open-WebUI is installed correctly! Continue on, if not, please find a workshop TA or raise your hand for some help.

Click *Getting Started*. Fill out the next screen and click the *Create Admin Account*. This will be your login for your local machine. Remember that this because it will be your Open-WebUI configuration login information if want to dig deeper into it after this workshop.

![user setup screen](../images/openwebui_user_setup_screen.png)

You should see the Open-WebUI main page now, with `granite3.1-dense:latest` right there in
the center!

![main screen](../images/openwebui_main_screen.png)

Test it out! I like asking the question, "Who is Batman?" as a sanity check. Every LLM should know who Batman is.

The first response may take a minute to process. This is because `ollama` is spinning up to serve the model. Subsequent responses should be much faster.

![batman](../images/openwebui_who_is_batman.png)

You may notice that your answer is slighty different then the screen shot above. This is expected and nothing to worry about!

**Congratulations!** Now you have Open-WebUI running and it's configured to work with `granite3.1-dense` and `ollama`. Move on to the next lab and have a chat with your model!
