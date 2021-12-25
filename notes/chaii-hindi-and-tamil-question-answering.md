---
tags: [Notebook/kaggle]
title: chaii-hindi-and-tamil-question-answering
created: '2021-09-26T11:01:56.809Z'
modified: '2021-10-17T11:00:22.834Z'
---

# chaii-hindi-and-tamil-question-answering

- [Kaggle link](https://www.kaggle.com/c/chaii-hindi-and-tamil-question-answering)


## Problem:
- NLU
- Question and answering
- `In this competition, your goal is to predict answers to real questions about Wikipedia articles`


## Dataset
- `chaii-1`: a new question answering dataset with question-answer pairs
- The dataset covers Hindi and Tamil

### Details
- `train.csv` - the training set, containing context, questions, and answers. Also includes the start character of the answer for disambiguation.

## Evaluation
The metric in this competition is [the word Jaccard score](https://en.wikipedia.org/wiki/Jaccard_index)

```python
def jaccard(str1, str2): 
    a = set(str1.lower().split()) 
    b = set(str2.lower().split())
    c = a.intersection(b)
    return float(len(c)) / (len(a) + len(b) - len(c))
```
## Input-output

Input: `context` and `question`
Output: `answer start` and `answer text`


# New hypothesis:

- Monitor jaccard data
- Punctuation mask
- Shifted sentence window
Finish in this afternoon
- Debug failed case
- LIME for bert model


