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

Notes: my notes

<!--
Réfernce :
- manuel git : https://happygitwithr.com/
- lecture git (but with RStudio) => Grant Delmott
- Aniket : https://github.com/dlab-berkeley/Computational-Social-Science-Training-Program/blob/master/Reproducible%20Data%20Science/GitHub%20Intro.md
- slides : https://www.frankpinter.com/notes/git-for-economists-presentation.pdf
- gitlab cheatsheet https://about.gitlab.com/images/press/git-cheat-sheet.pdf
-->


---

<!-- .slide: id="why"  -->
# The importance of version control

<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

<!-- .slide: class="fragmented-lists" -->

## What is version control?

Version control is a way to keep track of changes to code, text, and documents. And data and outputs.

  - It gives you an organized revision history
  - It lets you experiment without fear
  - It lets you go back and forth between many different versions of the same file, and see a list of the differences
  -  It makes (the technical aspects of) collaboration a breeze
  -  It lets you and your collaborators work on different versions and then merge them

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

## Git(Hub) solves this problem

- [Git](https://git-scm.com/):  
 <!-- .element: class="fragment" data-fragment-index="1" -->

  - Git is a <bcolor>distributed version control system</bcolor>. *(Wait, what?)*

  - *Okay, try this:* Imagine if Dropbox and the "Track changes" feature in MS Word had a baby. Git would be that baby.

  <!-- .element: class="fragment" data-fragment-index="1" -->

<!--
  *Even better* than that because Git is optimised for the things that economists and data scientists spend a lot of time working on (e.g. **code**).
-->

- [GitHub](https://github.com/)   <!-- .element: class="fragment" data-fragment-index="2" -->

  - It's important to realise that Git and GitHub are distinct things.

  - GitHub = <bcolor>online hosting platform</bcolor> that provides an array of services built on top of the Git system. <!-- .element: class="fragment" data-fragment-index="2" -->
    - (Similar platforms include Bitbucket and GitLab.)

  <!-- .element: class="fragment" data-fragment-index="2" -->

We don't *need* GitHub to use Git... But it will make our lives so much easier.
$\rightarrow$ There is a learning curve, but I promise you it's worth it.

  <!-- .element: class="fragment" data-fragment-index="3" -->

--

## Git(Hub) for:

- Software development

- Scientific researcher

- Anything involving coding (even latex)

Notes:
- [Central]() role of VC in global software development
- [Research]() : Git(Hub) helps to operationalise the ideals of **open science** and **reproducibility**.

---

<!-- .slide: id="start"  -->
# Getting started on a project

<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

1. Install [Git](https://git-scm.com/downloads) (Linux, Mac, Windows)

2. Git comes with a command line interface (powerful!).

3. You might want to add a *graphical interface* to make things easier

--

## First steps

- Login to gitlab using you uliege address [segi instructions](https://my.segi.uliege.be/cms/c_10828225/fr/mysegi-gitlab)

- create ssh key https://docs.gitlab.com/ee/ssh/index.html
  1. open a terminal
  2. ```ssh-keygen -t ed25519 -C "comment"

More details on [gitlab docs](https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html#configure-git)

--
