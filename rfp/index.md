# Requests for Projects

Inspired by YC's [*Request for Startups*](https://www.ycombinator.com/rfs/), here are a list of potential problems for students, researchers, engineers, businesses and competitions.

They could be realised as research, datasets, libraries, applications or products.

## Language

### Core components
Models like BERT or GPT-3 rely on legacy libraries for charset detection, language detection and sentence segmentation to turn raw data crawled from the web into rows of training data.  They are imperfect, especially for long-tail languages, and their quirks affect the accuracy of the downstream models.  Ironically they are often rules-based.  Today it makes sense to try a deep learning approach to these foundational problems.

#### Charset detection
Deep-learning-based charset detection / encoding detection
The incumbent is Mozilla's chardet (and ports to Node and Python, like https://pypi.org/project/chardet/).
It is not great.

#### Language detection
Deep-learning-based language detection / language identification
The incumbent is Google Chrome's stats-based cld3 (and ports to Node and Python).
Facebook did this in 2017 with fastText (which had been already proposed in our community) but it is still not great.

#### Sentence segmentation
Deep-learning-based sentence segmentation / sentence splitting
This is key for the self-supervised pre-training of BERT etc.

### Code
There are many interesting problems between natural language and programming language.
- text → .html or .md
- code repo → README.md
- pull request code → pull request title and description
- unit test → function
...



### More
See also:
- [projects built with or for the spaCy parser](https://spacy.io/universe/)


### For Armenian
Note that we generally discourage language-specific work that copies advances in English, and favor language-agnostic approaches.

[*Tools and data for the Armenian language*](/hy/)


---

## Vision

---

## Biomedical

---

## Mapping

---

## Security 

---

## Defence

---

## Finance

---

## Markets
