---
toc: true
layout: post
description: A quick guide to setting up a Data Dcience Environment on Linux.
categories: [markdown]
title: Setting Up a Data Science Environment on Linux
---

# Setting Up a Data Science Environment on Linux

This article is a quick guide showing how to setting up a minimal Linux environment for your Data Science projects.

You should be familiar with the most usual bash commands for navigating thourgh your file structure and to install programs.

Here is what I will cover in this guide :

1. The terminal with zsh
2. The Python programming language
3. The conda virtual environment
3. th VS code editor
4. The Jupyter notebook
5. The git and Github version control
6. The Cookiecutter Data Science project organization

Then, I will conclude with a simple and typical workflow to follow when starting a new Data Science project.

## The terminal with zsh

A terminal is used to interact with your computer via text. 

The terminal we’re going to be setting up is zsh, and specifically the Oh My Zsh framework.

To install the Oh My Zsh framework, you have to first install a zsh terminal :

```shell
sudo apt install zsh
```

You have to exit out of your terminal and open it up again for the changes to take effect.

To verify the zsh installation, simply run :

```shell
zsh --version
```

Then, to install Oh My Zsh, copy-paste the command into your terminal:

```shell
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Exit out of the terminal and open it back up again. We're done !


## The Python programming language

If you're there you know some Python. So this part will be short. 

Here, I recommend to install a new version of Python using Miniconda. 

Go to the Miniconda home page and download either the “Miniconda3 Linux 64-bit” or “Miniconda3 Linux 32-bit” installer for Python 3.8.

Open up a terminal and navigate to where you downloaded the file.

Then run :

```shell
bash Miniconda3-latest-Linux-x86_64.sh
```

Close your terminal and re-open, then run :

```shell
conda env list
```

You should get a short list printed out.

Finaly, check which Python is your default :

```shell
which python
```

You should see a path printed out that has “miniconda” in it. We're done !

## The conda virtual environment

A good Data Science practice is to basically separate installations of Python that have their own set of packages that they have access to.

This means each project you work on can have its own set of packages, and you don’t have to worry about your projects having conflicting package requirements.

Using conda to create a virtual environment :

Run this command to create a new conda environment named “ds-projects” with pandas installed :

```shell
conda create -n ds-projects pandas
```

If you run conda env list again, and you should now see “ds-projects” listed.

To Activate your conda virtual environment, simply run :

```shell
conda activate ds-projects
```

You are now using a new virtual environment to work in. 

Hence, you can install a new package (seaborn for example) with the command :

```shell
conda install seaborn
```

To deactivate your conda environment :

```shell
conda deactivate
```

Finallly, you can remove your virtual environment by running :

```shell
conda remove --name ds-projects --all.
```

It’s a best practice to create a new virtual environment for each project that you work on.


## th VS Code editor


The VS Code editor is popular among data scientists and developers. It has very useful functionality right out of the box with all of the features you would expect like multi-line select, an integrated terminal, and debugging tools.You can use extensions to make it as powerful as you need it to be.

Installing VS Code is very easy. Simply go to the VS Code website, click “Download”, and install using the instructions.

To use it, open up a terminal. Type :

```shell
code .
```

Find the “extensions” icon on the left-hand bar and click it. You should see a search bar where you can search for extensions.

Search for a Python extension (you can just search “python”), and install it.

If you're new to VS Code, I suggest to familiarize yourself with by creating a file structure, a Hello World Python program that you will run in the integrated terminal.


## The git and Github version control

A best practice is to create a new git “repository” for each project you work on. 

A git repo is simply where all of your code for a project lives.

To install it, simply type :

```shell
sudo apt install git-all
```

Exit your terminal and open a new one.

Then, run git --version to ensure that the install worked correctly

In your terminal, run these two lines to configure your git for the first time so that git knows who you are :

```shell
git config --global user.name "Your Name Here"
```

```shell
git config --global user.email youremail@example.com
```

Create a project with some code to use with our first git repo.

For example, create such a file structure :

README.md
.gitignore
test_script.py

Initialize a git repo for your project, and take a snapshot (“commit”) of your code.

Run git init in your terminal to initialize a git repository in your project directory.

Run git add . in your terminal, which adds all of the files in the current directory to the “staging” area of git.

Run git commit -m "First commit."

GitHub Usage Instructions :

Create a GitHub account.

Create a repo on GitHub.

Push your code to GitHub.

Your code and commits are now safely stored on GitHub.

## The Jupyter notebook

Jupyter notebooks have become incredibly popular with data scientists over the last few years, and for good reason—they’re a great way to analyze data, run some experiments, and document your results in a way that others can follow along with. With notebooks, you create individual cells where you can either write and run Python code, or write Markdown code to document your findings.

Create a new conda environment.

In your terminal, run :

```shell
jupyter notebook
```

You should see some text printed to the console telling you that Jupyter notebooks is starting up and running.

Create a new notebook and play around with it. We're almost done !

## The Cookiecutter Data Science project organization


Cookiecutter Data Science is essentially a template project directory that you can use when you start new data science projects. 

A good suggestion for starting out is to just use the main directories that scripts that you need. 

A good starting place is to only use the “data”, “notebooks”, and “src” folders.

To install via conda, run this command in your terminal :

```shell
conda install -c conda-forge cookiecutter
```

Use cookiecutter to download and create a data science project template :

```shell
cookiecutter https://github.com/drivendata/cookiecutter-data-science
```

Delete anything you don’t want.

## A typical workflow for a Data Science project 

1. Open up your terminal.

2. Create a new conda environment for your project :

```shell
conda create -n my-project-env pandas jupyter scikit-learn matplotlib seaborn
```

```shell
conda activate my-project-env
```

3. Create a new project directory using cookiecutter :

```shell
cookiecutter https://github.com/drivendata/cookiecutter-data-science
```

4. Open up your new project directory in VS Code :

```shell
code my-project-directory
```

5. Open up a terminal in VS Code, initialize a new git repo, and take a first snapshot.

```shell
git init
```

```shell
git add .
```

```shell
git commit -m “First commit.”
```

6. Create a new repo on GitHub, then follow the instructions to push your code from your computer project directory to that repo :

```shell
git remote add origin https://www.github.com/yourname/your-repo-name.git
```

```shell
git push origin master
```

And now you’re ready to go for your next data science project.

Happy coding !