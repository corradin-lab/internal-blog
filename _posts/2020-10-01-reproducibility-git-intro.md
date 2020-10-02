---
title: Introduction to git
description: Meeting notes for introduction to git Oct 1st
toc: true
comments: true
layout: post
categories: [git, reproducibility]
author: An Hoang
---

# Talked about our current issues
- Orian dealing with different versions of scripts. Figuring out Git
- Yanwei dealing with multiple files/threshold to test with GSEA
- An dealing with broken conda environment, cannot install packages

# Talked about the article  [Reproducible Programming for Biologists Who Code. Part 1: Must do](https://ben-heil.github.io/2020-06-16-mustdo/)

## Version control

### Showed the `.snapshot` folder on Whitehead's `corradin_data` (`corradin_biobank` and `corradin_cache` are not backed up)

### War stories
- Created multiple versions of a file and forgetting what they do

- Change one file and don't know if the other files in a pipeline still work or not. Need to test multiple versions of a step in a pipeline

- Inheriting a script from someone else, want to make changes => create different functions `function_x`, `function_x_an`


- Every time create a new feature, duplicate the old file and then add new feature to the new file. Finally, **MANUALLY MERGE BY EYE** to see which line changed between the new file and the old one to copy and paste back into the old file

- The need to maintain two versions of a script concurrently: **development/experiment** and **production**.

- Accidentally delete files and have to rely on backups by IT, which might not be fine-grained enough to save changes between two backups.

- Jupyter froze and did not save code => have to rewrite code


### Introducing git

#### Barebones, layman definition
![]({{ site.baseurl }}/images/logo.png "fast.ai's logo")

![https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control](/images/reproducibility/git/git-simple.png "test image not working")

![https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control]({{ site.baseurl }}/images/reproducibility/git/git-simple.png "test")

- `git` is like the `.snapshot` folder storing backup of different versions for you only. `github` is like Google Drive, where you share your code/files with other people. 
  - If you work alone, on the same machine, git is enough
  - If you work alone, on different machines, use git to backup on your local machine, then push to Github
  - If you work with other people, push to Github as above

- Fundamental unit: a `commit`. Committing changes is like saving a checkpoint/version to go back to in video games.

Read more:
- https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control
- https://coderefinery.github.io/git-intro/01-motivation/
- https://kbroman.org/github_tutorial/pages/why.html

  
#### 5 "locations" your file goes through

