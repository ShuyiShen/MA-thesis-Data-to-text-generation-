# Data to text generation for job advertisement with joint entity and relation extraction based approach
MA Text Mining Thesis  at VU University Amsterdam

## AUTHORS
------------------
S.Shen (Shen)

## PROJECT STRUCTURE
-------------------
This project tackles the NLP task of data to text generation for job advertisement with joint entity and relation extraction based approaches. 
Data-to-text generation (D2T) refers to the task of generating textual output from non-linguistic input such as databases of records. Joint entity and relation extraction is a sub-task in Natural Language Processing (NLP) that refers to detecting and categorizing the information from unstructured text through knowledge graphs where we can navigate across different nodes to discover hidden relationships between entity pairs.

In our task, the non-linguistic source data are domain-specific knowledge bases, a triplet consisting of an entity relation
tuple. We approach joint entity and relation extraction techniques to retrieve good triples as our source data.

## Research Questions
-------------------
- How does model performance relate to the annotation quality during the iterative
annotation process?
- How much data do we need to train a data to text generator?
- Could T5 generate accurate and fluent content with multiple triples based on selfcurated
tags?

### Repository structure
-------------------
**What you will find in this project:**

- the copy module PRGC classifier
- data to text generator (T5)
- Regex for preprocessing 
- Statistics folder that measures the number of overlapping entities 
- Inter annotator agreement
- human evaluation 
- annotation guideline

#### ./the copy module of PRGC classifier - potential relation and global correspondence framework:

The architecture of this model is developed by Zheng et al. (2021). Based on the author’s ideas, the emergence
of the model aims to resolve the inherent limitations of previous works: redundancy
of relation prediction, poor generalization of span-based extraction, and inefficiency.
Three subtasks were proposed to solve these concerns: relation judgment,entity extraction,
and subject-object alignment.

#### ./the data to text generator using T5 module (NLG):

T5 stands for Text-to-Text Transfer Transformer. It is an encoderdecoder
model that has recently received the most incredible attention from researchers
since its release.Inspired by the T5 model’s ability to support data to text generation by fine-tuning on smaller and
specialized datasets, we decided to use this model as our baseline. Additionally, to our
knowledge, recent neural approaches have not been applied to data-to-text generation
(job qualification) in the job domain. These factors also push us to explore this model.

#### ./Regular Expression for preprocessing (REGEX):

Regular Expressions, also known as “regex” or “regexp” are patterns used to match
character combinations in strings. Following the framework of our annotation guideline, 
we explicitly designed different regexe commands that match the sentences containing 
one of the entities of the job field. 

#### ./Inter annotator agreement :

One significant concern of our annotation project is consistency. Phrases in the Job
corpus can be discontinuous. For example, in the sentence “a three year+ experience
in the financial industry,” spans of annotated instances might differ in Version A and
Version B. The annotator might label “3 year+ experience” as an “experience” token,
omitting a determiner in Version A and revising it in Version B. Thus, testing for
identical job entities requires checking more than just the phrase boundaries. 

With this in mind, based on the previous approach, the revised measures of recall and precision
was adopted and yielded a slightly different interpretation of our task since comparing
version A and B does not involve a “correct” annotation.

#### ./Human Evaluation

As several past studies Novikova et al. (2017)Reiter (2018)Chaganty et al. (2018) have
found that automatic evaluation is not a reliable way to evaluate data-to-text generation
models, we also perform the human evaluation on generated texts from our systems.

Text generation could be potentially misleading while still receiving similar scores on
automated metrics. Identifying what can be improved, therefore, requires an eyeball
error analysis. With BLEU, for instance, if a word is placed incorrectly within
a sentence, it can change its entire meaning. However, BLEU does not consider the
gravity of errors.

#### ./Statistic:

For our classification experiments, we are provided with a training, development and
test dataset. The data are self-curated Job corpus that contain 6 categories of entities
and 5 types of relations. In this folder, we measure the distribution of average numbers 
of sentences, tokens, triples, and classes for entities and relations across train, 
validation, and test dataset in Job corpus. 

# Data Structure

The data used for this project is covered by privacy policy of the client that provided it.\
Therefore, it was not possible to include it in this repository.\
The dataset provides the following information: the “text” property describing the sentence being annotated, the “span”.\
property representing the entities highlighted at both character and the token level.\
The “start” and “end” offset indicate the position in the annotated text at the character.\
level. In contrast, the “token start” and “token end” offset indicates the position.\
at the token level. The “label” refers to the entity we selected. Lastly, the ‘head’ and,\
‘child’ refer to the entity pair that forms a relation label. They represent the start and,\
end-entity tokens in the annotated span.\

The details regarding this dataset can be found in "*Chapter 4 & 5 : Annotation Study & statistics*" of the thesis.

For illustration purposes, an example file, showing the structure of the datasets used for training, validation, and testing, is included to `job` folder.\
The name of the file is `raw_data.jsonl` and can serve as a means for easier comprehension of the code.

### Expereimental Result
-------------------
The name of the file of predicted text derived from triplets is `t5_pred_final.txt`, included to `NLG/result` folder. 
The details regarding this dataset can be found in "*Chapter 6 & 7 : Classification & Generation*" of the thesis.

## References
-------------------
### joint entity and relation extraction 
The code used for the fine-tuning step was adopted and modified for this task from the work of [Hengyi Zheng, Rui Wen, Xi Chen et al. ACL 2021].\
Source code: https://github.com/hy-struggle/PRGC

### data to text generation - T5 
Our T5 models were built using PyTorch and followed Mathew Alexander’s idea. He did the original work, so all the credit goes to
him. Source code: https://towardsdatascience.com/data-to-text-generation-with-t5-building-a-simple-yet-advanced-nlg-model-b5cce5a6df45
