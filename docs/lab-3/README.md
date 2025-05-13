---
title: Prompt Engineering Overview
description: A general overview of Prompt Engineering
logo: images/ibm-blue-background.png
---

!!! note
    This lab was informed by [@juliandiscovers](https://www.youtube.com/channel/UCXKuHxwAeZZu_dg_qs8Z-9w) and [@BenzaMaman](https://www.instagram.com/benzamaman/)'s workshops and content and presents a broad overview of what they teach. If you want to dive deeper into Prompt Engineering we recommend checking them out.

## What is Prompt Engineering (PE)?

Prompt engineering is the practice of designing clear, intentional instructions to guide the behavior of an AI model.

It involves crafting prompts—usually in natural language—that help a model identify what task to perform, how to perform it, and if there are considerations in style or format.
This can include specifying tone, structure, context, or even assigning the AI a particular role.
Prompt engineering is essential because the quality and precision of the prompt can significantly influence the quality, relevance, and creativity of the generated output.
As generative models become more powerful, skillful prompting becomes a key tool for unlocking their full potential.

### The Three Key Principles of PE

1. Specificity - The more detailed your criteria, the more focused and relevant the output will be.
2. Step-by-step structuring - Break complex tasks down into smaller parts to guide the model more effectively.
3. Iterative refinement - Adjust your prompt or build on previous responses to achieve the best result.

### What Makes a Good Prompt?

1. Use natural, unambiguous language – Phrase your prompt as if you're explaining the task to a person.
2. Provide guiding context – Share relevant background information, examples, or constraints to clarify your intent.
3. Define format and tone when needed – Specify style, structure, or voice (e.g., bullet points, formal, pirate).
4. Adapt based on responses – Treat the model’s output as feedback and refine accordingly.

### The Prompting Workflow

1. Define the problem or goal → *“I want a fun fact about cats to share with kids.”*
2. Include relevant context and keywords → *“Keep it short, easy to understand, and fun.”*
3. Write the prompt → *“Tell me a fun and simple fact about cats that a 7-year-old would enjoy.”*
4. Test, evaluate, and iterate → If the fact is too complex: *“Make it even simpler and add a playful tone.”*

## Types of Prompts

Open a brand _new_ Workspace in AnythingLLM (or Open-WebUI) called "Learning Prompt Engineering". Read along with the examples below, and be sure to try them out for yourself!

### Zero-shot Prompting

These prompts don't have any previous data, structure, or guidelines provided with the request. Here's an example:

```
I want to explore pasta making recipes. 
Do you have any suggestions for recipes that are unique and challenging?
```

As you can see, this Granite model comes back with some very challenging options:

![pasta challenges](../images/anythingllm_pasta_challenges.png)

Try it for yourself, did you get a different response? Think about how the response could be better.

As a follow-up, I'll ask for the recipe to make the "Homemade Ravioli" option in the response I received:

```
I do like some homemade ravioli. 
What is the spinach, ricotta and cheese recipe you suggest?
```

![homemade ravioli](../images/anythingllm_homemade_ravioli.png)

These simple back-and-forth questions are examples of **zero-shot prompts*.

Come up with your own zero-shot prompt about any subject you want. Then, we'll start to add some complexity to our prompts.

## One-Shot and Multi-Shot Prompting

First, create a new "thread" so the context window resets. You can think of a *context window* as the amount of information a model can "remember".

![new thread](../images/anythingllm_new_thread.png)

In the following examples, we'll add more guidance in our prompt. By providing **one** example or structure, we achieve *one-shot prompting*.

Take the provided prompts, and replace the [words] in brackets with your own choices. Get creative with it!

```
I want you to act as a customer support assistant who is [characteristic]. 
How would you respond to [text] as a representative of our [type] company?
```

My version will be:
```
I want you to act as a customer support assistant who is an expert in shipping logistics. 
How would you respond to client who has had their freight lost as a representative of our company?
```

![lost freight](../images/anythingllm_lost_freight.png)

That's not a satisfactory or interesting response, right? We need to interate on it, and provide more context about the client, like what they may have lost. **Tip: always think about adding more context!**

```
The freight they lost was an industrial refrigerator, from Burbank, California to Kanas City, MO. 
I need you to write out an apology letter, with reference to the shipping order #00234273 
and the help line of 1-800-347-2845, with a discount code of OPPSWEDIDITAGAIN for 15% off 
shipping their next order. Mention that sometimes, the trucks have accidents and need 
to be repaired and we should be able to reach out in a couple weeks.
```

![better lost freight](../images/anythingllm_better_lost_freight.png)

So much better! By providing more context and more insight into what you are expecting in a response, we can improve the quality of our responses greatly.

By providing **multiple** examples, you're achieving *multi-shot prompting*!.

## Applying What You Learned

## Employee Cover Letter Prompt

Do you have your work resume on the laptop you're using? If you do, you can take it and build a summary about your skill set and who you are. If you are really adventurous, you can even try to make the model write you a cover letter! If you don't have your resume available, have the model create one! *Don't forget to start a new thread!*

Here's a prompt to help you get started with a cover letter, you can fill in the [words] again.

<details>
<summary> Show example prompt </summary>
```
The following text is my resume for my career up 
until my most recent job. I am [current job] with
[years of experience] considered a highly skilled 
individual in [core skill set]. I want to build a
two paragraph explanation about why someone should
hire me for a role with both my current skill set 
and previous experience.
```

![](../images/anythingllm_resume.png)

The response I received has room for improvement, but gives me something to work with!
</details>

Try to build and modify this blurb using the principles of prompt engineering you learned until you're happy with the quality of the response you receive. Think outside of the box!

## Summarization Prompt

Summarizing long documents or emails is a very popular use case to leverage your local AI model for.

The author of this workshop is probably older than you, but remember [CliffNotes](https://en.wikipedia.org/wiki/CliffsNotes)? Well, you have your own built-in CliffNotes bot with AI on your laptop now!

<details>
<summary> Show example prompt </summary>
Here's a prompt to help you set up your AI model to put it "head space" this was inspired from [this website](https://narrato.io/blog/get-precise-insights-with-30-chatgpt-prompts-for-summary-generation/):

```
Generate an [X]-word summary of the following document,
highlighting key insights, notable quotes, and the overall
tone of the core point of it.
Be sure to add any specific call to actions or things that
need to be done by a specific date.
```
</details>

## Role-Playing Prompt

If you're familiar with the role-playing game Dungeons & Dragons, this excercise is for you! Write a prompt that you would give to an AI to generate a one-shot D&D adventure. 

Keep it focused, creative, and self-contained—just enough detail to inspire a full session of gameplay.


```
Generate a self-contained dungeon adventure for a party of 4 adventurers,
set in a [specific environment like a forgotten temple or an abandoned mine],
with a clear objective, unique challenges, and a memorable boss encounter,
all designed to be completed in a single session of gameplay
```

The student took inspiration from [this website](https://www.the-enchanted-scribe.com/post/6-steps-one-prompt-using-chatgpt-to-generate-one-shot-d-d-adventures), which goes more in-depth, and can build out a whole game for you if you want.

The best part of this prompt is that you can take the output and extend or shorten
the portions it starts with, and tailor the story to your adventurers' needs!

## Hands-on Exercises

Let's get back to interfacing with your local LLM. You can go back to AnythingLLM or Open-WebUI.

!!! tip
    You could even use `ollama`'s CLI in a terminal by using `ollama run granite3.1-dense`

!!! tip
    Have you figured something neat out? Raise your hand and offer it to the workshop. Only you know what you came up with.
    We've had stories of leveraging `granite` as a DM for a "one shot" dungeon campaign and leveraged it for collaborative
    writing exercises. We are excited to see what you share!