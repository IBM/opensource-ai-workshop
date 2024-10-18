# Tuning the Granite Model

Now that you've set up InstructLab, lets get tuning the Granite Model.

## Sanity check

Take a moment to verify that you are not running `ilab model chat` or `ilab model serve` anywhere,
it will clash with the following commands with training and tuning the model.

The Granite family of foundation models span an increasing variety of modalities, including language, code, time series, and science (e.g., materials) - with much more to come. We're building them with transparency and with focus on fulfilling rigorous enterprise requirements that are emerging for AI. If you'd like to learn more about the models themselves and how we build them, check out Granite Models.

The mission of the Granite Community organization is to work collaboratively across industries and geographies to leverage Granite to solve problems and bring value across use cases, from code generation and modernization, to forecasting and predictive maintenance, to materials discovery.

## Prepare to train your model

1) Pull down an example `qna.yaml`. But wait what is a `qna.yaml`? There's a few things you should know before going any further.

Knowledge is based more on answering questions that involve facts, data, or references.

Knowledge in the taxonomy tree consists of a few more elements than skills:

- Each knowledge node in the tree has a `qna.yaml`, similar to the format of the `qna.yaml` for skills.
- ⭐ Knowledge submissions require you to create a Git repository, can be with GitHub, that contains the markdown files of your knowledge contributions. These contributions in your repository must use the markdown (.md) format.
- The `qna.yaml` includes parameters that contain information from your repository.

!!! tip
    Guidelines for Knowledge contributions

    - Submit the most up-to-date version of the document
    - All submissions must be text, images will be ignored
    - Do not use tables in your markdown freeform contribution

Format of the `qna.yaml`:

- `version`: The cache version of the qna.yaml file, this is the format of the file used for SDG. The value must be the number 3.
- `created_by`: Your GitHub username.
- `domain`: Specify the category of the knowledge.
- `seed_examples`: A collection of key/value entries.
  - `context`: A chunk of information from the knowledge document. Each `qna.yaml` needs five `context` blocks and has a maximum word count of 500 words.
  - `questions_and_answers`: The parameter that holds your questions and answers
    - `question`: Specify a question for the model. Each `qna.yaml` file needs at least three question and answer pairs per `context` chunk with a maximum word count of 250 words.
    - `answer`: Specify the desired answer from the model. Each `qna.yaml` file needs at least three question and answer pairs per `context` chunk with a maximum word count of 250 words.
- `document_outline`: Describe an overview of the document your submitting.
- `document`: The source of your knowledge contribution.
  - `repo`: The URL to your repository that holds your knowledge markdown files.
  - `commit`: The SHA of the commit in your repository with your knowledge markdown files.
  - `patterns`: A list of glob patterns specifying the markdown files in your repository. Any glob pattern that starts with `*`, such as `*.md`, must be quoted due to YAML rules. For example, `"*.md"`.

### Knowledge: YAML examples

