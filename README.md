### General

This repo summarizes our work in the **Math Teacher Challenge** as part of the DataHack 2018 hackaton in Jerusalem.
The main track of the DataHack involved [4 challenges](https://www.datahack.org.il/#challenges), where the Math Teacher Challenge was owned by Microsoft.

Microsoft's "The Math Teacher” Challenge was a NLP Challenge for building a personal math teacher using natural language for understanding and reasoning capacities around Math. The goal was to build a NLP model that can perform automatic problem solving (especially Math Word Problems) written in natural language.

Example problems:

<img width="619" alt="example_questions" src="https://user-images.githubusercontent.com/35026597/46653023-8cfd6e80-cbad-11e8-891f-3c016fb2f0f7.png">

Our main challenge was that non of our team members had any experience with seq2seq models, an in general very limited knowledge in Deep Learning, which required us to learn these fundementals in a very short time.

Additional challenges we faced:
* Broad range of problems
* Text and numbers representaitio
* Equation representation (the output sequence was the set of equations)
* Small datasets (374 questions in the train set)
* Very short time (36 hours)


### Approach

**Focus on specific questions**
Since there many types of questions, we believed that if we focus on one set of questions, that roughly have the same characteristics, that may help us get right prediction, however for only this type of question (high recall / loe precision). The question we focused on were:
* Simple – vocabulary, context, explicit
* Linear – Allows simple representation (embedding) for the equations
* Explicit – No complex tokens (e.g. arithmetical progression)

Eventually we got left with 28 questions only, based on the following funnel:


