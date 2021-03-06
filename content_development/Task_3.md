---
output:
  html_document: default
  pdf_document: default
---

# Task 3: How to integrate Git with R Studio

This task is designed for students and researchers who want to implement a system of version control within a standard R-based workflow. Your future research self will thank your for the convenience.

Don't forget you can join in the discussions over at our open [**Slack channel**](https://openmooc-ers-slackin.herokuapp.com/). Please do introduce yourself at #module5opensource, and tell us a bit about who you are, your background, and how you ended up here!

Estimated time to complete: 30 minutes

Estimate time saving once complete: Virtually infinite

## Table of contents

* [Getting started](#Getting_started)
  * [Git](#Git)
  * [R Studio](#Rstudio)
* [Step one: Download all the things](#one)
* [Step two: Configure Git inside RStudio](#two)
* [Step three: Why did I just do that?](#three)
* [Step four: The perfect marriage between Git and R](#four)
* [Step five: Getting content with content](#five)
* [Step six: A brave commitment](#six)
* [Step seven: PUSH!](#seven)


## Getting started <a name="Getting_started"></a>

Congratulations on making it this far! If you're reading this, you've survived pull requests, webhooks, and can probably even tell us know what the F in FOSS stands for (*not* Frustration...) Hopefully, you have overcome any skepticism or reluctance towards the benefits of GitHub and Open Source Software, and are ready to take the next step.

Before starting this Task, make sure you have already completed [Task 1](https://github.com/OpenScienceMOOC/Module-5-Open-Research-Software-and-Open-Source/blob/master/content_development/Task_1.md) and [Task 2](https://github.com/OpenScienceMOOC/Module-5-Open-Research-Software-and-Open-Source/blob/master/content_development/Task_2.md), so that you are more familiar with GitHub and some standard Open Source practices.

This task will teach you how to integrate the version control software, Git, with the popular coding environment, RStudio. And yes, it is Git as in gif or God, not Jit as in the wrong way of pronouncing things.

If you are one of those researchers who thinks that having code spread across multiple hard-drives that are waiting to break, Dropbox, Google Drive, or any other non-specialist software, this task is just for you. All of us are guilty of this sort of thing once in a while, but there are ways to do it that are better for you, future you, and those who might benefit from your work.

<br/>

### Geting Git <a name="Git"></a>

So, what is Git, and how is it different to GitHub? Git is a version control system, which enables you to save and track time-stamped copies of your work throughout the development process. It also works with non-code items too, like this MOOC, the majority of which was written in markdown in R Studio, and integrated with a Git/GitHub workflow.

This is important, as all research goes through changes, and some times we want to know what those things were. Did you delete some text that you now think is important? Version control will save that for you. Did your code used to work perfectly, but is now buggy beyond belief? Version control. It's a great way to avoid that chaotic state where you have multiple copies of the same file, but without a stupid and annoying file naming convention. `FINAL_Revised_2.2_supervisor_edits_ver1.7_scream.txt` will be a thing of the past.

<p align="center">
  <img src="https://github.com/OpenScienceMOOC/Module-5-Open-Research-Software-and-Open-Source/blob/master/content_development/images/phdcomics.png" width="600px"/>
</p>

<p align="center"><i>Never again. (Source: phdcomics.com)</i></p>

<br/>

GitHub is the platform that allows you to seamlessly share code from your workspace (e.g., laptop) to be hosted in an online space. So, sort of like the public interface to GitHub. The advantages of this are:

1. You get to keep copies of all your work through time;
2. You can compare work through different copies through time, which helps to spot bugs or errors;
3. Other people can collaborate openly with your work; 
4. You have both a local and an online copy of your work that remain in sync; 
5. You can see who made a change, why they made, and when;
6. You can have multiple people working on the same project at once in parallel.

<br/>

### RStudio <a name="Rstudio"></a>

RStudio is a popular coding environment for researchers who use the statistical programming language, R. It comes with a text editor, so you don't have to install another and switch between. It also includes a graphical user interface (GUI) to Git and GitHub, which we will be using here.

Isn't it nice when brilliant Open Source tools integrate seamlessly like that.

If at any point you need to install new packages for R, simply use the following command:

<br/>

`install.packages("PACKAGE NAME", dependencies = TRUE)`

<br/>

Replacing `PACKAGE NAME` with the, er, package name. Some examples you can play with that might come in useful include `knitr` or `ggplot2`.

<br/>

## Step one: Download all the things <a name="one"></a>

1. You should already have a GitHub account by now if you have followed the previous tasks. If not, [sign up here](https://github.com/). Free unlimited repositories for all!
2. Download and install the latest version of [R](https://www.r-project.org/). Also available for [Mac](https://cloud.r-project.org/) and [Linux](https://cloud.r-project.org/bin/linux/).
3. Download and install the latest version of [Rstudio](https://www.rstudio.com/products/rstudio/#Desktop). Oh, hey, looks it Open Source! Swish.
4. Download and install the latest version of [Git](https://gitforwindows.org/). **Make sure to Select “Use Git from the Windows Command Prompt” during installation.**

> **Pro-tip**: To update all of your R packages in one, simply execute the following code `update.packages(ask = FALSE, checkBuilt = TRUE)`

For now, just choose all the usual default options for each install. Depending on which Operating System (e.g., Mac, Windows, Linux), this might be different for each of you. For now, and for the rest of this task, we're going to stick with doing things the easy-ish Windows way (but also provide some instructions for using the command line).

If you want, you can also download the [local version of GitHub](https://desktop.github.com/) and use it through the simple GUI. It's available on Windows and Mac and Linux, and can make your life a little easier, especially if you want to use a different platform to RStudio.

> **Pro-tip:** You see when installing Git it says 'Use Git Bash as shell for Git projects?' This is the place where you can use the command-line to access Git from outside of RStudio. It's a powerful beast. Try the following two commands to get started:

<br/>
  `git config --global user.name 'YOUR USERNAME'`
<br/>
  `git config --global user.email 'YOUR EMAIL'`
<br/>

## Step two: Configure Git inside RStudio <a name="two"></a>

Right, that's the easy bit done. Next, go into RStudio, and in the tabs at the top go to Go to **Tools > Global Options > Git/SVN**. SVN is just another version control system like Git, and we don't need to worry about that here.

In the place where it says *Git executable*, add the pathway here to the git.exe file that you just downloaded in the previous step. Make sure all the boxes here are ticked.

<p align="center">
  <img src="https://github.com/OpenScienceMOOC/Module-5-Open-Research-Software-and-Open-Source/blob/master/content_development/images/git_svn.png" width="400px"/>
</p>

<p align="center"><i>The Global Options window inside RStudio</i></p>

<br/>

Next, hit the button in this window that says *Create RSA Key*, This is a private key that is used for authentication between different systems. Here, it will pop up a new window with a public key, that you want to copy to your clipboard. 

Head over to GitHub, go to your profile settings, and the *SSH and GPG keys* tab. Click *New SSH key*. Here, paste in the key from RStudio, and call it something imaginative like 'RStudio'.

<p align="center">
  <img src="https://github.com/OpenScienceMOOC/Module-5-Open-Research-Software-and-Open-Source/blob/master/content_development/images/ssh_key.png" width="800px"/>
</p>

<p align="center"><i>Inside GitHub where you will want to enter the key you just generated in RStudio</i></p>

<br/>

OK, now hold on to your butts, we're going into the commandline. Back in RStudio, go to **Tools > Shell**, and it will open up a command prompt window. If you already played with the Git Bash above, you should have done this step already. Enter the following two commands:

<br/>
`git config --global user.name 'YOUR USERNAME'`
<br/>
`git config --global user.email 'YOUR EMAIL'`
<br/>

Hopefully it does not have to be said to substitute in your own GitHub username and email here. You can access this at any point just by finding the 'Shell' within Windows. Or, if you right click on any folder on your Desktop that is linked to a GitHub repo, you can open up the Shell instantly and Bash away.

What this stage has done is configure Git, which is software that runs on your desktop, to GitHub, which is a repository website.

Restart R Studio. Whew, that was tough. Next.

## Step three: Why did I just do that? <a name="three"></a>

OK, hold your breathe, we're going to learn some more Git commands. Some of the key ones you could do with learning are:

* **Repository**: This is the location for all of the files associated with your project.

* **Add**: This is where you submit files to the staging area before being committed.

* **Commit** This is like 'saving' your work by creating a new version or copy.

* **Push**: This is how you send files from your local project to the online repository.

* **Pull**: This is how you get files from your online repository to your local project.

## Step four: The perfect marriage between Git and R <a name="four"></a>

Now, in Task 1, you should have learned how to build your very first GitHub repository. If you haven't done that, we can wait here while you go and do that. If you have already, or have an existing GitHub repository, we can move on.

So, you should have a repository on GitHub, complete with a `README` file, a `LICENSE` file and some other bits and bobs.

What we are going to do now, is integrate that repository with Git. Steady now.

1. Firstly, go to **Project > Create Project > Version Control > Git**.
2. Back on GitHub, you should see a bit where there is a https:// URL. That is the link to your repository, and it gives you the option to clone it in your desktop. For now, just copy that link, switch back to RStudio, and paste it into the 'Repository URL' as indicated.
3. Give the project a directory name, like test, Jim, or whatever you want.
4. Next, browse for the place on your desktop where you want this project to live, its subdirectory.
5. Click 'Create Project', and let the magic be done!

What you just did was tell RStudio to associate a new project in R with specific repository on GitHub.

## Step five: Getting content with content <a name="five"></a>

Remember that `README` file we created a while back? Well, it's time to write it. Thinking back to Task 1, there were some specific things that we said make a good `README` file. Do you remember what any of them were? Just to refresh your memory, these were:

* What is this project about and what does it do.
* Why should people care, and why is it useful.
* How can someone get started contributing to the project.
* Who can be contacted in case someone needs help.
* A link to the license, contributing guidelines, and code of conduct.
* A description of the project structure.
* Who is involved, and what are their roles.
* The current status of the project.

So, in RStudio, try adding just a bit of information about this for your project. If you are doing this for an actual project, try and make it useful. If you are just tinkering for now, you can add what you want.

Remember that your `README` file is in markdown (.md) format. For a refresher on some of the simple syntax markdown uses, check this [handy cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

<p align="center">
  <img src="https://github.com/OpenScienceMOOC/Module-5-Open-Research-Software-and-Open-Source/blob/master/content_development/images/markdown.png" width="600px"/>
</p>

<p align="center"><i>Screenshot of what this module looks in markdown, during development. Meta.</i></p>

<br/>

## Step six: A brave commitment <a name="six"></a>

OK, so now you should have a nicely edited `README` file. Now we are going to 'commit' this to the project using Git. This is basically the equivalent of saving this version of your project, with a record of what changes were made. Successive commits produce a history that can be examined at a later time, allowing you to work with confidence.

There are a few ways of doing this.

1. Go to Tools > Version Control > Commit
2. In the environment pane in RStudio, there should be a new 'Git' tab. Handy.
3. In your console pane, there should now be a new 'Terminal', which you can run Git command lines through.

Let's just stick with the second option for now.

Select the README` file in the Git window, which should show up automatically if you have made any edits to it. This adds that file to the 'staging' area, which is sort of like the pre-saving space for your work. Click 'Commit' and a new window should pop up.

Here, you have a chance to review your changes, and write a nice commit message. Type in something brief, but informative about the changes that you have made in this version. You want this to be enough information so that if you or someone else looks back on it, you'll know why you made this commit and the changes associated with it.

> **Pro-tip**: Here, you will see a list of all the changes you have made since your last commit. Old lines are in red, and new lines are in green. Double check these to make sure that the edits you have made are the ones you intended to make. Safety first.

When you click 'Commit', another window will pop up, telling you how many files you have changed and the number of lines within that file you have changed. Close that little window down.

## Step seven: PUSH! <a name="seven"></a>

Click the 'Push' button in the top right of the new window. A new window will pop up now. What this is doing is syncronising the files changed on your local repository with the `README` file to the online version of the project on GitHub. 

Some times here you will be prompted to add your username and password from GitHub, which you should do if asked.

Close that window down, and the next one. Go to your project on GitHub, refresh, and check that the `README` file is still there in all its newly edited glory. You should see the commit message you made next to the file too.

**CONGRATULATIONS**

You just integrated Git with R Studio, and made your first change to a version controlled project. Your life will now never be the same, and your research workflow will probably be more rapid, agile, and collaborative than ever. Good luck going back to Word.

The great thing is that this doesn't have to just be used for code. You can use it for plain text, markdown, html, and, well, R code. The possibilities are limitless - what you have just learned is a new form of openly collaborative project management that works for an enormous range of tasks. How you use it is up to you.

## Checklist for integrating Git and R Studio <a name="Checklist"></a>


- [ ] 


**CONGRATULATIONS!** 


From now on, it is all up to you! Some advice is to:

* Make frequent commits. Treat Git like your puppy, in that it requires constant and special attention. Just a pat on the head every now and then is enough to keep it satisfied, but it'll be happiest with sustained servicing.

* Push often. Don't let those commits build up, otherwise you run more risk of getting into merge conflicts. Seeing as these can be the stuff of nightmares, just make sure to push often.


**Know a way this content can be improved?**

Time to take your new GitHub skills for a test-run! All content development primarily happens [here](https://github.com/OpenScienceMOOC/Module-5-Open-Research-Software-and-Open-Source/blob/master/content_development/Task_3.md). If you have a suggsted improvement to the content, layout, or anything else, you can make it and then it will automatically become part of the MOOC content after verification from a moderator! 
