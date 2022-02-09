# Data Management
## Introduction
## [Malka Guillot](https://malkaguillot.github.io/)
## HEC Liège | <a href="https://gitlab.uliege.be/mguillot/econ2306-data-management-2021-22/">ECON2306</a>

---


<!-- exportation : decktape --chrome-arg=--disable-web-security 0-overview.html 0-overview.pdf -s 1024x768
--->

<!-- .slide:  id="toc" class: left, inverse -->
# Table of contents
1. [Prologue]()

1. [Data management: why, how?](#dm)

2. [(Big) data](#data)

2. [Managing a project with data](#code)

3. [Tools](#tools_resources)

3. [This class: overview & logistics](#logistics)

1. [Epilogue](hw)

--

## Welcome
<div class="r-stack">
<img src="https://www.dqglobal.com/wp-content/uploads/2017/07/Data-Management.jpg.webp" style="height: 450px;">
 </div>


--

## Introduction: Who are we?


|Teaching assistant| Lecturer|
|:------:|:---:|
| <a href=http://www.hec.ulg.ac.be/fr/faculty-recherche/faculty-and-researchers/profil/383/>Michel Coppee</a>  | <a href=https://malkaguillot.github.io/>Malka Guillot</a> |
|<img data-src="./images/michel-coppee.jpg"  style="height: 160px;" > | <img data-src="./images/malka_small.jpg" style="height: 160px" class="center"> |
|[michel.coppee@uliege.be](michel.coppee@uliege.be)| [mguillot@uliege.be](mguillot@uliege.be) |


<i class="fa fa-location-arrow" aria-hidden="true"></i>
Bât. N1 Economie (bureau 33a) <br>
rue Louvrex 14 <br>
4000 Liège <br>
Belgique


--

<!-- .slide: id=""-->
## Who am I?

  <div class="image-float">
    <p style="position: relative; right: 0px; top: 10;">
        <a href="./images/malka_small.jpg"><img src="./images/malka_small.jpg" height="200px"/></a></p>
        <a href="image2.jpg"><img src="" height="100px"/></a></p>
   <p class="fragment" data-fragment-index="4" style="position:absolute; left:40px; top:40px;">
     </div>
  <div class="content-aside">
   <p class="fragment fade-down" data-fragment-index="1">
    PhD in economics from the Paris School of Economics </p>
   <p class="fragment" data-fragment-index="2">
    Postdoc at ETH </p>
    <p class="fragment" data-fragment-index="3">
     Assistant professor in applied micro economics at HEC Liège </p>   <p class="fragment" data-fragment-index="4">
    Interested in <bcolor>public economics</bcolor> questions:
    <a href="https://cepr.org/active/publications/discussion_papers/dp.php?dpno=15415/">inequality</a> and
    <a href="https://payroll-tax-inequality-app.herokuapp.com/">taxation</a></p>


   <p class="fragment" data-fragment-index="4">
    Using the standard econometric toolbox + natural language processing + machine learning </p>
 </div>

 <a href="https://malkaguillot.github.io/"><i class="fas fa-globe" ></i></a>
 <a href="https://twitter.com/MalkaGuillot/"><i class="fab fa-twitter" ></i></a>
 <a href="https://www.linkedin.com/in/malka-guillot-408b5361/"><i class="fab fa-linkedin" ></i></a>

--

## Wooclap


<div style="position:relative;  text-align: center;" >
<iframe allowfullscreen frameborder="0" height="600px" width="600px" mozallowfullscreen src="https://app.wooclap.com/events/BEPSEL/questions/6202a57e1289bf116f5afc28" height="400px"  width="600px"></iframe>
   <div style="position:absolute;  z-index:500;height:80%;width:100%;"></div>
</div>





--

## Introduction: Who are you ?


<div style="position:relative;  text-align: center;" >
<iframe allowfullscreen frameborder="0" height="600px" width="600px" mozallowfullscreen src="https://app.wooclap.com/events/BEPSEL/questions/6202a5b3a07f0e119f298284" height="400px"  width="600px"></iframe>

--

## What do you expect to learn during the class?


<div style="position:relative;  text-align: center;" >
<iframe allowfullscreen frameborder="0" height="600px" width="600px" mozallowfullscreen src="https://app.wooclap.com/events/HHQNFR/questions/61e9758ca45a831197a500c0" height="400px"  width="600px"></iframe>


---

<!-- .slide: id="dm"  -->
# Data management: why, how?
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## What is data management about?
All processes, tools, and techniques that have to do with **working with data** :
- Data management plan
- Research data archiving
- Metadata :
    - = structured information that describes, explains, locates, and otherwise represents something else [data].

$\rightarrow$ Allows data to be found and interpreted

- *Bottom line*: data should be valid, shared and contextualized within (research) communities

--

## The Data Management Plan (DMP)
Supports Transparency and openness, by indicating:  
  - how data will be made discoverable, accessible, and reusable

Important in the context of open science / governemnts:
- So that **public investments** are transferable

But also in the context of a firm:
- Long-term investments are key for sustainability

**Document that helps you manage the data lifecylce**


Notes:
- **DMP**:  
  - We won't elaborate DMP: that's really not the objective of the class. But it is important to know such things exists, so that we can implement good data management practices
- Lifecycle : useful representation

--

## The data lifecycle

<div class="r-stack"><img src=http://belgium.devoteam.com/wp-content/uploads/sites/19/2021/05/Devoteam_DataLyfecycle2.png style="width: 600px;" ></div>


Notes:
1. CREATION: Data collection: the life cycle of data starts with information gathering. This allows the creation of values (that do not exists yet).
Capturing the data: Acquisition / entry / signal receipt (internet of things)
7. DESTROY: Data cleaning : possible deletion of the data when it is no longer of use

--

## This class: from acquisition of data to data analysis

The class focuses concepts & skills related to the management of data, that are central for the **exploitation** of data.

**Goals**:
- Equip you with the standard datascience toolkit.
- Put it to work on a real-world project.

Notes:
The class focuses on the practical ingredients related to data (acquisition & analysis) rather than on the higher level concepts.

--

## Backbone of the class
1. The <bcolor>skills</bcolor>:
  - Data collection
  - Data cleaning & operation:
    - Pipelines
  - Data vizualisation
2. The <bcolor>tools</bcolor>:
  - python
  - git
3. The <bcolor>concepts</bcolor>:
  - *Project management*: documenting, sharing & managing code
  - *Reproducibility*

*Public targeted*: <bcolor>anyone using data for projects</bcolor>.
For academics or non academics.
- For research
- For firms

Notes:
**Question**: Do you have some ideas of what question you would want to use data for ?

--

## What this course **is**, and *is not*
- **It is**:
  - <bcolor>Applied</bcolor> and oriented towards practice;
  - <bcolor>General</bcolor> overview of different techniques - what they are and how to use them.
  - <bcolor>Data analysis</bcolor> in general, not restricted to a research or a field (economics, political science).
  - In [python]().
- *It is not*:
  - <bcolor>Computer science</bcolor>. We’re not coding up models from scratch.
  - <bcolor>Mathematical statistics</bcolor>. We’re not deriving the functions by hand.


---

<!-- .slide: id="data"  -->

# (Big) data
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

Notes:
More on the type of data I am talking about.

Of course I elude to a relatively new ovni in the world of data : the big data.

But there is a continuum from small to big data, and the size is not the only characteristics.

--

## Revolution in the use of data
- <bcolor> new datasets</bcolor> : administrative microdata, digitization of text archives, social media
- <bcolor> new methods</bcolor> : causal inference, natural language processing, machine learning

$\Rightarrow$ New avenues  in:
- research
- policy analysis
- business (costumer services)

[New possibilities: exciting!]() <!-- .element: class="fragment" -->

Notes:
We are seeing a revolution in research / policy analysis / business sector

I have my own field of specialization, but I expect that you come with your own intresest in economics / finance / management

$\rightarrow$ invest the tools learnt during the class to invent new visualization important for your field

--

## Examples of business applications
- Decision making:
  - What judges can be replaced by robots?
  - Using algorithms to help diagnose cancer / propose the most effective treatment

- Growth hacking:
  - Identify markets where the investments have the highest returns
- Forecasting:
  - Predict sales

--

## What is (big) data?

<div class="r-stack"><img data-src="./images/big-data-illustration.jpeg" style="width: 400px;" ></div>

--

## Expert Survey (UC Berkeley, 2014)

<div class="r-stack"><img data-src="./images/bigdata-worldcould.png" style="width: 600px;" ></div>

Image by Jennifer Dutcher, [source]{https://datascience.berkeley.edu/what-is-big-data}

--

## What is (big) data?

- **Variety** of types/formats of data
  - Structured
  - Unstructured
- **Volume** of data
- **Velocity**: Speed of data flow/stream
- Unusual sources
  - Ready made vs. costummades

$\rightarrow$ Use programming and statistics to extract value


--

## Big data in the Social sciences

- From web applications and digitization of economic and political processes
- <bcolor> Volume </bcolor>: can be big, but usually smaller than in natural sciences
- <bcolor> Variety </bcolor> and <bcolor> variability</bcolor>: often important and challenging
  - Various resources
  - Data generation from 'the real world'
- But usually no streaming applications (<bcolor>velocity</bcolor> not that much of an issue)

--

## New tools and methods

- <bcolor>Data collection</bcolor> API, Webscraping
- <bcolor>Analysis</bcolor> text analysis, machine learning
  - Data can be tall (many observations) or **wide/fat** (many regressors)
  $\Rightarrow$ Machine learning helps to extract the relevant information

- <bcolor>Visualization</bcolor> maps, social networks, web applications

--

## Big data ecosystem

<div class="r-stack"><img data-src="./images/2020-Data-and-AI-Landscape-Preview-1.png" style="width: 800px;" ></div>

Source: ‘Big Data Landscape (2020)’ from  http://mattturck.com, [high definition image](http://mattturck.com/wp-content/uploads/2020/09/2020-Data-and-AI-Landscape-Matt-Turck-at-FirstMark-v1.pdf)


---

<!-- .slide: id="code"  -->
# Managing a project with data
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## The importance of good coding practices

<div class="r-stack"><img src=https://www.explainxkcd.com/wiki/images/6/68/wanna_see_the_code.png style="width: 800px;" ></div>

Source: [xkcd 2138](https://xkcd.com/2138/)

Notes:
If the code is readable, it becomes a **dead body** => it is not usable anymore, it becomes a problem

--

## Readability of the code

The <bcolor>Pep 8</bcolor> convention: [Style guide for python code](https://www.python.org/dev/peps/pep-0008/)

$\rightarrow$ makes it easier (possible) to understand a code of someone else (= you + 2 day!)

- **Naming**
  - Variables: underscores & small letters `snake_case`
  - Constants: underscores & capital letters
  - Classes `CapitalizedCase`
- **Code layout**
  - Blank lines
  - Maximum line length & line breaking
- **Comments**
  - Should be useful (explain code) but not obvious
  - Not on o code line
  - Documentation Strings (Using docsstrings)  -> mainly for functions


(A nice [reference](shttps://realpython.com/python-pep8))

Notes:
The right amount of comments: you can understand the code, but there is not too much information. Beware you have to modify the comments when you modify the code...

--

## Reproducibility principle

The results of the project should be *reproducible* by someone else in the future:
  - this is a basic scientific principle... but too often forgotten

<bcolor>WANTED</bcolor>:
- maintaining a single master file of the data
- [version control]() of the code
- [Readme]() of the project
- document the code (« comments ») & the data (« metadata »)
- controlled coding environment

[Next lecture]()

<bcolor>$\rightarrow$ The course project satisfy by the reproducibility principle</bcolor>

---

<!-- .slide: id="tools_resources" -->
# Tools
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## Your programming background

<div style="position:relative;  text-align: center;" >
<iframe allowfullscreen frameborder="0" height="600px" width="600px" mozallowfullscreen src="https://app.wooclap.com/events/BEPSEL/questions/6202a8c6dd619011842d6615" height="400px"  width="600px"></iframe>


--


## Why Python?

<div class="r-stack"><img data-src="./images/python-search.png" style="height: 500px;" ></div>

--

## Why Python?

- General-purpose language
  - One of the core languages of scientific computing
- Elegant syntax
- Many useful libraries:
  - Data manipulation: [Pandas](https://pandas.pydata.org/)
  - Machine learning: [scikit-learn](http://scikit-learn.org/)
  - Statistics: [statsmodels](http://statsmodels.sourceforge.net/)
  - Natural Language Procession [nltk]()
- Also path dependency: the language I know the best


--

## Using Python

| <a href=https://www.anaconda.com/products/individual>Anaconda</a>| <a href=https://jupyter.org/>Jupyter notebook</a> | Spyder</a> |
|:------:|:---:|:-----:|
|<img data-src="./images/anaconda-logo.png"  style="height: 80px;" > | <img data-src="./images/jupyter-logo2.png" style="height: 80px" class="center"> | <img data-src="./images/spyder-logo.png" alt="" style="height: 80px">|
|a convenient all-in-one install |for homerwork|for longer code|

<bcolor> You are welcome to use R instead.</bcolor>


--

##  <i class="fa fa-arrow-right" aria-hidden="true"></i> Anaconda

<img data-src="./images/anaconda-navigator.png" style="width: 1800px;"  >

Spyder & Jupyter notebook are two development environments from the Anaconda set up.

Notes:
See downlowding instruction and small video


--

## Main python packages

| Task | Package |
|:------:|:---:|
| Webscraping | beautiful soup |
| Data management  | <img src=https://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/Pandas_logo.svg/600px-Pandas_logo.svg.png style="width: 80px;background-color: #e5e0d8"> |
| Visualisation | <img src=https://steemitimages.com/1280x0/https://res.cloudinary.com/hpiynhbhq/image/upload/v1521146556/frskntefqfbebukx3l1m.png style="width: 80px"> |
| Web application | <img src=https://rapids.ai/assets/images/Plotly_Dash_logo.png style="width: 80px;background-color: #e5e0d8"> |
| Machine Learning | <img src=https://upload.wikimedia.org/wikipedia/commons/thumb/0/05/Scikit_learn_logo_small.svg/440px-Scikit_learn_logo_small.svg.png style="width: 80px;background-color: #e5e0d8"> |
| Natural language processing | NLTK & <img src=https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/SpaCy_logo.svg/440px-SpaCy_logo.svg.png style="width: 80px;background-color: #e5e0d8"> |


---

<!-- .slide: id="logistics"  -->
# This class: overview & logistics
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## How does the class work? Spirit
Sessions are designed to be [interactive]()

- mix of live *coding* & *exercises*
- we want to get you comfortable using your computing environment to solve problems
  - bring your laptop!
  - we expect you have completed the installation guide and have all software installed.
  - ask questions!

--

## How does the class work? Details

- <!-- .element: class="fragment" -->
  <bcolor> Lectures</bcolor>: 3 hours / week  
  - 2 hour theory
  - 1 hour practice:
    - coding exercises
  - sometimes the frontier between theory and practice will be fuzzy.
- <!-- .element: class="fragment" -->
  <bcolor>Every week</bcolor>
  - Thursdays
    - Theory: 9:00-10:25 (with a 10 minute break)
    - Practice: 10:35-12:00
  - Where? N1a 220 (2/20) [Liège centre - Louvrex]
  - Dates: 10.02.; 17.02.; 24.02.; 03.03.; 10.03.; 17.03.; 24.03.; 31.04.; 28.04.; 05.05.; 12.05.; 19.05.


--

## Online Course Materials
- [Syllabus](https://docs.google.com/document/d/1eviJuOoWUjoonxS1LvQJi1kMbmkNUulJtZ31542w100)
- <!-- .element: class="fragment" data-fragment-index="2" -->
 [lola]([Moodle](https://moodle-app2.let.ethz.ch/course/view.php?id=14461) ):
  - Course announcement and forum
  - Giving back homerwork
-   <!-- .element: class="fragment" -->
  [Github folder](https://github.com/MalkIPP/big_data_policy_2020) or [Github page](https://malkipp.github.io/big_data_policy_2021/)
  - <!-- .element: class="fragment" -->
      <bcolor>Slides</bcolor>: in html, also available in PDF
      - relying on [RevealJS](https://revealjs.com/)
  -   <!-- .element: class="fragment" -->
      <bcolor>Coding sessions</bcolor>: in [Jupyter Notebook](https://jupyter.org/)
      - You can use [mybinder](https://mybinder.org/) in the beginning

--

## [Evaluation Policy]

- <bcolor>Problem sets</bcolor>:
  - should be given back as [jupyter notebooks](https://jupyter.org/) in PDF format on [lola]().
  - $3 \textrm{h w} * 5%$ <bcolor> =15%</bcolor>
-  **Participation in class & presentations** <bcolor>= 5% bonus</bcolor>:
- <bcolor>Course project = 85%</bcolor>

The problem sets are simple exercises designed to help students to “get their hands in the data & code”.

--

## [Course project] Objectives

- The <bcolor>basics</bcolor>:

  - End-to-end data project using Python  
    - From collection to vizualisation

  - Group project (2 people; 3 of odd no. of students)

- Use what you learn in this course to <bcolor>solve a non-trivial real-world question/problem</bcolor> using a graphical analysis

  - Code must be in split into meaningful sub-files

  - Solution must be submitted using GitHub

  - Web application, that should be deployed online

--

## [Course project] Web application deployed online???

$\rightarrow$ Some examples in various sector:

- Finance:  
  - The [Yield Curve](https://www.nytimes.com/interactive/2015/03/19/upshot/3d-yield-curve-economic-growth.html?mtrref=dash.gallery&assetType=PAYWALL)
- Health
  - [Opioid epidemic in the US](https://dash.gallery/dash-opioid-epidemic/)    
- Transportation:
	- [Uber rides](https://dash.gallery/dash-uber-rides-demo/)
- [Energy consumption](https://dash.gallery/dash-peaky-finders/)
- https://xkcd-data.herokuapp.com/  
- [Research project](https://payroll-tax-inequality-app.herokuapp.com/)

$\rightarrow$ Be creative, have fun!

Notes:
- <bcolor>Energy consumption</bcolor> if you want to merge DM + TS
- <bcolor>XKCD</bcolor> My favorite one!

--

## What about you?

1 minute to think about a potential field of application.

- Present yourself

- Specify 1 or 2 domain of interest with possible data analysis
  - Can be academic: green finance, agile management
  - or not: sport, important topic

Notes:
I would like to think about what ideas you would want to bring to the class

--

## [Course project] Requirements

- Data:
  - Original data collection

- Analysis :
  - 2 tables and 2 Figures (using different commands)

- Deployment:
  - The main output should be a dash page that you develop on Herokuapp

- Submission format:
  - Invite [@malkaguillot](https://github.com/malkaguillot) and [@MichelCop](https://github.com/MichelCop) to collaborate on your GitHub repository by the due date.

--

## [Course project] Evaluation: 85% =

- [Project management]() <bcolor>= 15%</bcolor>
  - reproducibility, github, readme
- [Project relevance]() <bcolor>= 10%</bcolor>
  - Does the project respond to an interesting/important question?
- Quality of the [visualisation]() <bcolor>= 20%</bcolor>
  - Choice of the graphical representations & colors
- [Technical]() dimension <bcolor>= 15%</bcolor>
  - Is the project using advanced tools/techniques?
- [Oral]() presentations <bcolor>= 25%</bcolor>
  - ML1: Project idea & scrapping methodology <bcolor>= 5%</bcolor>
  - ML2: Visualisation plan <bcolor>= 5%</bcolor>  
  - ML3: Final presentation <bcolor>= 15%</bcolor>  


--

## Course Communication
- Us $\rightarrow$ you
  - Course communication will be done through [lola's forum]()

- You $\rightarrow$ us
  - We will be available
    - During the breaks, after the class.
    - Michel Copée can answer questions about lectures, notebooks, assignments, and projects

  - **Personal question**:
    - face-to-face interaction > email
  - **General interest question**:
    - forum > email

--

## <i class="fa fa-book fa-fw" aria-hidden="true"></i>References?<i class="fa fa-book fa-fw" aria-hidden="true"></i>

No general texbook. Specific references will be given when corresponding subjects are tackled.

- [Introduction](https://pp4rs.github.io/pp4rs-python/intro.html) to python, pandas, plotting

- [Stackoverflow](https://stackoverflow.com/): all the answers are there, but you have to ask the right question.

---

<!-- .slide: id="hw"-->
# Epilogue
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>


--

## Troubleshooting

  - Use the [course forum]() to share & find answers
  - Let's try to make this a <bcolor>fun collaborative experience</bcolor> for everyone
