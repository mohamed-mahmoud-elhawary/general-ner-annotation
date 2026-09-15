# Title

   * General NER Annotation Project
   * Name: Mohamed Mahmoud Abdelhamid (Mohamed El-Hawary)
   * Date: 14-09-2026
   * Dataset: Few-NERD

# Project Objective

I made this training project to measure my skill in  NER annotation, QA, Errors analysis and create a guideline from zero. This project is consider as application course which I finished [Data Annotation](Check out this course I found on the Elevify platform: https://www.elevify.com/en-us/courses/engineering-construction-and-technology/technology/data-annotation-course-e776c) by elevify.

This project involved a Named Entity Recognition (NER) annotation task using the Few-NERD dataset. I annotated 150 sentences, divided into three rounds of 50 sentences each. After each round, I compared my annotations against the "gold standard" samples and analyzed the errors and their types. Following the first two rounds, I developed a set of guidelines based on the observed errors and insights; I then finalized these guidelines and applied them in the third round to measure their impact on performance.
The project aimed to evaluate the quality of my annotation work and my ability to annotate entities without an initial manual, while simultaneously creating a guideline document to improve annotation accuracy. It also sought to enhance the detection of edge cases and improve conflict resolution efficiency without delving into sub-categories.

In this project, I annotated approximately 150 sentences based on the dataset's core specifications. Since no ready-made guideline manual was available, I had to draft my own rules to standardize the annotation process. This was achieved through an iterative approach involving three separate batches, followed by a final comparison against the dataset's gold standard samples.
# Dataset & Task

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

Note: The dataset has fine-grained labels, but they were not included as data.
# Methodology

## 1. Annotation in Round 1 & 2

I annotated two rounds with the same steps to know where i miss while data and how much improvement without guideline.  

```

annotation
↓
gold comparison
↓
error analysis

```

## 2. Annotation in Round 3

After round 2 and made a guideline according to my analysis and errors for round 1&2 and freeze it to measure its efficiency. 


```

check the guideline
↓
 annotation + back to guideline when we need
↓
gold comparison
↓
error analysis
↓
 update guideline

```
## 3. Review and Comparison

After annotation all 150 Sentences in 3 rounds we check and analysis the error and defining edge cases and out the final results regarding to improvement rate, errors types and its percentage and insufficiency of guideline. 
# Results

You can find the below results summarily: 
## Results by Round

| Round   | Total Objects | Correct | Wrong | Missed | Accuracy | Total Edge Cases |
| ------- | ------------: | ------: | ----: | -----: | -------: | ---------------: |
| Round 1 |           142 |      89 |    43 |     10 |      62% |               11 |
| Round 2 |            98 |      63 |    16 |     19 |      64% |                8 |
| Round 3 |           134 |     100 |    31 |      3 |      75% |               11 |
## Training vs Testing Samples

| Samples          | Round   | Objects | Correct | Wrong | Missed | Accuracy % | Wrong Rate | Missed Rate |
| ---------------- | ------- | ------: | ------: | ----: | -----: | ---------: | ---------: | ----------: |
| Training samples | 1 and 2 |     240 |     152 |    59 |     29 |        63% |        25% |         12% |
| Testing samples  | 3       |     134 |     100 |    31 |      3 |        75% |        23% |          2% |

## Errors types

| Errors                     | Round 1 | Round 2 | Round 3 |
| -------------------------- | ------: | ------: | ------: |
| Missed entities            |      10 |       9 |       4 |
| Incorrect entity type      |       3 |       4 |       1 |
| Incorrect span selection   |      18 |       6 |      11 |
| Context misunderstanding   |       1 |       6 |       2 |
| Ambiguous entity inclusion |       3 |       5 |       8 |
| Ambiguous class boundaries |      18 |       6 |       5 |
## Edge Cases: resolved vs. Not resolved

| Resolved | Not resolved | Total |
| -------- | ------------ | ----- |
| 9        | 21           | 30    |
# Error Analysis

After analysis the performance and results we found the following:
- Accuracy increases from 63% in training simples to 75% in testing simple. that's may refer the guideline had a direct positive impact.
- Missed Rate decreases from 12% in training simples to 2% in testing simple. that's may refer to the increase the focusing and identify all the entities within the sentences without overlooking any of them.
- Wrong Rate decreases from 25% in training simples to 23% in testing simple, that's not big different so we need more analysis about errors type. 
- In Errors types analysis, we found that `Incorrect span selection` is the most persistent error, in round one was 18 then round two was 6 then round three was 18. the reason may refer to inaccuracy rule (span selection) in guideline and need more specific. 
- error `Ambiguous class boundaries` decrease from round form 18 to 5 to 6, This's mean that after round one we understand the annotated more clearly
- error `Ambiguous entity inclusion` increased from Round three to 8. This mean that the manual needs to clarify when an entity should be included and when it should be excluded in edge cases.
# Some of Error Analysis and Edge Cases

| Edge Case                      | Sentence | Annotation   | Gold Standard | Reason for Discrepancy                                                                                                                                                           |
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
  
We notice that some cases are interesting and need more deeply to understand behaviors original annotators.

For example, In sentence 114 `Nurhaci`  is annotated as person while the context it mention as organization. label person is correct in case the rule is rather the exact meaning of the word ignoring the context but that's not near correctly as General NER dataset. This is not mean that annotators make a mistake necessarily, the gold dataset is based on branched labels which created with main labels so that if we investigate it may we reach to his understanding. May examples like `mobile telephone` make us lean towards this understanding. 

All edge cases can be found in edge_cases.md file.
# Guidelines Development
   
As the general guidelines are not found, I try to annotate as per my understand to task without guideline in round 1&2 and to get a knowledge to created as per my misunderstanding points. We can consider that round 1 and 2 are training simples while round 3 is testing simple.

## Most of rules in Guidelines v1.0

- Nature of named entities: generic nouns (common nouns) are not to be annotated. 
- Determining the scope of the annotation: If a proper noun cannot be understood without the word preceding it, that word is included in the annotation (e.g., "Grill Room," where "grill" is not understood without "room"). 
- Human Error: like failure to grasp the sentence context, rushing through data annotation, overlooking names that require annotation, or forgetting annotation conventions over time and relying instead on personal impressions.
### Some of Possibility Edge Cases 

`Organization vs. Building`

When a building is annotated in a way that makes it a distinct entity (a proper noun in its own right), it is annotated as a "building."
If it is annotated as a specific collective group, it is annotated as an "organization."
Example:
high school = building
high school of California = organization

`Building vs. location`
Some structures are considered sites or famous areas rather than specific buildings—such as parks—because the emphasis is not on their construction materials.

All details about Guidelines can be found in Guidelines v1.0.md file.
# Key Findings

 - The guidelines improved performance in some points and need to be updated to others.
 - Error analysis revealed that some errors were recurring rather than random.
 - Context is crucial for category selection.
 - Some generic mentions appeared as entities.
 - Some gold decisions were difficult to replicate using fixed rules.
# Limitations

* The used sample size is small (all rounds = 150 sentences)
* There is no second annotator.
* There are no comprehensive, official, detailed guidelines available.
* Some cases could not be adjudicated.
* Evaluation is based solely on the gold dataset.
# Conclusion

Finally,  I learnt a lot in this project and makes me understand data annotation and know many negative point which need to developed. The project prove that accuracy has been increase according to using a guideline and understand workflow as well.

Also, The first guideline i created succeeded in vastly improving recall (reducing omissions) and generally enhancing precision, but it did not solve the span selection problem.

Next step should be measure my skills in other dataset with other conditions to develop annotation as widely space. and developed guideline with enough understanding for branched labels.
