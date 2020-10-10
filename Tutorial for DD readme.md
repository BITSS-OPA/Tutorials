## Tutorial for Writing a readme.md for Dynamic Documents
#### Aleksandra (Teng) Ma
#### 10/7/2020

This tutorial serves as the instruction of writing a readme file to assist OPA readers to understand and reproduce the Dynamic Document for any OPA projects we may do in the future.

The readme for the dynamic document consists of three parts: Background, Setup, and Body of Analysis. We'll go through each section one by one in this tutorial.

#### Background of your project:
This is where we list reports, summaries, and research papers that can help our readers understand the topic of our OPA.

#### Setup for Reproducing

We are assuming that our reader has no prior experience in R or RShiny. So here we will introduce a couple of things here:

* Setup of R and RStudio including: 1) where to install them 2) how to knit the file to render the final dynamic report 3) the syntax of each Rmd component such as the YAML script and R code chunk    
* Types of code chunk we will have in this dynamic document, as well as how they are formatted. Take the Deworming OPA as an example, we have narrative code chunks and analytic code chunks. Narrative code chunks render summary tables, whereas analytic code chunks define functions for later calculations.  
* We refer to each code chunk by its name, so remember to introduce where the code chunk name is located above.

By practice, we will have three code chunks in the setup section: setup, notes, and sources. All we need to do is explain on a high level what each code chunk does without going into details about what each line does. The same goes for the rest of the code chunks in the dynmaic document.

#### Body of Analysis:

Here we follow the flow of Dynamic Document. It's convenient to have the knitted file open along with the .Rmd file so that it's easier to read. Sometimes it's easier to jot down notes of what specific function or variable does so that you don't forget or lose track of it later on.

##### Variable Definition

Most OPA projects have the same template for defining different variables, so we could just have **an overarching explanation** of what the template does to construct them at the very beginning to avoid repetition. If the OPA project presents more than one research approach, make sure to explain concisely if or how these approaches differ from each other.  

##### Deriving Main Results & Other Analysis

This is where most of the analysis happens. For big analytic code chunks, we can explain them by chunk and refer to them with their chunk names.

Make sure to include the things below:
1. Introduce which approach it takes to get the reproducible results.
2. Introduce the recyclable functions (ones that we will call multiple times in our dynamic document) and what it does.
3. If the code uses an algorithm or process that the Dynamic Document didn't describe, have a brief introduction of what this algorithm is(Monte Carlo for Deworming DD).
4. Explain each step of how we apply the algorithm in our code chunk in plain text.
5. Inform your readers of your final analysis result and its statistical or economic significance.

We should also include how our dynamic document links with shiny app.

#### Appendix

Use this space to list 1) abbreviations that you think your users might not know 2) a brief description of significant functions that are called multiple times throughout the Dynamic Document 3) other information that is crucial but scattered throughout the Dynamic Document. 
