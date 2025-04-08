<!--

author:   André Dietrich
email:    masub.makhdoom@ovgu.de
date:     19/03/2025
version:  30.0.0
language: en
narrator: UK English Female

repository: https://github.com/LiaScript/docs

logo:     img/logo.png

comment:  This document shall provide an entire compendium and course on the
          development of Open-courSes with [LiaScript](https://LiaScript.github.io).
          As the language and the systems grows, also this document will be updated.
          Feel free to fork or copy it, translations are very welcome...

script:   https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js
          https://felixhao28.github.io/JSCPP/dist/JSCPP.es5.min.js

link:     https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.css

link:     https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css

import:   https://raw.githubusercontent.com/liaTemplates/ABCjs/main/README.md

link:     https://fonts.googleapis.com/css2?family=Noto+Sans+Egyptian+Hieroglyphs
          https://fonts.googleapis.com/css2?family=Noto+Sans+Ogham

font:     Noto Sans Egyptian Hieroglyphs, Noto Sans Ogham
-->

# Prompt Writing Examples for ChatGPT+





# Generative AI Resources

    

● Artificial Intelligence Now: ChatGPT & AI Literacy Toolbox: Images, Writing, &
Prompts

● MasterList of LibGuides on AI


## Prompt Approaches

All approaches are from Ethan Mollick’s work

*  The first is simply adding context to a prompt. There are many ways to do that: give
the AI a persona (you are a marketer), an audience (you are writing for high school
students), an output format (give me a table in a Word document), and more.

*  The second approach is to give the AI a few examples to work from. LLMs work well
when given samples of what you want, whether that is an example of good output
or a grading rubric.

*  The final tip is to use Chain of Thought, which seems to improve most LLM outputs.
While the original meaning of the term is a bit more technical, a simplified version
just asks the AI to go step-by-step through instructions: First, outline the results;
then produce a draft; then revise the draft; finally, produce a polished output.
(Another example) Unlike blindly using magic words, these are techniques and
approaches that can help you craft a better prompt.

###  Prompt Tips
    {{0}}
*  When creating images, it seems like hallucination can increase on follow-up tasks, so
a tip is to start over if hallucination becomes problematic.

*  When trying to transcribe pages of writing, including “will you manually transcribe”
in the prompt is effective.

*  When asking for an output like an Excel file or a PowerPoint slide, explicitly ask for
the output format.

*  When uploading images, JPGs and PNGs are better formats than TIFFs.

*  LLMs are weird, and sometimes, asking ChatGPT+ to create its own prompt from
your first draft prompt gets you closer to our desired outcome. To do this use this
prompt: “Improve this prompt to maximize the creativity and analytical abilities of a
large language model:” [*prompt*]

#### Prompt Format


When writing prompts for ChatGPT+, it is essential to structure your prompts thoughtfully.
Feel free to create prompts of your own and experiment. Below are current best practices
for prompt creation. **The four key components are**


**Role**

* This helps ChatGPT+’s model have background pointers for the kinds of responses it could generate.



**Context**



* This helps the model get closer to your desired outcome because it gives it pointers to what to pay attention to in your document if you are uploading a document or what part of a pasted-in text to pay attention to when adding text.

* There are times when context could limit ChatGPT+’s ability to provide information. The group has found success with providing context and without. Experiment with adding context and not in your prompts.

**Output Specification for ChatGPT+**

* This gets you closer to what you need from ChatGPT. Include a bailout clause, like “‘if you cannot find this information, respond “I do not know.”’
* Note you don’t need to include this clause. ChatGPT sometimes explains why they might be unable to provide that information unprompted. This is something to help with the hallucinations that can exist. There are trade-offs to both approaches.

#### Text-Based Example

You are an expert in teaching. I am trying to find the best ways to teach design school students how to get the most out of our library. Design in this context means architecture, landscape architecture, and urban planning and design. What is the best format for library instruction for design school students?


### Primary Source Document Example

You are an expert in movie posters. Generate the following metadata for the attached poster to be used in a library catalog and format it in an Excel sheet with the column headings listed below. When possible pull information directly from the image. For the last two items on the list, limit text to three sentences.

* Film title
* Film director
* Production Studio
* Film Distributor
* Year of release
* Country(ies) of production
* Cast
* Summary of film
* Alt-text

# Excel Spreadsheet Example

You are an expert in cleaning spreadsheets and data. This is a spreadsheet of records of books. The spreadsheet has a year of publication column for when the book was published. Create a new column in the spreadsheet that will indicate if the book's year of publication column is after 1930. Please add Yes if it was after 1930 and No if it was not after 1930 in the newly created column. If the answer cannot be determined or inferred from the
spreadsheet, please respond, **“I do not know”**. 
It handled this exceptionally well.




## Image Analysis Example

You are an expert in understanding maps. This is a map that is in French of Madagascar from 1753 created by a French explorer. What text do you see in the image? Please answer this accurately. If the answer cannot be determined or inferred from the image,
please respond, **“I do not know”**.

 It could translate the French in the legend to English without me asking. The image I used:

![](https://github.com/61087/Quantitative-Research-/blob/main/Screenshot%2012.png?raw=true)






