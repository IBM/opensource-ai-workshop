---
title: Applying What You Learned
description: 
logo: images/ibm-blue-background.png
---

Complete the following exercises using your local LLM.

- **Be curious!** What if you ask the same question but in a different way, does the response significantly change?
- **Be creative!** Do you want the response to be organized in a numbered or bulleted list instead of sentences?
- **Be specific!** Aim for perfection. Use descriptive language, examples, and parameters to perfect your output.

!!! note
    Discovered something cool or unexpected? Don’t keep it to yourself, raise your hand or let the TA know!
    Whether it’s a creative use of the tool or a surprising result, we’d love to hear it.
    Past students have used granite to run D&D one-shots and co-write stories, your idea might inspire the whole room!

## 1. Generate a Creative Story

**Ask the model to generate three creative sentences about camels.**

Each sentence must:

- Be written from a different point of view (e.g., a child, a scientist, or the camel itself),
- Include at least one vivid sensory detail (sight, sound, touch, etc.),
- And build a mini narrative across the three (the second sentence should follow from the first, the third from the second).

Format the sentences like a list.

## 2. Extract Summary Topics

**Prompt a model to extract a short, bulleted summary from a meeting transcript.**  
The goal is to turn raw dialogue into clear, actionable notes — just like you'd want after a real meeting. 

You can use the following meeting transcripts.

```
00:00 [joe] The goal today is to finalize the budget proposal.
00:15 [sarah] I think we should allocate 30% to marketing.
00:30 [joe] That's a good starting point.
00:50 [dave] I agree, but we should also consider allocating 20% to research and development.
01:15 [sarah] That's a good point. What about the remaining 50%?
01:40 [dave] We could use it for operational costs.
02:05 [joe] I think that's a solid plan. Are we all in agreement?
02:30 [sarah] Yes, I am.
02:50 [dave] Me too.
03:15 [joe] Done!
```

```
00:00 [jess] Let's plan the company picnic!
00:10 [ali] How about we have it at the beach?
00:21 [sarah] Good idea.
00:35 [ali] Can we have a BBQ and games too?
00:50 [jess] Maybe we could also have a potluck?
01:05 [sarah] That way everyone can bring something to share.
01:20 [ali] We could also set up a few outdoor activities like volleyball and badminton.
01:40 [jess] I like this plan. Let's make it happen!
```

Here's an example summary:

```
Transcript:
00:00 [jane] What's the status on Project A?
00:08 [bob] Oh, before we dive in—did everyone have a good weekend?
00:12 [jane] Haha, yeah, it went by too fast. Okay, back to it—Project A?
00:15 [bob] We're still waiting on the Johnson report for Project B, which is kind of blocking progress.
00:30 [jane] Got it. Can we get an update on the timeline for Project C?
00:37 [bob] Hmm, let me check... one sec...
00:45 [bob] Okay, I’ll send out an email with the latest information right after this.
01:02 [jane] Sounds good. Also, let's schedule a meeting with the marketing team to discuss the campaign for Project D.
01:10 [bob] Marketing… got it. Give me a second to pull up the calendar.
01:18 [bob] I’ll set it up for next Thursday.
01:25 [jane] Perfect. Thanks.
01:30 [bob] No problem.
01:35 [jane] Sounds good. Let’s move forward with the plan.

Summary:
- Project A is pending the Johnson report for Project B
- Project C update will be sent via email
- Project D meeting scheduled for next Thursday
```

<details>
<summary> Show hint </summary>
Try prompting like this:

"Summarize the following meeting transcript as a short bulleted list of key decisions and discussion points."

Then paste in the transcript and see what the model gives you. Ask yourself:

- Are the bullets focused and concise?
- Did the model include only important information?
- Did it ignore filler or small talk?
</details>

## 3. Compare Two Passages

**Prompt the model to analyze and explain what two short passages have in common.**

Try to generate output that doesn't just focus on shared objects, the model is probably smarter than that! Your prompt should encourage the model to reflect on **themes, tone, or emotional meaning**, not just surface-level details.

```
The bird sat on the windowsill, its bright feathers a splash of color
against the drab gray wall. It cocked its head to one side, as if listening
to the distant chirping of its fellow birds. The morning sunlight
streamed through the window, casting a warm glow over the bird's
plumage.

The bird took to the skies, its wings beating rapidly as it soared above
the treetops. The wind ruffled its feathers, but it flew with ease, its eyes
scanning the landscape below for signs of food or danger. The sun was
high overhead, casting a warm glow over the bird's feathers as it flew
over the fields and forests.
```

```
It's windy as the sun sets over the horizon, casting a warm glow on the 
landscape.

A gentle breeze rustles the leaves of the trees as the sun begins to set 
and colour the landscape.
```

```
"The dog wagged its tail excitedly as it waited for its owner to come
home. It had been a long day, and the dog was eager to play and receive
some attention. As soon as it heard the door open, the dog ran to greet
its owner, tail wagging furiously."

"The dog lay on its bed, panting softly as it watched its owner pack
up the car. It had been a long day, and the dog was tired but content.
As soon as its owner gave it a pat and a treat, the dog settled in for a
well-deserved nap."
```

```
"The old woman sat on the beach, watching the sun set over the ocean. He
thought about his life, and the memories he had made with his loved ones.
As the stars began to twinkle in the sky, he felt a sense of peace wash over
him, knowing that he had lived a full and happy life."

"The old woman sat on the mountain, watching the sun rise over the
valley. She thought about her life, and the lessons she had learned from her
experiences. As the mist cleared from the valley, she felt a sense of
contentment, knowing that she had lived a life of purpose and meaning."
```

## 4. Build a Cover Letter

**Ask the model to help write a short, two-paragraph cover letter based on a resume.**

Use a resume to prompt the model to generate a **two-paragraph cover letter** that explains:

1. Who you are and what your expertise is.
2. Why a hiring manager should consider you for a new role.

A sample resume is provided below, but you could even use your own if you have it saved locally! *You could even ask the model to generate a short resume for you to use.*

```
Name: Jordan Rivera
Current Job: Marketing Specialist
Experience: 5 years
Core Skills: content strategy, SEO optimization, team leadership, data analytics
Past Roles:
- Social Media Manager at BrightSpark (2 years)
- Content Writer at BuzzTone Agency (1 year)
Education: 
- B.A. in Communications
```

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

## 5. Dungeons & Dragons Role-Play

If you're familiar with the role-playing game Dungeons & Dragons, this excercise is for you! Write a prompt that you would give to an AI to generate a one-shot D&D adventure.

**Write a prompt that you would give to an AI to generate a one-shot D&D adventure**

Focus on providing enough detail to create a cohesive story for a one-session gameplay experience. 
Think about the environment, the objectives, challenges, and the final boss encounter—all while keeping it concise and exciting for the players.

<details>
<summary> Show example prompt </summary>
```
Generate a self-contained dungeon adventure for a party of 4 adventurers,
set in a [specific environment like a forgotten temple or an abandoned mine],
with a clear objective, unique challenges, and a memorable boss encounter,
all designed to be completed in a single session of gameplay
```

The best part of this prompt is that you can take the output and extend or shorten the portions it starts with, and tailor the story to your adventurers' needs!
</details>
