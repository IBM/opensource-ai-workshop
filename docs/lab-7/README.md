---
title: Using Mellea to help with Generative Computing
description: Learn how to leverage Mellea for Advanced AI situations
logo: images/ibm-blue-background.png
---

# What is Generative Computing?

A generative program is any computer program that contains calls to an LLM.
As we will see throughout the documentation, LLMs can be incorporated into
software in a wide variety of ways. Some ways of incorporating LLMs into
programs tend to result in robust and performant systems, while others
result in software that is brittle and error-prone.

Generative programs are distinguished from classical programs by their use of
functions that invoke generative models. These generative calls can produce
many different data types — strings, booleans, structured data, code,
images/video, and so on. The model(s) and software underlying generative
calls can be combined and composed in certain situations and in certain
ways (e.g., LoRA adapters as a special case). In addition to invoking
generative calls, generative programs can invoke other functions, written
in languages that do not have an LLM in their base, so that we can, for
example, pass the output of a generative function into a DB retrieval system
and feed the output of that into another generator. Writing generative
programs is difficult because generative programs interleave deterministic
and stochastic operations.

If you would like to read more about this, please don't hesitate to take a
look [here](https://docs.mellea.ai/overview/project-mellea).

# Mellea

[Mellea](https://github.com/generative-computing/mellea) is a library for
writing generative programs. Generative programming replaces flaky agents
and brittle prompts with structured, maintainable, robust, and efficient AI workflows.

## Features

* A standard library of opinionated prompting patterns.
* Sampling strategies for inference-time scaling.
* Clean integration between verifiers and samplers.
   - Batteries-included library of verifiers.
   - Support for efficient checking of specialized requirements using
     activated LoRAs.
   - Train your own verifiers on proprietary classifier data.
* Compatible with many inference services and model families. Control cost
  and quality by easily lifting and shifting workloads between:
       - inference providers
       - model families
       - model sizes
* Easily integrate the power of LLMs into legacy code-bases (mify).
* Sketch applications by writing specifications and letting `mellea` fill in
  the details (generative slots).
* Get started by decomposing your large unwieldy prompts into structured and maintainable mellea problems.

## Let's setup Mellea to work locally

1.  Open up a terminal, and run the following commands:
```bash
python3.11 -m venv venv
source venv/bin/activate
pip install mellea
```

!!! note
    If you see something about the Rust compiler, please confirm you are using python3.11, or python3.12 anything above that has a Rust dependency.

1.  Start python:
```bash
python
```

1.  Run a simple Mellea session:
```python
import mellea

m = mellea.start_session()
print(m.chat("What is the etymology of mellea?").content)
```
You can either add this to a file like `main.py` or run it in the python REPL, if you get output
you are set up to dig deeper with Mellea.

!!! note
    If you see an error message with: "ModuleNotFoundError: No module named 'PIL'" then you will need to install the python package pillow with "pip install pillow"

## Simple email examples

!!! note
    The following work should be done via a text editor, there should be a couple installed on your laptop, if you aren't sure raise your hand and a helper will help you out.

1.  Let's leverage Mellea to do some email generation for us, the first example is a simple example:
```python
import mellea
m = mellea.start_session()

email = m.instruct("Write an email inviting interns to an office party at 3:30pm.")
print(str(email))
```

1.  As you can see, it outputs a standard email with only a couple lines of code, lets expand on this:
```python
import mellea
m = mellea.start_session()

def write_email(m: mellea.MelleaSession, name: str, notes: str) -> str:
    email = m.instruct(
        "Write an email to {{name}} using the notes following: {{notes}}.",
        user_variables={"name": name, "notes": notes},
    )
    return email.value  # str(email) also works.


print(
    write_email(
        m,
        "Olivia",
        "Olivia helped the lab over the last few weeks by organizing intern events, advertising the speaker series, and handling issues with snack delivery.",
    )
)
```
With this more advance example we now have the ability to customize the email to be more directed and
personalized for the recipient. But this is just a more programmatic prompt engineering, lets see where
Mellea really shines.

### Simple email with boundries and requirements

1. The first step with the power of Mellea, is adding requirements to something like this email, take a look at this first
example:
```python
import mellea
m = mellea.start_session()

def write_email_with_requirements(
    m: mellea.MelleaSession, name: str, notes: str
) -> str:
    email = m.instruct(
        "Write an email to {{name}} using the notes following: {{notes}}.",
        requirements=[
            "The email should have a salutation",
            "Use only lower-case letters",
        ],
        user_variables={"name": name, "notes": notes},
    )
    return str(email)


print(
    write_email_with_requirements(
        m,
        name="Olivia",
        notes="Olivia helped the lab over the last few weeks by organizing intern events, advertising the speaker series, and handling issues with snack delivery.",
    )
)
```
As you can see with this output now, you force the Mellea framework to start checking itself to create what you need.
Imagine this possibility, now you can start making sure your LLMs only generate things that you want. Test this theory
by changing from "only lower-case" to "only upper-case" and see that it will follow your instructions.

Pretty neat eh? Lets go even deeper.

Let's create an email with some sampling and have Mellea, find the best option for what we are looking for:
We add two requirements to the instruction which will be added to the model request.
But we don't check yet if these requirements are satisfied, we add a strategy for validating the requirements.

1. This sampling strategy (`RejectionSamplingStrategy()`) checks if all requirements are met and if any requirement fails, the sampling strategy will sample a new email from the LLM.
```python
import mellea
m = mellea.start_session()

from mellea.stdlib.sampling import RejectionSamplingStrategy


def write_email_with_strategy(m: mellea.MelleaSession, name: str, notes: str) -> str:
    email_candidate = m.instruct(
        "Write an email to {{name}} using the notes following: {{notes}}.",
        requirements=[
            "The email should have a salutation",
            "Use only lower-case letters",
        ],
        strategy=RejectionSamplingStrategy(loop_budget=5),
        user_variables={"name": name, "notes": notes},
        return_sampling_results=True,
    )
    if email_candidate.success:
        return str(email_candidate.result)
    else:
        print("Expect sub-par result.")
        return email_candidate.sample_generations[0].value


print(
    write_email_with_strategy(
        m,
        "Olivia",
        "Olivia helped the lab over the last few weeks by organizing intern events, advertising the speaker series, and handling issues with snack delivery.",
    )
)
```
You might notice it fails with the above example, just remove the `"Use only lower-case letters",` line, and
it should pass on the first re-run. This brings up some interesting opportunities, so make sure that the
writing you expect is within the boundaries and it'll keep trying till it gets it right.

## Instruct Validate Repair

1. The first `instruct-validate-repair` pattern is as follows:

```python
import mellea
from mellea.stdlib.requirement import req, check, simple_validate
from mellea.stdlib.sampling import RejectionSamplingStrategy

def write_email(m: mellea.MelleaSession, name: str, notes: str) -> str:
    email_candidate = m.instruct(
        "Write an email to {{name}} using the notes following: {{notes}}.",
        requirements=[
            req("The email should have a salutation"),  # == r1
            req(
                "Use only lower-case letters",
                validation_fn=simple_validate(lambda x: x.lower() == x),
            ),  # == r2
            check("Do not mention purple elephants."),  # == r3
        ],
        strategy=RejectionSamplingStrategy(loop_budget=5),
        user_variables={"name": name, "notes": notes},
        return_sampling_results=True,
    )
    if email_candidate.success:
        return str(email_candidate.result)
    else:
        return email_candidate.sample_generations[0].value


m = mellea.start_session()
print(write_email(m, "Olivia",
                  "Olivia helped the lab over the last few weeks by organizing intern events, advertising the speaker series, and handling issues with snack delivery."))
```

Most of this should look familiar by now, but the `validation_fn` and `check` should be new.

We create 3 requirements:

- First requirement (r1) will be validated by LLM-as-a-judge on the output of the instruction. This is the default behavior.
- Second requirement (r2) uses a function that takes the output of a sampling step and returns a boolean value indicating successful or unsuccessful validation. While the validation_fn parameter requires to run validation on the full session context, Mellea provides a wrapper for simpler validation functions (simple_validate(fn: Callable[[str], bool])) that take the output string and return a boolean as seen in this case.
- Third requirement is a check(). Checks are only used for validation, not for generation. Don't think mention purple elephants.

Run this in your local instance, and you'll see it working, and ideally no purple elephants! :)

Hopefully you felt like you've learned a bunch about AI and engaging with our open source models through this journey. Never hesitate
to give us any feedback, and remember all of this stuff is free, open source, Apache 2 licensed, and designed to work in the
Enterprise ecosystem. Thanks for reading and joining us!