```yaml
created_by: cdoern
version: 3
domain: animals
seed_examples:
  - context: |
      Moo Deng (bouncy pig) is a pygmy hippopotamus, living in Khao Kheow Open Zoo in Si Racha, Chonburi, Thailand. She gained notability at two months of age in September 2024 as a popular Internet meme after images of her went viral online.
      Moo Deng was born on 10 July 2024. Her name was chosen through a public poll, with over 20,000 people voting for "Moo Deng", translating to "bouncy pork" or "bouncy pig".
    questions_and_answers:
      - question: |
          Who is Moo Deng?
        answer:
          Moo Deng is a pygmy hippopotamus living in Khao Kheow Open Zoo, Thailand, who became an Internet sensation in 2024.
      - question: |
          When was Moo Deng born?
        answer:
          Moo Deng was born on 10 July 2024.
      - question: |
          How was Moo Deng's name chosen?
        answer:
          Moo Deng's name was chosen through a public poll with over 20,000 votes, translating to "bouncy pork" or "bouncy pig".
  - context: |
      Moo Deng's father is Tony, and her mother is Jonah. She has two full siblings: Nadet, born in 2010, male, and Moo Tun, born on 27 October 2019, male.

      She also has three half-siblings through her mother's relationship with Rambo: Ko, Kanya, and Phalo. Additionally, Moo Deng has one half-sibling through her father's relationship with Kanya: Moo Wan, female.
    questions_and_answers:
      - question: |
          Who are Moo Deng's parents?
        answer:
          Moo Deng's father is Tony, and her mother is Jonah.
      - question: |
          How many full siblings does Moo Deng have?
        answer:
          Moo Deng has two full siblings, Nadet and Moo Tun.
      - question: |
          How many half-siblings does Moo Deng have?
        answer:
          Moo Deng has four half-siblings, Ko, Kanya, Phalo (from her mother's side) and Moo Wan (from her father's side).
  - context: |
      Khao Kheow Open Zoo posted images of its pygmy hippopotamuses on its official Facebook page, and Moo Deng quickly became a favorite among fans. She is noted for being more playful and energetic than other hippopotamuses.

      The zoo responded to her popularity by selling merchandise featuring designs based on Moo Deng. Other companies joined in by producing merchandise, including Vetmon Cafe, which created a realistic cake shaped like Moo Deng. Additionally, Sephora posted a makeup tutorial inspired by her, and she became the subject of many fan artworks.
    questions_and_answers:
      - question: |
          How did Moo Deng become popular?
        answer:
          Moo Deng became popular after Khao Kheow Open Zoo posted images of her on Facebook, where she quickly became a fan favorite.
      - question: |
          What merchandise was created based on Moo Deng?
        answer:
          The zoo sold merchandise featuring designs based on Moo Deng, and Vetmon Cafe created a realistic cake shaped like her.
      - question: |
          Which company posted a makeup tutorial inspired by Moo Deng?
        answer:
          Sephora posted a makeup tutorial inspired by Moo Deng.
  - context: |
      Due to Moo Deng's viral online popularity, the number of daily visitors to the zoo doubled in early September 2024. Some visitors harassed the baby hippo by splashing water at her or throwing objects to wake her up. In response, the zoo installed security cameras around her enclosure, and the zoo's director threatened legal action against visitors who harassed her.
      The zoo also implemented a five-minute time limit for visitors to accommodate the high volume of guests.
    questions_and_answers:
      - question: |
          How did Moo Deng's popularity affect the number of visitors at Khao Kheow Open Zoo?
        answer:
          The number of daily visitors to Khao Kheow Open Zoo doubled in early September 2024 due to Moo Deng's popularity.
      - question: |
          What actions did the zoo take to protect Moo Deng from harassment?
        answer:
          The zoo installed security cameras around Moo Deng's enclosure and threatened legal action against visitors who harassed her.
      - question: |
          How long can visitors spend with Moo Deng at the zoo?
        answer:
          The zoo implemented a five-minute time limit for visitors to see Moo Deng due to the high volume of guests.
  - context: |
      In September 2024, zoo director Narongwit Chodchoi announced that the zoo had begun the process of copyrighting and trademarking "Moo Deng the hippo" to raise funds for the zoo. The zoo also plans to launch a continuous livestream to allow fans to watch Moo Deng live over the Internet.
    questions_and_answers:
      - question: |
          What did the zoo do to protect Moo Deng's brand?
        answer:
          The zoo began the process of copyrighting and trademarking "Moo Deng the hippo" in September 2024.
      - question: |
          How does the zoo plan to keep fans engaged with Moo Deng online?
        answer:
          The zoo plans to launch a continuous livestream for fans to watch Moo Deng live over the Internet.
      - question: |
          Why is the zoo copyrighting Moo Deng's name?
        answer:
          The zoo is copyrighting and trademarking "Moo Deng the hippo" to raise funds for its operations.
  - context: |
      On September 28, Moo Deng was the subject of a Saturday Night Live sketch. She was parodied by Bowen Yang on Weekend Update, where the character was used to satirize American pop-artist Chappell Roan's commentary on fame and political endorsements. Yang later extended his support to Roan.
    questions_and_answers:
      - question: |
          How was Moo Deng featured on Saturday Night Live?
        answer:
          Moo Deng was parodied by Bowen Yang on Weekend Update on September 28, 2024.
      - question: |
          What was Moo Deng's parody on SNL used to satirize?
        answer:
          Moo Deng's parody on SNL was used to satirize American pop-artist Chappell Roan's commentary on fame and political endorsements.
      - question: |
          Who portrayed Moo Deng on Saturday Night Live?
        answer:
          Bowen Yang portrayed Moo Deng on Saturday Night Live.
document_outline: Verbatim information about Moo Deng, covering her rise to internet fame, her background, online popularity, merchandise, and how the zoo responded to her viral fame.
document:
  repo: https://github.com/cdoern/knowledge
  commit: 142a62438f227e4bcadd8aac55ef4a9fa625ce0f
  patterns:
    - pop_culture/moodeng.md
```

*Example `attribution.txt` file*

```text
Title of work: Moo Deng
Link to work: https://en.wikipedia.org/wiki/Moo_Deng
Revision: https://en.wikipedia.org/w/index.php?title=Moo_Deng&oldid=1250784534
License of the work: CC-BY-SA-4.0
Creator names: Wikipedia Authors
```

### Knowledge: Markdown file example

