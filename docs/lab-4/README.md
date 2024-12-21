---
title: Prompt Engineering Overview
description: A general overview of Prompt Engineering
logo: images/ibm-blue-background.png
---

# Prompt engineering overview

First off, a lot of this information was taken from some training from
[@juliandiscovers](https://www.youtube.com/channel/UCXKuHxwAeZZu_dg_qs8Z-9w) and [@BenzaMaman](https://www.instagram.com/benzamaman/)
workshops and content. This is just a broad overview of what they teach,
and if you are looking for in depth tutorials, on Prompt Engineering they
are amazing.

## What is Prompt Engineering (PE)?
An [article from IBM](https://www.ibm.com/topics/prompt-engineering).

From [Wikipedia](https://en.wikipedia.org/wiki/Prompt_engineering):
Prompt engineering is the process of structuring an instruction that can be
interpreted and understood by a generative artificial intelligence (AI) model.
A prompt is natural language text describing the task that an AI should perform.
A prompt for a text-to-text language model can be a query such as "what is Fermat's
little theorem?", a command such as "write a poem in the style of Edgar Allan Poe
about leaves falling", or a longer statement including context, instructions,
and conversation history.

Prompt engineering may involve phrasing a query, specifying a style, choice of words
and grammar, providing relevant context or assigning a role to the AI such as "act
as a native French speaker".

When communicating with a text-to-image or a text-to-audio model, a typical prompt is
a description of a desired output such as "a high-quality photo of an astronaut riding
a horse" or "Lo-fi slow BPM electro chill with organic samples". Prompting a text-to-image
model may involve adding, removing, emphasizing, and re-ordering words to achieve a
desired subject, style, layout, lighting, and aesthetic.

## The three key principles of PE?
1. Be specific: The more criteria you give, the more focused the output will be
1. Work in steps: break the task into smaller chunks. This returns better results, just like a human
1. Iterate and improve: Re-work the inputs and have the granite-3.1 model improve its own output.

## What makes a good prompt?
1. Clear and concise language that is direct and unambiguous
1. The information and examples that you provide area your input.
1. A specific task that you are requesting granite-3.1 to complete area your desired output
1. Refinement as needed once you receive your first response area reiteration until receiving the desired output


## The main prompting steps and/or loop
1. Define the problem or goal
1. Use relevant keywords and phrases
1. Write the prompt
1. Test, evaluate, and iterate

You'll notice that it's a lot like programming in general. And that's by design, PE is just an engineering
problem leveraging development processes.

Now that you see this overview, lets actually get into some prompts and helpful prompt templates.

<img src="https://count.asgharlabs.io/count?p=/lab4_opensource_ai_page>
