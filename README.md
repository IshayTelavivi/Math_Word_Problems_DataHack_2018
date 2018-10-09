### General

This repo summarizes our work in the **Math Teacher Challenge** as part of the DataHack 2018 hackaton in Jerusalem.
The main track of the DataHack involved [4 challenges](https://www.datahack.org.il/#challenges), where the Math Teacher Challenge was owned by Microsoft.

Microsoft's "The Math Teacher” Challenge was a NLP Challenge for building a personal math teacher using natural language for understanding and reasoning capacities around Math. The goal was to build a NLP model that can perform automatic problem solving (especially Math Word Problems) written in natural language. [Here are the guidelines](https://github.com/DataHackIL/DataChallenges/blob/master/2018/Microsoft_challenge_datahack_2018.pdf) provided by Microsoft.

Example problems:

<img width="619" alt="example_questions" src="https://user-images.githubusercontent.com/35026597/46653023-8cfd6e80-cbad-11e8-891f-3c016fb2f0f7.png">

Our main challenge was that non of our team members had any experience with seq2seq models, and in general very limited knowledge in Deep Learning, which required us to learn these fundementals in a very short time.

Additional challenges we faced:
* Broad range of math problem types
* Text and numbers representaition
* Equation representation (the output sequence was the set of equations)
* Small datasets (374 problems in the train set)
* Very short time (36 hours)


### Approach

**Focus on specific questions**

Since there were many types of questions, we believed that if we focus on one set of questions, that roughly have the same characteristics, that may help us get correct predictions, however for only this type of questions (high recall / low precision). The questions we focused on were:
* Simple – vocabulary, context, explicit
* Linear – Allows simple representation (embedding) for the equations
* Explicit – No complex tokens (e.g. arithmetical progression)

Eventually we got left with 28 questions only, based on the following funnel:

![image](https://user-images.githubusercontent.com/35026597/46660518-d9ea4080-cbbf-11e8-9675-fca3c23cb778.png)


**Data Enrichment**

Since we focused on similar type of problems/equations, we realized that if there is an exact correspondence between the numbers in the text and those in the equations, then we can generate more problems with the exact same structure. Actually we could generate any number of questions we wanted. We multiplied the data by x1000, so eventually the model ran with roughly 30,000 questions.

Of course the numbers were generated randomly, to get similar but not identical ones.
 
 
 
**Equation Representation**

We chose to represent our equations by their linear parmaneters as a vectorized representation (as mentioned we had only linear problems). We believed that it will be easiler for the network to learn this kind of representation. 
For example:

![image](https://user-images.githubusercontent.com/35026597/46659216-2a13d380-cbbd-11e8-99eb-81884fb57ccf.png)



### Result

We managed to predict correctly 17 problems (out of 1507 in the test set). Although this is a low accuracy, the fact that we narrowed the problems to a specific type, and that it was our first seq2seq model, we considerקג the outcome as success.




### Additional Thoughts

Because we had limited time, the following ideas did not come into action, but would have if we had more time.

1. Extracting the numbers from the problems/equations, replacing them with tokens, and letting the model train on the "naked" version. Then bring these number back to the output sequence
2. Use attention as part of the neural network


