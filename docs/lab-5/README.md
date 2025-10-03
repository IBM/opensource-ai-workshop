---
title: Using AnythingLLM for a local RAG
description: Learn how to build a simple local RAG
logo: images/ibm-blue-background.png
---

## Configuration and Sanity Check

Open up AnythingLLM, and you should see something like the following:
![default screen](../images/anythingllm_open_screen.png)

If you see this that means AnythingLLM is installed correctly, and we can continue configuration. If not, please find a workshop TA or
raise your hand we'll be there to help you ASAP.

Next as a sanity check, run the following command to confirm you have the [granite4:micro](https://ollama.com/library/granite4)
model downloaded in `ollama`. This may take a bit, but we should have a way to copy it directly on your laptop.

```bash
ollama pull granite4:micro
```

If you didn't know, the supported languages with `granite4` now include:

- English, German, Spanish, French, Japanese, Portuguese, Arabic, Czech, Italian, Korean, Dutch, and Chinese. However, users may finetune this Granite model for languages beyond these 12 languages.

And the Capabilities also include:

- Thinking
- Summarization
- Text classification
- Text extraction
- Question-answering
- Retrieval Augmented Generation (RAG)
- Code related tasks
- Function-calling tasks
- Multilingual dialog use cases
- Fill-in-the-middle
- Long-context tasks including long document/meeting summarization, long document QA, etc.

Next click on the `wrench` icon, and open up the settings. For now we are going to configure the global settings for `ollama`
but you may want to change it in the future.

![wrench icon](../images/anythingllm_wrench_icon.png)

Click on the "LLM" section, and select **Ollama** as the LLM Provider. Also select the `granite4:micro` model. (You should be able to
see all the models you have access to through `ollama` there.)

![llm configuration](../images/anythingllm_llm_config.png)

Click the "Back to workspaces" button where the wrench was. And Click "New Workspace."

![new workspace](../images/anythingllm_new_workspace.png)

Name it something like "learning llm" or the name of the event we are right now, something so you know it's somewhere you are learning
how to use this LLM.

![naming new workspace](../images/anythingllm_naming_workspace.png)

Now we can test our connections _through_ AnythingLLM! I like the "Who is Batman?" question, as a sanity check on connections and that
it knows _something_.

![who is batman](../images/anythingllm_who_is_batman.png)

Now you may notice that the answer is slighty different then the screen shot above. That's expected and nothing to worry about. If
you have more questions about it raise your hand and one of the helpers would love to talk you about it.

Congratulations! You have AnythingLLM running now, configured to work with `granite4:micro` and `ollama`!

## Creating your own local RAG

Now that you have everything set up, lets build our own RAG. You need a document, of some sort to questions to answer against
it. Lets start with something fun. As of right now, our Granite model doesn't know about the US Federal Budget in 2024, so lets
ask it a question about it to verify.

Create a new workspace, and call it whatever you want:

![new budget workspace](../images/new_budget_workspace.png)

Now you have a new workspace, ask it a question like:

```
What was the US federal budget for 2024?
```

You should come back with something like the following, it may be different, but the gist is there.

![doesnt know the budget](../images/doent_know.png)

Not great right? Well now we need to give it a way to look up this data, luckly, we have a backed up
copy of the budget pdf [here](https://github.com/user-attachments/files/18510560/budget_fy2024.pdf).
Go ahead and save it to your local machine, and be ready to grab it.

!!! note
    Granite 4 has newer data, so since this lab was created, it DOES have the 2024 data.  If you find that's the case, you can try it with the question about 2025 using the 2025 full-year budget using the link below. 

[budget_fy2025.pdf](https://www.whitehouse.gov/wp-content/uploads/2024/03/budget_fy2025.pdf)

Now spin up a **New Workspace**, (yes, please a new workspace, it seems that sometimes AnythingLLM has
issues with adding things, so a clean environment is always easier to teach in) and call it
something else.

![budget workspace](../images/budget_workspace.png)

Click on the "upload a document" to get the pdf added.

Next we need to add it to the workspace.

![adding pdf](../images/adding_pdf.png)

Next click the upload or drag and drop and put the pdf in there, and then the arrow to move it to the
workspace. Click Save and Embed.

You have now added the pdf to the workspace.

Now when the chat comes back up ask the same question, and you should see some new answers!

![success pdf](../images/success.png)

It won't be exactly what we are looking for, but it's enough to now see that the Granite model can
leverage the local RAG and in turn can _look things up_ for you. You'll need some prompt engineering
to get exactly what you want but this is just the start of leveraging the AI!

<script data-goatcounter="https://tracker.asgharlabs.io/count"
        async src="//tracker.asgharlabs.io/count.js"></script>
