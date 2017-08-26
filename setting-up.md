# Setting up

Here is what we'll do:

1. Set up Python (Install Anaconda (actually miniconda) and necessary packages)
2. Set up Spark2
3. Configure Spark, findspark and pySpark

Note: The instructions have been tested only on Ubuntu and OS X. Please raise a issue if you hit any snags on your windows system.

---

# Set up Python

## Install Anaconda

From the Anaconda [docs](http://conda.pydata.org/docs):

> Conda is an open source package management system and environment management system
for installing multiple versions of software packages and their dependencies and
switching easily between them. It works on Linux, OS X and Windows, and was created
for Python programs but can package and distribute any software.

## Overview

Using Anaconda consists of the following:

1. Install [`miniconda`](http://conda.pydata.org/miniconda.html) on your computer
2. Create a new `conda` [environment](http://conda.pydata.org/docs/using/envs.html)
3. Each time you wish to work, activate your `conda` environment


## Installation

**Download** the version of `miniconda` that matches your system. Make sure you download the version for Python 3.x (3.6 is the latest at the time of writing).

|        | Linux | Mac | Windows |
|--------|-------|-----|---------|
| 64-bit | [64-bit (bash installer)][lin64] | [64-bit (bash installer)][mac64] | [64-bit (exe installer)][win64]
| 32-bit | [32-bit (bash installer)][lin32] |  | [32-bit (exe installer)][win32]

[win64]: https://repo.continuum.io/miniconda/Miniconda3-latest-Windows-x86_64.exe
[win32]: https://repo.continuum.io/miniconda/Miniconda3-latest-Windows-x86.exe
[mac64]: https://repo.continuum.io/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
[lin64]: https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
[lin32]: https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86.sh

**Install** [miniconda](http://conda.pydata.org/miniconda.html) on your machine. Detailed instructions:

- **Linux:** http://conda.pydata.org/docs/install/quick.html#linux-miniconda-install
- **Mac:** http://conda.pydata.org/docs/install/quick.html#os-x-miniconda-install
- **Windows:** http://conda.pydata.org/docs/install/quick.html#windows-miniconda-install


---

## Install necessary packages

**Setup** the `bdap` environment.

```sh
git clone https://github.com/soumendra/learn-spark-python.git
cd learn-spark-python
```

> You should already have a `GitHub` account, and should have installed `git` in your system to be able to clone the repo in the last instruction. If not, [you can download the repository here](https://github.com/soumendra/learn-spark-python/archive/master.zip), extract the folder, `cd` into it,  and then continue.

If you are on Windows, **rename** `meta_windows_patch.yml` to `meta.yml`.

**Create** `bdap`.  Running this command will create a new `conda` environment that is provisioned with all libraries listed above.
```
conda env create -f bdap.yml
```


**Verify** that the `bdap` environment was created in your environments:

```sh
conda info --envs
```

**Cleanup** downloaded libraries (remove tarballs, zip files, etc):

```sh
conda clean -tp
```

## Uninstalling

To uninstall the environment:

```sh
conda env remove -n bdap
```

## Using Anaconda and Jupyter Notebooks

Now that you have created an environment, in order to use it, you will need to activate the environment. This must be done **each** time you begin a new working session, i.e., open a new terminal window.

**Activate** the `bdap` environment:

### OS X and Linux
```sh
$ source activate bdap
```

### Windows
Depending on shell either:
```sh
$ source activate bdap
```

or

```sh
$ activate bdap
```

That's it. Now all of the `bdap` libraries are available to you. You can start a Jupyter Notebook with:

```sh
jupyter notebook
```

To exit the environment when you have completed your work session, simply close the terminal window.


## Jupyter Notebook Basics

* [Get started with IPython](https://www.youtube.com/watch?v=j08Ry-8MOxM) (ignore the sections on installation)
* You should understand the following concepts:
  - Managing Cells
     * Cell Types
     * Moving Cells around
     * Executing and Creating New Cells
  - Handling Notebooks
     * Creating new notebooks (with different kernels)
     * Exporting notebooks to various formats
  - IPython Kernels
  - Keyboard Shortcuts

IPython Homepage: https://ipython.org/

## Just enough Markdown for Jupyter Notebooks

* [What is markdown?](https://help.github.com/articles/markdown-basics/)
* [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/) (used by IPython)

Here are some examples of markdown in action (edit this cell to see the raw text)
* Styling Text
    - *italicised*
    - **bold**
    - ***italicised and bold***
    - **styles _mixed_ together**
* Unordered lists
  - Nested Unordered Lists
  1. Ordered Lists
    1. Nested Lists
    2. More Nesting
      * More nested lists
* Writing Code Blocks
```R
x = 0
x = 2 + 2
hist(rnorm(1000))
```


---

# Set up Spark

## Install Java

Check if `Java` sdk is installed in your system. If not, follow the following instructions (for Ubuntu only, mac folks can do `brew install java` and windows folks can just download and execute the binary)

```bash
sudo apt-get update
sudo apt-get -y upgrade
```

```bash
sudo apt-get install -y software-properties-common curl
sudo apt-get install default-jre default-jdk
```

## Java Alternative (optional)

 
* **Please note that Java was installed in the last section, and don't actually need to go through this section to install Java.**
* **This is for adventurous students who wish to install the jdk/jre from Oracle (if you don't know what I am talking about, you don't need to do it.**

```bash
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update

sudo apt-get install oracle-java8-installer
```

If the Oracle version is the only one you have installed, then you have only one Java framework installed i your system. Otherwise, if you have multiple Java frameworks installed in your system, you can choose one of them with the following:

```bash
sudo update-alternatives --config java
sudo update-alternatives --config javac
```

And here is how you can set up your JAVA_HOME

* Note in the install path from (the command above)
        sudo update-alternatives --config java
* Add JAVA_HOME="YOUR_PATH" to /etc/environment
        source /etc/environment
        echo $JAVA_HOME
        
## Configuring Spark, findspark and pySpark

```bash
source activate bdap
```

After executing that in the terminal, follow the instructions in [these slides](http://nbviewer.jupyter.org/github/soumendra/spark_machine_learning_tutorial/blob/master/Slides/Spark02-%20Setting%20Up%20Spark%2C%20PySpark%20and%20Notebook.pdf).

---

# Git and GitHub (optional)

* Signup for an account in https://github.com/ (remember your github username and password)
* [Setup GitHub](https://help.github.com/articles/set-up-git/) (setup your local *git* installation for GitHub)
```bash
git config --global user.name "YourName"
git config --global user.email "YourGitHubEmailId"
```
* Learn the basics of git
  - [Git the simple guide](http://rogerdudler.github.io/git-guide/)
  - [Set up Git in your machine](http://rogerdudler.github.io/git-guide/)
  - [Practise Git](https://try.github.io/levels/1/challenges/1)
  - [Comparing Git Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows/)
* [GitHub Workflow using web-ui](https://help.github.com/articles/create-a-repo/)
* (Optional) [Forking Repos](https://help.github.com/articles/fork-a-repo/) and [GitHub Fork Workflow](https://github.com/sevntu-checkstyle/sevntu.checkstyle/wiki/Development-workflow-with-Git:-Fork,-Branching,-Commits,-and-Pull-Request)
* (Optional) [Set up SSH authentication](https://help.github.com/articles/generating-ssh-keys/)

