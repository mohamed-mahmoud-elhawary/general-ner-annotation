# General NER Annotation Project
## 1. Project Overview

This project involved a Named Entity Recognition (NER) annotation task using the Few-NERD dataset. I annotated 150 sentences, divided into three rounds of 50 sentences each. After each round, I compared my annotations against the "gold standard" samples and analyzed the errors and their types. Following the first two rounds, I developed a set of guidelines based on the observed errors and insights; I then finalized these guidelines and applied them in the third round to measure their impact on performance.
The project aimed to evaluate the quality of my annotation work and my ability to annotate entities without an initial manual, while simultaneously creating a guideline document to improve annotation accuracy. It also sought to enhance the detection of edge cases and improve conflict resolution efficiency without delving into sub-categories.

In this project, I annotated approximately 150 sentences based on the dataset's core specifications. Since no ready-made guideline manual was available, I had to draft my own rules to standardize the annotation process. This was achieved through an iterative approach involving three separate batches, followed by a final comparison against the dataset's gold standard samples.
## 2. Dataset
Dataset: Few-NERD
Source: DFKI-SLT/few-nerd
Task: Named Entity Recognition
Number of labels used: 8 coarse-grained labels

Labels:
- person
- location
- organization
- building
- event
- product
- art
- other

Total annotated sentences in this project: 150
Rounds: 3
Sentences per round: 50
## 3. Annotation Workflow
```

Round 1
↓
Annotate 50 sentences
↓
Compare with gold annotations
↓
Calculate accuracy
↓
Analyze errors and edge cases

```

```

Round 2
↓
Annotate another 50 sentences
↓
Compare with gold annotations
↓
Analyze recurring errors and edge cases
↓
Create Annotation Guidelines v1
↓
Guideline Freeze
↓
No further changes before evaluation

```

```

Round 3
↓
Annotate 50 new sentences using Guidelines v1
↓
Compare with gold annotations
↓
Measure performance change
↓
Analyze unresolved ambiguities

```

## 4. Annotation Guidelines
After analyzing errors from Rounds 1 and 2, I created a set of annotation guidelines to improve consistency.

The guidelines covered:
- entity inclusion
- entity span selection
- context-dependent labeling
- building vs. organization
- building vs. location
- product vs. art
- person vs. art
- human annotation errors and QA

The guidelines were frozen before Round 3 and were not modified during evaluation.
## 5. Results

## Accuracy overall:

| Round   | Sentences | Total Objects | Guidelines           | Accuracy |
| ------- | --------- | ------------- | -------------------- | -------- |
| Round 1 | 50        | 142           | No                   | ~62%     |
| Round 2 | 50        | 98            | No                   | ~64%     |
| Round 3 | 50        | 134           | Frozen Guidelines v1 | ~74%     |

## Conflicts cases and its management

| Round   | Conflicts Cases | resolved | not resolved (Edge cases) |
| ------- | --------------- | -------- | ------------------------- |
| Round 1 | 11              | 5        | 6                         |
| Round 2 | 8               | 4        | 4                         |
| Round 3 | 11              | 4        | 7                         |

Edge cases is cases which i did not found or understand any reason and point to annotated in gold dataset. I will mention some of them as in point 6.
## Error Analysis:

| Errors                     | Round 1 | Round 2 | Round 3 |
| -------------------------- | ------- | ------- | ------- |
| Missed entities            | 10      | 9       | 4       |
| Incorrect entity type      | 3       | 4       | 1       |
| Incorrect span selection   | 18      | 6       | 11      |
| Context misunderstanding   | 1       | 6       | 2       |
| Ambiguous entity inclusion | 3       | 5       | 8       |
| Ambiguous class boundaries | 18      | 6       | 5       |

## 6. Some of Error Analysis and Edge Cases

| Edge Case                      | Sentence | Description  | Gold Standard | Reason for Discrepancy                                                                                                                                                           |
| :----------------------------- | :------- | :----------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| television program "Emergency" | 21       | art          | none          | Unclassified; it is a television program.                                                                                                                                        |
| Lawrence                       | 22       | person       | none          | Not described, despite being a person's name.                                                                                                                                    |
| Elector of Bavaria             | 47       | none         | person        | This is a title, yet it was described as a person.                                                                                                                               |
| 8th legislative district       | 50       | organization | none          | A legislative district; it should be described as an organization but was not.                                                                                                   |
| Papacy                         | 97       | none         | event         | It is a title, yet it was described as an event.                                                                                                                                 |
| Steak 'n Shake                 | 82       | organization | art           | The phrase refers to an archive center or similar; why was it classified as 'art' instead of 'organization'?                                                                     |
| phosphate                      | 54       | other        | none          | Why wasn't the name classified, while only the chemical symbol was?                                                                                                              |
| Nurhaci                        | 114      | organization | person        | In this context, it is a tribe name but was classified as a person; it is like saying the "Awlad Ali" tribe and treating "Ali" as a person rather than part of the tribe's name. |
| British and Free French        | 120      | none         | organization  | The context implies attacks; are the attacks themselves described as an organization, or does it refer to the armies?                                                            |
| L'affaire Clémenceau           | 112      | art          | none          | This is the title of a novel but was not described at all.                                                                                                                       |

## 7. Key Findings

- Creating explicit annotation guidelines improved overall annotation accuracy.
- Error analysis helped identify recurring annotation patterns.
- Context was important for distinguishing labels such as LOCATION and ORGANIZATION.
- Some generic noun phrases were annotated as entities despite not being proper names.
- Some gold annotations could not be consistently reproduced using the rules inferred from previous examples.
- Fine-grained distinctions in the original dataset may influence some coarse-label decisions.
## 8. Project Structure

```
general-ner-annotation/
├── README.md
├── data/
├── analysis/
├── guidelines/
└── report/
```



general-ner-annotation/
├── README.md
├── data/
├── analysis/
├── guidelines/
└── report/

