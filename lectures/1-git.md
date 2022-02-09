# Data Management
## GIT: A version control system
### [Malka Guillot](https://malkaguillot.github.io/)
### HEC Liège | <a href="https://gitlab.uliege.be/mguillot/econ2306-data-management-2021-22/">ECON2306</a>


---

<!-- .slide:  id="toc" class: left, inverse -->
# Table of contents

1. [The importance of version control ](#why)

2. [Getting started on a project ](#start)

2. [Using Git](#how)

2. [Using Git for collaboration](#hw)

<!--
Réfernce :

- lecture git (but with RStudio) => Grant Delmott
- Aniket : https://github.com/dlab-berkeley/Computational-Social-Science-Training-Program/blob/master/Reproducible%20Data%20Science/GitHub%20Intro.md
- slides : https://www.frankpinter.com/notes/git-for-economists-presentation.pdf

For students:
- manuel git : https://happygitwithr.com/
- gitlab cheatsheet https://about.gitlab.com/images/press/git-cheat-sheet.pdf
- interactive tutorial https://gitimmersion.com/index.html
- interactive tutorial git branching https://learngitbranching.js.org/?locale=fr_FR

-->

Notes:
Throughout this course, we'll be using a platform called GitHub. GitHub is a popular code hosting platform. It has lots of features that make version control and collaboration easier.

---

<!-- .slide: id="why"  -->
# The importance of version control

<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>


--

<!-- .slide: class="fragmented-lists" -->

## What is version control?

Version control is a way to keep track of changes to code, text, and documents. And data and outputs.

  - It gives you an organized revision history
  - It lets you experiment *without fear*
  - It lets you go back and forth between many different versions of the same file, and see a list of the differences
  -  It makes (the technical aspects of) collaboration a breeze
  -  It lets you and your collaborators work on different versions and then merge them

Notes:
Version control refers to the techniques for managing changes to software and code, and easily going back and forth between older and new versions of a code base. Getting familiar with GitHub and all of its tools can take some time, but the benefits for open science and streamlined collaboration are worth it.

--

## From local to distributed version control system
- <bcolor>Local</bcolor>: everything is on your computer
<img data-src="./images/git-local-vc.png"  style="height: 350px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

[$-$]() No collaboration

[$-$]() Not possible to retrieve files if the local machine crashes

--

## From local to distributed version control system
- <bcolor>Centralized</bcolor>:
  - all files on 1 server
  - many collaborators checkout files
<img data-src="./images/git-centralized-vc.png"  style="height: 350px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

[$+$]() Collaboration

[$-$]() Not possible to retrieve files if the central server crashes

Notes:
Each collaborator only have a working copy. Only the server has the full history.

--

## From local to distributed version control system
- <bcolor>Distributed</bcolor>:
  - one or more servers
  - many collaborators
<img data-src="./images/git-distributed-vc.png"  style="height: 350px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

[$+$]() Collaboration

[$+$]() Each user has their own repository and a working copy

Notes:
**CCL**: GitHub is a useful tool because it removes a lot of the obstacles that we usually face when we are collaborating with others.
- Instead of *saving multiple versions* of the same document, GitHub lets us iterate on the same document while recording how it has changed over time.
- Rather than sending collaborators *messily named documents*, everyone can work from the same GitHub repository.
- GitHub also has tools for *resolving editing conflicts* between collaborators and creating a clear workflow.


--

## Why bother?

<img data-src="./images/phd-comics-doc.gif"  style="height: 550px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

Also [git vs. Dropbox from a researcher's perspective](https://michaelstepner.com/blog/git-vs-dropbox/)

Notes:
This type of version control, where you put dates or number of things is not efficient:
- very hard to (collectively) remember what caused the change of version
- even harder to keep track of the correction of a coding error (which versions are right)?
- Maybe you introduced a new mistake !  

--

## [CCL] Version control system

Enables <bcolor>coordinatation</bcolor> $\rightarrow$ no code change is lost or accidentally overwriten.

Provides an organized <bcolor>sharing</bcolor> platform $\rightarrow$ *open source* & documentation

$\Rightarrow$ key tool from our <bcolor>project management</bcolor> perspective

$\Rightarrow$ widely used in a companies / not enough in research:

- Software development
- Scientific researcher
- Anything involving coding (even latex)


Notes:
- [Central]() role of VC in global software development
- [Research]() : Git(Hub) helps to operationalize the ideals of **open science** and **reproducibility**.

---

<!-- .slide: id="git"  -->
# Git(Hub)
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## Git(Hub): a solution

- [Git](https://git-scm.com/):  
 <!-- .element: class="fragment" data-fragment-index="1" -->

  - Git is a <bcolor>distributed version control system</bcolor>. *(Wait, what?)*

  - *Okay, try this:* Imagine if Dropbox and the "Track changes" feature in MS Word had a baby. Git would be that baby.

  - most popular *open source* version control system out there.

  <!-- .element: class="fragment" data-fragment-index="1" -->

<!--
  *Even better* than that because Git is optimised for the things that economists and data scientists spend a lot of time working on (e.g. **code**).
-->

- [GitHub](https://github.com/)   <!-- .element: class="fragment" data-fragment-index="2" -->

  - GitHub = <bcolor>online hosting platform</bcolor> that provides an array of services built on top of the Git system. <!-- .element: class="fragment" data-fragment-index="2" -->
    - (Similar platforms include Bitbucket and GitLab.)

  <!-- .element: class="fragment" data-fragment-index="2" -->

--

## Git vs. Github

- It's important to realize that Git and GitHub are distinct things.

- We don't *need* GitHub to use Git... But it will make our lives so much easier.

$\rightarrow$ There is a learning curve, but I promise you it's worth it.

  <!-- .element: class="fragment" data-fragment-index="3" -->

<img data-src="./images/git_github.jpg"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

Notes:
- **Git** helps to coordinate so that no code change is lost or accidentally overwriten.

- **Git** solves the version control problem, **GitHub** solves the code repository problem.


--

## Git model

1. You do work in your <bcolor>working directory</bcolor>
2. Then you add it to your <bcolor>staging area</bcolor>
2. Once you've staged [all you changes for one discrete task](), <bcolor>commit</bcolor> a snapshot of the staging area
3. If you have a remote repository, <bcolor>push your commit</bcolor>

<img data-src="./images/git-local-remote.webp" style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block; background-color: #e5e0d8" >

--

## Commits: saving a snapshop
"One discrete task" = a collection of changes, across multiple files (or not), that does *one thing*.

Examples:
- Change the formatting of a variable from string to numeric, and treat it properly across multiple scripts
- Change your regression specification in code, in the output, and in your paper and supporting documentation
- Add a new function

--

## Commit message
Examples:
- “Change the formatting of start date variable from string to date format”
- “Add year dummies to regression specification”

$\rightarrow$ The more detail, the more your future self will thank you.

--

## Commit: example
<img data-src="./images/commit-example.png" style="height: 550px; position:relative;     margin-left: auto;margin-right: auto;display: block; background-color: #e5e0d8" >


---

<!-- .slide: id="start"  -->
# Getting started on a project

<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## First steps: Setup [GitHub account](https://github.com/)

- Navigate to [GitHub's homepage](https://github.com/) + "Sign Up"
  - Go through the account setting steps ("Verify your email address"...)

<img data-src="./images/github sign up.png"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

Navigate to GitHub's homepage. Navigate to "Sign Up" in the top right hand side of the page.

--

## Getting started with Git(Hub)

1. Install [Git](https://git-scm.com/downloads) (Linux, Mac, Windows) if not already installed

2. Git comes with a command line interface (powerful!).

3. You might want to add a *graphical interface* to make things easier:
  - [GitHub desktop](https://desktop.github.com/)

--

## Your first repository


--

## How to interact with the materials?

1. **Simple** -> Just use the online GitHub interface to
   - Access the materials
   - Amend the students' presentation signing sheet
2. **Advanced**
   - Download [git](https://git-scm.com/downloads)
   - Create an account on [GitHub](https://github.com/)
   - Go through this [simple guide](https://rogerdudler.github.io/git-guide/)
   - In case it goes wrong: http://ohshitgit.com/

You can use [mybinder](https://mybinder.org/v2/gh/MalkIPP/big_data_policy_2021/main) to launch the notebooks from Github


--

## Course materials are on [Github](https://malkaguillot.github.io/ECON2206-Data-Management-2022/)

- [Git](https://git-scm.com)
  - Git is a distributed version control system.
  - Dropbox + track changes, optimized for codes
- [GitHub](https://github.com/) (≠ Git)
  - = Online hosting platform that provides an array of services built on top of the Git system.
  - Makes life easier

>Github is also great for scientific research and for collaboration on code.

--