```markdown
## Moo Deng

Moo Deng (bouncy pig) is a pygmy hippopotamus, living in Khao Kheow Open Zoo in Si Racha, Chonburi, Thailand. She gained notability at two months of age in September 2024 as a popular Internet meme after images of her went viral online.

## Background

Moo Deng was born on 10 July 2024. Her name was chosen through a public poll, with over 20,000 people voting for "Moo Deng", translating to "bouncy pork" or "bouncy pig".

## Parents and siblings

Moo Deng's father is Tony, and her mother is Jonah.

Moo Deng has two full siblings:

▪ Nadet, born 2010, age 1314, male

## Moo Deng

Species: Pygmy hippopotamus

Sex: Female

Born: 10 July 2024

Residence:  Khao Kheow Open Zoo

Named after: Thai for "bouncy pig"

Moo Deng has two full siblings

▪ Nadet, born 2010, age 13–14, male

▪ Moo Tun, born 27 October 2019, age 4, male

She has three half-siblings through her mother's relationship with Rambo:

▪ Ko

▪ Kanya

▪ Phalo

She also has one half-sibling through her father's relationship with Kanya:

▪ Moo Wan, female

## Online popularity

Khao Kheow Open Zoo posted images of its pygmy hippopotamuses on its official Facebook page, and Moo Deng quickly became a favorite among fans. Moo Deng is noted to be more playful and energetic than other hippopotamuses. In response to her popularity, the zoo announced that it would sell clothing and other merchandise featuring designs based on Moo Deng. Other companies have produced merchandise based on Moo Deng, including a cake shop, Vetmon Cafe, which created a realistic cake shaped like her. Additionally, Sephora posted a makeup tutorial inspired by her. Moo Deng has become the subject of many pieces of fan art.

Thai-language news coverage of Moo Deng in September 2024

Due to Moo Deng's viral online popularity, the number of daily visitors to the zoo doubled in early September 2024. Some visitors have harassed the baby by splashing her with water. or throwing objects at her to wake her up. As a result, the Khao Kheow Open Zoo installed security cameras around her enclosure and the zoo's director threatened legal action against visitors who harassed her. The misbehavior by some visitors has been widely condemned online. The zoo also implemented a fiveminute time limit for visitors in order to accommodate the high volume.

In September 2024, zoo director Narongwit Chodchoi announced that the zoo had begun the process of copyrighting and trademarking "Moo Deng the hippo" to raise funds for the zoo.The zoo also plans to launch a continuous livestream to allow fans to watch Moo Deng live over the Internet.

On September 28, Moo Deng was the subject of a Saturday Night Live sketch. She was parodied by Bowen Yang on Weekend Update, and the character was used to satirize American pop-artist Chappell Roan's commentary on fame and political endorsements. Yang later extended his support to Roan.

## See also

▪ Pesto, another baby zoo animal that gained online popularity in 2024
```

## Putting the `qna.yaml` in the correct place

We need to put the `qna.yaml` like above to the correct place so we can actual do the training. The following commands pulls a copy of it down and puts it in your local `taxonomy` tree.

```bash
cd ~/.local/share/instructlab/taxonomy
mkdir -p knowledge/science/animals/hippos/
cd knowledge/science/animals/hippos/
wget https://raw.githubusercontent.com/instructlab/taxonomy/7ff90c1b7dd7760df130fc21cef46c6a8208048c/knowledge/science/animals/hippos/qna.yaml
cd -
```

!!! note
    If `wget` is not found, please run `brew install wget` that should get it on your laptop.


## Generating synthetic data

After you've built a good knowledge submission like above, the `qna.yaml`, the `attribution.txt` and
finally the hosted `.md` file, you need to tell the teacher model to build questions around
your seeded ones. Lets do that now.

1) If you haven't yet, you'll need to pull down the default teacher model, this is done with this command:

```bash
ilab model download
```

2) Next we need to generate the data, this is done with the following command:

```bash
ilab data generate
```

This can take some time, take note of the time in the right hand corner, this is building 1000 questions off of your initial 15.
This takes the granite model, leverages the tokenized version of it, and runs the SDG from the `generate` command against it.

3) After this is complete, now we'll need to train the actual model. If this isn't a Mac M3, this will take **at least an hour**, so
hopefully you can take a lunch break or something while this is running.

```bash
ilab model train --pipeline simple
```

4) When this is completed, you'll need to test this model, which is the following command:

```bash
lab model test --model-dir ~/.local/share/instructlab/instructlab-granite-7b-lab --adapter-file ~/.local/share/instructlab/checkpoints/instructlab-granite-7b-lab-mlx-q/adapters-100.npz --data-dir ~/.local/share/instructlab/datasets
```

5) Now to run the command on the Mac M3, or Apple hardware you'll need to convert it to a `gguf`, that is this next command.


```bash
ilab model convert --adapter-file ~/.local/share/instructlab/checkpoints/instructlab-granite-7b-lab-mlx-q/adapters-100.npz --model-dir ~/.local/share/instructlab/checkpoints/instructlab-granite-7b-lab-mlx-q
```

6) Finally run the new model with `ilab model serve`.

```bash
ilab model serve --model-path instructlab-granite-7b-lab-trained/instructlab-granite-7b-lab-Q4_K_M.gguf
```

Success! You should notice a difference in the knowledge from what you've trained. If you haven't or something isn't working as expected please understand
that the way [quantization](https://huggingface.co/docs/optimum/en/concept_guides/quantization#) happens to run on your laptop sometimes causes the model to
not know what you trained it. We have some evidence that 1 out of 5 models trained retains your submissions when running on your local laptop. Don't fret
though your submission is great for the upstream model, and extremely valuable to the project.

When the full run from the upstream happens, the PR you submit with the new (or corrected) knowledge will be "baked in" better then the quantization
method you use here, which will give much higher percentage of retrieval.

<img src="https://count.asgharlabs.io/count?p=/lab4_opensource_ai_page>
