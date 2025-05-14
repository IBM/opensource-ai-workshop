---
title: Chatting with Your Local AI
description: Get acquainted with your local LLM
logo: images/ibm-blue-background.png
---

It's time for the fun exploration part your Prompt Engineering (PE) journey. In this lab, you're encouraged to spend as much time as you can chatting with the model, especially if you have little experience doing so. Keep some questions in mind: can you make it speak in a different tone? Can it provide a recipe for a cake or a poem about technology? Is it self-aware?

## Chatting with the Model

Open a brand _new_ Workspace in AnythingLLM (or Open-WebUI) called "Learning Prompt Engineering".

You can pretty much write whatever you want to, give it a shot. Treat it like a good friend, be polite,
and guide it to an answer you are looking for.

For some inspiration, I like to start with `Who is Batman?` then work from there. I might want to see if the LLM knows who
Batman's top 10 enemies are, or what was the most creative way Batman saved the day? Some example responses to those questions are below.

!! note
    If you treat the LLM like a knowledge repository, you can get a lot of useful information out of it. But, remember not to
    blindly accept its output. You should always cross-reference important things. Treat it like a confident librarian! They've read
    a lot and they can be very fast at finding books, but they can mix things up too!

## Using the `ollama` CLI

This is an example of of using the CLI with vanilla ollama:

```
$ ollama run granite3.1-dense
>>> Who is Batman?
Batman is a fictional superhero created by artist Bob Kane and writer Bill Finger. He first appeared in Detective Comics #27,
published by DC Comics in 1939. Born as Bruce Wayne, he becomes Batman to fight crime after witnessing the murder of his parents
as a child. Unlike most superheroes, he has no actual superpowers but instead relies on his physical prowess, intellect, and
advanced technology. His symbol is a bat, which instills fear in criminals due to its nocturnal nature. Batman is known for his
strong moral code, not killing his enemies, and his relentless pursuit of justice. He's one of the most iconic and enduring
characters in the world of comics and popular culture.
```

```
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
```

```
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

## Conclusion

Spend as much time as you want asking your LLM about anything about any topic and exploring how you can alter its output to provide you with more interesting or satisfying responses.

When you are acquainted with your model, move on to [Lab 3](https://ibm.github.io/opensource-ai-workshop/lab-3/) to learn about Prompt Engineering.
