# ECON2306-Data-Management-2021-22

Course materials for Spring 2021 HEC Liège Course, "Data Management"

## Outline of the class

The following table presents the structure of the class through the program & materials of the Lectures et the Practices classes.
The **Lecture** column lists the content associated with theoretical presentations.  
The **practice** column details the content associated with practical sessions.
The **Homework** column details the homework, that are either project's milestones or problem sets.

| Week   | Lecture                                         | Practice                               | Problem sets, project milestones    |
|--------|-------------------------------------------------|----------------------------------------|-------------------------------------------|
| 10-Feb | Introduction [html](https://malkaguillot.github.io/ECON2206-Data-Management-2022/lectures/0-overview.html) [pdf](https://raw.githubusercontent.com/malkaguillot/ECON2206-Data-Management-2022/fa3fa2cfbef59cd251825fde90e1ca3abbab6805/lectures/0-overview.pdf)| Using git [html](https://malkaguillot.github.io/ECON2206-Data-Management-2022/lectures/1-git.html) [pdf](https://raw.githubusercontent.com/malkaguillot/ECON2206-Data-Management-2022/fa3fa2cfbef59cd251825fde90e1ca3abbab6805/lectures/1-git.pdf) | Installing python using the [guide](https://dox.uliege.be/index.php/s/nDh7bKGWhriRor2) ; getting ready with git         |
| 17-Feb | Introduction to Python [slides]()               | Python practice [notebook](https://github.com/malkaguillot/ECON2206-Data-Management-2022/blob/main/practice/1-intro-python/Introduction%20to%20Python.ipynb)                       |                                           |
| 24-Feb | The importance of visualization principles (1h) [slides]() | Pandas 1: introduction (2h) [slides]() | **PS1**:  simple pandas + graphs (due:10/03) |
| 03-Mar | Webscraping theory [notebook](https://github.com/malkaguillot/ECON2206-Data-Management-2022/blob/main/lectures/3-data-collection.ipynb)                 | Webscraping practice [notebook]()      |  Start thinking about a project idea      |
| 10-Mar | ML1: intro + unsupervised [notebook]()          |  Brainstorming on project ideas ; Starting webscraping of project |                                           |
| 17-Mar | ML2: supervised  [notebook]()                   |  Practice ML [notebook]()              |   **PS2** on ML (due: 31/03)                  |
| 24-Mar | Natural Language Processing [slides]()          |  NLP [notebook]()                      | ML1: Having decided on the project idea       |
| 31-Mar | Visualization using dash                        |  Presentation of project ideas & scraping methodology 'Open house' on webscraping of project | **PS3**: on NLP (due: 05/05)    |
| 28-Apr | _Topic to be decided together_*                 |   ‘Open house’ on dash visualization   | ML2: Webscraping done; starting with visualization    |
| 05-May | _Topic to be decided together_*                 |   ‘Open house’ on dash visualization   |                                           |
| 12-May |                                                 |   ‘Open house’ on dash visualization   |                                           |
| 19-May | Student’s presentation of the applications      |                                        |                                           |

* Lists of potential subjects : Maps, Creating a Github website, Replication package, Logging, Pandas and SQL, Scraping twitter, Selenium, Scrapy, Computer vision

## Course project
I would like you to chose a standard [research or policy or business] question that you can answer using data (eg. where are located the death from covid? Where are the cheapest beers in Liège? At what time people go to work? When and where should you go sailing?)

You will develop a project abiding by the good practices taught in class. The project should incorporate:

- Include an original **data collection step** (webscraping)
- The **main output** should be a `dash page` that you develop on `Herokuapp`, and should include;
  - Some text, with brief explanations regarding : the question asked, the choice and the nature of the data (you do not have to include the data steps [collection & cleaning] here), the exhibits (should have reading notes) and what you conclude from them.
  - 4 exhibits: 2 tables and 2 Figures (using different commands)
  - The possibility to modify the visualization using button for at least one exhibit

**Submission format**: Invite @malkaguillot and @michel to collaborate on your GitHub repository by the due date.

    - This means, we expect well version controlled work.
    - a github folder with at least 5 commits (bonus if you have several development branches!)
    - Tag your final submission using the following `git command git tag -a 1.0 -m "submitted version"`.
    - You must have a `README.md` in the main directory with:
      - instructions on how we can build the assignment & what it does;
      - a link to the deploymed application.

Projects should be realized by group of 1 or 2 (one group of 3 if there is an odd number of remaining students).

**Project milestones**
We will discuss about your proposed project several times so that we can evaluate whether it is do-able within the time frame. The project will be organized around the following milestones, materialized by a presentation in class:
- ML1: Project idea & scraping methodology (5 minutes)
- ML2: Visualization plan (5 minutes)
- ML3: Final presentation (5 minutes)
At ML3, you should also hand the final course product (by inviting us to your gitlab folder).

## Problem sets
The Problem sets are simple exercises designed to help you to “get their hands in the data”. They will be available on Lola and should be handed in there. These problem sets will take the form of Jupyter notebooks, that will have to be converted in pdf before being handed in.

## Evaluation

| Detail                                                                                                              | Grading decomposition  |
| ------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| **Problem sets (individual)**                                                                                       | **15%** (5% each)      |
| **Course project**                                                                                                  | **85%**                |
| Project management (reproducibility, github, readme)                                                                | 15%                    |
| Relevance of the project<br>Does the project respond to an interesting/important question?                          | 10%                    |
| Quality of the visualization<br>Choice of the graphical representations & colors                                    | 20%                    |
| Technical dimension<br>Is the project using advanced tools/techniques?                                              | 15%                    |
| Quality of the oral presentation<br>_Final presentation_<br>_Project idea & scraping methodology_<br>_Visualization plan_ | 25%<br>_15%_<br>_5%_<br>_5%_ |
| **Bonus (class participation)**                                                                                     | **5%**                 |