![https://ndpsoftware.com/git-cheatsheet.html#loc=;]({{ site.baseurl }}/images/reproducibility/git/5-git-locations.png)
![https://www.edureka.co/blog/git-tutorial/]({{ site.baseurl }}/images/reproducibility/git/5-git-locations-with-commands.png)
![]({{ site.baseurl }}/images/reproducibility/git/git-commands-to-switch-between-file-status.png)


  1. **Stash**: save your changes temporarily in a stack (eg. a change that is not final enough to be a commit). Kind of like `Ctrl + Z`, although you get to define how much work/code is restored each time. You can reapply your changes from the most recent save to the oldest one


  2. **Workspace**: Your active working space, files you create will go here. Files that don't have changes since last commit will go here. Once you added/committed a file, Git tracks the status of that file and tell you (unchanged, uncommitted change)

  3. **Index/Staging area**: Think of it as a loading dock. If your `commit` is like a *shipment*, and your `file changes` are like *individual packages* then your `index/staging area` is where you bundle those changes (could be from one or many different files) into one shipment. 

        Once you have commited the changes/save your check point/sent off the shipment, these changes are always bundled together. Going back to the checkpoint will load changes up until that commit/version 

  4. **Local repository**: Your `.git` folder in the same location that saves all your versions


  5. **Upstream/Remote repository**:  Where you upload your files onto the internet/cloud. This can be Github, Bitbucket, AWS or sites that can store your data for a fee

#### 4 status of file
![https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository]({{ site.baseurl }}/images/reproducibility/git/life-cycle-of-file-status.png)

![https://screencasts.delicious-insights.com/courses/git-core-concepts/102205-default-section/305169-zones-and-file-lifecycle]({{ site.baseurl }}/images/reproducibility/git/file-transitioning-states.png)

Read more:
- https://ilearnthis.com/a/git-file-status-lifecycle/
- https://screencasts.delicious-insights.com/courses/git-core-concepts

#### Tying the two concepts together

![]({{ site.baseurl }}/images/reproducibility/git/location-and-file-status.png)


## Recording data access
- Save the command to download the data (UKBiobank, outside dataset)
- Record the download/access date or version of the dataset
- **How to link data artifact to code?** DVC #future
- **Catalog of data for each project and their metadata** Intake

# Actions for next meeting

  ## Everyone
  - Learn about git commands from the resources below : add, commit, push, merge, branch, checkout, pull 
  - Check out all resources in the **shared** section (they are short, visual and helpful) and one in **optional** section
  
  ## An
  - Design git/github activity (fork, pull request, branch)
  - Prepare more materials on git workflow for data analysis (how often to commit, when to commit etc, branching, visualizing git)
  - Find resources for git + Jupyter, git submodules/changing folder structure
  - Find resources about python package management (conda + pip + Docker)
  - Do nbdev/fastpage tutorial

# Resources
  
## Shared
### Cheatsheets
  * [git - the simple guide - no deep shit!](http://up1.github.io/git-guide/index.html)
  * [Git: Cheat Sheet (advanced) | Maxence Poutord](https://www.maxpou.fr/git-cheat-sheet)
  * [Interactive Git Cheatsheet](https://ndpsoftware.com/git-cheatsheet.html#loc=workspace;)
  * [Flowchart for when getting stuck](http://justinhileman.info/article/git-pretty/git-pretty.png)

### Learning resources
  * [GitHub Guides](https://guides.github.com/) (In order: Git Handbook,Understanding the Github flow, Hello world, Forking projects)
  * [Resources to learn Git](https://try.github.io/) (Git-It section)
  

## Pick one (and explore as many as you'd like):
  * [Git Immersion](https://gitimmersion.com/)
  * [Introduction to version control with Git - Git introduction](https://coderefinery.github.io/git-intro/)
  * [Version Control with Git](http://swcarpentry.github.io/git-novice/)
  * [git/github guide](https://kbroman.org/github_tutorial/)
  * [🐙 Git series 1/3: Understanding git for real by exploring the .git directory · daolf](https://www.daolf.com/posts/git-series-part-1/)


## Extra resources (Ignore below if you're not An):
  * [A Visual Git Reference](http://marklodato.github.io/visual-git-guide/index-en.html)
  * [Learn Git Branching](https://learngitbranching.js.org/)
  * [git ready » learn git one commit at a time](http://gitready.com/)
  * [Git | Martin Zlámal 🤓](https://mrtnzlml.com/docs/git)
  * [Git power tools for daily use » nvie.com](https://nvie.com/posts/git-power-tools/)
  * [nvie/git-toolbelt: A suite of useful Git commands that aid with scripting or every day command line usage](https://github.com/nvie/git-toolbelt#readme)
  * [The Thing About Git](https://tomayko.com/blog/2008/the-thing-about-git)
  * [Git Staging Area: Explained Like I'm Five - DEV](https://dev.to/sublimegeek/git-staging-area-explained-like-im-five-1anh)

  * [Git - Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)

### Workflow
  * [Principled Git-based Workflow in Collaborative Data Science Projects - Essays on Data Science](https://ericmjl.github.io/essays-on-data-science/workflow/gitflow/)
  * [Understanding the Git Workflow](https://sandofsky.com/workflow/git-workflow/)
  * [A successful Git branching model » nvie.com](https://nvie.com/posts/a-successful-git-branching-model/)
