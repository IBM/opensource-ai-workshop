---
title: Prompt Engineering Overview
description: A general overview of Prompt Engineering
logo: images/ibm-blue-background.png
---

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

## Hands on portion

Bring up your interface to your local LLM, this can be one of the previous configured systems like
AnythingLLM or Open-WebUI, or even `ollama` on the command line.

This is an example of using the CLI with vanilla `ollama`:

```bash
$ ollama run granite3.1-dense
>>> Send a message (/? for help)
```

You can pretty much write whatever you want to, give it a shot. Treat it like a good friend, be polite,
and guide it to an answer you are looking for.

I really do like starting with `Who is Batman?` then work from there. Maybe see if the LLM knows who's
Batman's top 10 enemies are, and what was the most interesting way Batman saved the day? You have an opportunity
to ask a knowledge repository here on everything Batman related, or any super hero for that matter, take advantage of
it.

If you treat the LLM like the knowledge repository it is, you can get so much useful information out of it, but like
all interpreted knowledge repositories you need can't blindly take it's output. You should always cross reference important things,
and treat it like the "best librarian" you've ever seen. They know a TON of information, know how to
find it, and where to get more, but they aren't the final authority on the topic.

!!! tip
    Have you figured something neat out? Raise your hand and offer it to the workshop. Only you know what you came up with.
    We've had stories of leveraging `granite` as a DM for a "one shot" dungeon campaign and leveraged it for collaborative
    writing exercises. We are excited to see what you share!

If you're curious the one shot `prompt` was this, the student took inspiration from [this website](https://www.the-enchanted-scribe.com/post/6-steps-one-prompt-using-chatgpt-to-generate-one-shot-d-d-adventures):

```
Generate a self-contained dungeon adventure for a party of 4 adventurers,
set in a [specific environment like a forgotten temple or an abandoned mine],
with a clear objective, unique challenges, and a memorable boss encounter,
all designed to be completed in a single session of gameplay
```

Now that you see this overview, lets actually get into some prompts and helpful prompt templates.

## Asking the LLM about Batman

```
$ ollama run granite3.1-dense
>>> Who is Batman?
Batman is a fictional superhero created by artist Bob Kane and writer Bill Finger. He first appeared in Detective Comics #27,
published by DC Comics in 1939. Born as Bruce Wayne, he becomes Batman to fight crime after witnessing the murder of his parents
as a child. Unlike most superheroes, he has no actual superpowers but instead relies on his physical prowess, intellect, and
advanced technology. His symbol is a bat, which instills fear in criminals due to its nocturnal nature. Batman is known for his
strong moral code, not killing his enemies, and his relentless pursuit of justice. He's one of the most iconic and enduring
characters in the world of comics and popular culture.

>>> What was Batman's top 10 enemies?
Batman has faced numerous villains over the years, but here are ten of his most notable adversaries:

1. The Joker - One of Batman's archenemies, The Joker is a criminal mastermind known for his chaotic and psychopathic behavior.
He often uses deadly weapons disguised as everyday objects like flowers or toys.

2. Two-Face (Harvey Dent) - Once Batman's ally and Gotham City district attorney, Harvey Dent was scarred by acid and became a
villain with a coin that decides his actions, representing the duality of good and evil within him.

3. Penguin (Oswald Cobblepot) - A short, stout criminal with an umbrella-based arsenal, Penguin is known for his love of
animals, especially birds, and operates from his hideout in the sewers beneath Gotham City.

4. Catwoman (Selina Kyle) - A skilled thief and Batman's complex love interest, Catwoman wears a cat-themed costume and uses her
agility, charm, and whip to outwit her adversaries.

5. Ra's al Ghul - An immortal villain who leads the League of Assassins, Ra's seeks to cleanse the world with natural disasters
and replace humanity with a more "pure" species. Batman's ally Talia heads the organization.

6. The Riddler (Edward Nygma) - A criminal genius with an obsession for riddles, The Riddler uses complex puzzles to taunt
Batman while committing crimes.

7. Mr. Freeze (Victor Fries) - Once a brilliant cryogenic scientist, Victor Fries became Mr. Freeze after an accident involving
cryogenic technology left him needing a refrigerated suit to survive.

8. Poison Ivy (Dr. Pamela Isley) - A plant-based villainess with control over plants and the ability to manipulate pheromones,
she seeks to destroy humanity and create a new world dominated by flora.

9. Bane - A supervillain known for his physical strength, enhanced by a drug called Venom, Bane once broke Batman's back in a
legendary storyline.

10. Ra's al Ghul's Daughter Talia - As mentioned earlier, Talia is both the daughter of Ra's and an occasional love interest for
Bruce Wayne/Batman. She has played both roles as ally and enemy throughout various Batman stories.

These villains represent a mix of criminal masterminds, twisted psychopaths, and formidable physical threats that challenge
Batman's intellect, strength, and resolve.

>>> What was the most interesting way Batman saved the day?
One of the most intriguing and innovative ways Batman has saved the day is from Frank Miller's seminal graphic novel "The Dark
Knight Returns." In this story, an aging Batman returns to crime-fighting after a self-imposed retirement.

After a series of escalating conflicts with a new mutant gang known as the Mutants, led by Green Arrow's former sidekick, Talia
al Ghul (daughter of Ra's al Ghul), Batman faces off against their leader, a mutated Joker. The Joker has been given superhuman
strength through a risky experiment conducted by his henchmen.

The climax of the storyline takes place in a nuke-laden Bomb Squad truck, driven by the Joker himself and escorted by the
Mutants. With conventional methods proving ineffective against the Joker's newfound power, Batman devises an unconventional
plan:

1. Luring the Joker into a trap at the Gotham Bay.
2. Tying a massive concrete block to his leg and dropping him into the water, hoping the weight would neutralize the mutagenic
serum, returning the Joker's strength to normal levels.
3. Simultaneously triggering an explosion that would capsize the Bomb Squad truck carrying the nuclear bomb, causing it to sink
with the now-weakened Joker still inside.
4. Jumping into the water after the Joker and subduing him just before the truck goes underwater.
5. Finally, using a remote detonator to destroy the truck and the bomb, thus saving Gotham City from a catastrophic explosion.

This daring plan showcases Batman's resourcefulness, unwavering determination, and willingness to take risks for the greater
good - all hallmarks of his character. The innovative approach to saving the day has since become one of the most iconic moments
in Batman's extensive history.
```

