# LITERATE ECONOMIC DATA ANALYSIS

The name of this workshop is inspired in Donald Knuth's conceptual use of *literate programming*, defined as a script, notebook, or computational document that contains an explanation of a program's logic in a natural language, interspersed with snippets of macros and source code, which can be compiled and rerun. An executable paper!

As economic analyst/researchers our main weapon/programming tool to produce these analysis are primarily Stata and R, though some of us may be equally familiar with other programming tools such as Julia, Python, C, and the list goes on. Regarless of our preferred tool, matter which literate programming tool you use, only run the cells from top to bottom – ONLY. The number 1 cause of irreproducible jupyter notebooks is that the original authors run the cells out of order, which can't be reproduced without documentation about which cells in which order. So run your literate programming notebooks from top to bottom only.

Jupyter Notebooks
Jupyter Notebook is an interactive computing environment that enables users to author notebook documents that include code, interactive widgets, plots, narrative text, equations, images and even videos! Jupyter notebooks are heavily used in data science, and it would behoove you to get comfortable with the tool. The jupyter name comes from 3 programming languages: Julia, Python, and R. You can use one programming language per document, and it is done through choosing a kernel (e.g. Python, R, Go, and more -- get the full list of kernels from the wiki).

Jupyter notebooks can be comprised mainly of two types of cells (though more can be added with plugins).

Markdown Cells (for narratives): when run, a markdown cell will display markdown or HTML that you write (that means all sort of rich content, including images). Essential markdown summary: https://daringfireball.net/projects/markdown/syntax
Code Cells (for data cleaning, analysis, visualization, etc.): executable code in a variety of languages, dictated by the kernel (default is Python, but more can be added).
Some key jupyter notebook shortcuts to keep in mind while you work:

Use shift + enter to run an active cell

Use esc in highlighted cell to toggle command options:

esc + L - show line numbers

esc + M - format cell as Markdown cell

esc + a - insert cell above current cell

esc + b - insert cell below current cell

Check all current variables: run %whos from a code cell

RMarkdown
RMarkdown is another popular literate programming tool and can be considered an extension of Markdown. Like all literate programming tools, it  mixes documentation & code, and not just R code either! You can insert code snippets from other languages (SQL, bash, Python, etc.) into ONE DOCUMENT! Incorporating results directly into your documents is an important step in reproducible research. Any changes that occur in either your data set or the analysis are automatically updated in your document the next time the document is created.

Typically, RMarkdown files are edited from within RStudio. The R for Data Science book contains a great chapter on RMarkdown for more information: https://r4ds.had.co.nz/r-markdown.html.


## Quickstart

### Prerequirements

To adequately follow through the Workshop, you must have:

+ Python and Stata installed in your machine,
+ Some experience working with the command line,
+ A GitHub account.

If you do not meet the minimum prerequirements, the Worshop will prove a bit more difficult than expected. Please take sometime before our Workshop to fulfill these prerequirements and be ready to go. During our workshop we might take 10 minutes at most to ensure everyone is ready to go. However, to To help you get up to speed with the prerequirements, please read the instructions and links provided in the following links:



#### Github

GitHub is a code hosting platform for version control and collaboration, widely use to work together on projects from anywhere.


If you do not have a github account, please make sure to follow [these](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account) instructions to create a new github account. 


##### OS X


Python is probably already installed on your system. To check if it’s installed, go to Applications > Utilities and click on Terminal.

On

Find out which version of Python is installed by issuing the command python --version:
Install Python with Homebrew

Homebrew is a package installer.


* Python installed in our systems

Install Python with Homebrew

Homebrew is a package installer.

First, install Homebrew.

```{bash}
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Then, install brew to Path:

```{bash}
$ export PATH="/usr/local/opt/python/libexec/bin:$PATH"
```

Next, install Python.

```{bash}
brew install python
```

##### Ubuntu Linux machines.

To see which version of Python 3 you have installed, open a command prompt and run

$ python3 --version
If you are using Ubuntu 16.10 or newer, then you can easily install Python 3.6 with the following commands:

$ sudo apt-get update
$ sudo apt-get install python3.6
If you’re using another version of Ubuntu (e.g. the latest LTS release) or you want to use a more current Python, we recommend using the deadsnakes PPA to install Python 3.8:

$ sudo apt-get install software-properties-common
$ sudo add-apt-repository ppa:deadsnakes/ppa
$ sudo apt-get update
$ sudo apt-get install python3.8
If you are using other Linux distribution, chances are you already have Python 3 pre-installed as well. If not, use your distribution’s package manager. For example on Fedora, you would use dnf:

$ sudo dnf install python3
Note that if the version of the python3 package is not recent enough for you, there may be ways of installing more recent versions as well, depending on you distribution. For example installing the python3.9 package on Fedora 32 to get Python 3.9. If you are a Fedora user, you might want to read about multiple Python versions available in Fedora.

###  Setup Instructions

Now, we are ready to go.

#### 1. Fork/Clone repository

#### 2. Set up virtual enviroment

1. Install virtualenv in your machine. If your machine has a linux-based operating system, run:

```
pip install virtualenv
```

Else, 

```
sudo apt-get install python-pip
```

2. Create a Virtual Python Environment

Locate yourself on your project directory and run virtualenv to create the new virtual environment.

```
cd literate-economic-analysis
virtualenv econ-repr
```

3. Activate the Environment

Now that we have a virtual environment, we need to activate it.

```
source econ-repr/bin/activate
```

After you activate the environment, your command prompt will be modified to reflect the change.

4. Add Libraries and Create a requirements.txt File

After you activate the virtual environment, you can add packages to it using pip. You can also create a description of your dependencies using pip.

The following command creates a file called requirements.txt that enumerates the installed packages.

```
pip freeze > requirements.txt
```

This file can then be used by collaborators to update virtual environments using the following command.

```
pip install -r requirements.txt

```

Deactivate the Environment. To return to normal system settings, use the deactivate command.

```
deactivate
```

#### Launch Jupyter Notebook

First, make sure we have Jupyter Notebook installed in your machine. If not installed, [please install](https://jupyter.org/install).

```
pip install jupyterlab
```

Add the virtualenv you've cretead in the previous step as a jupyter kernel.

```
ipython kernel install --name econ-repr --user
```

Once installed, launch JupyterLab with:

```
jupyter-lab

```


#### Quick-off

##### PyStata

```
pip install pystata
```

```
pip install stata_setup
```

open stata_setup and change line 45 with "config.init(edition)"

In Stata, enter the following command to locate the folder containing Stata 17 : display c(sysdir_stata)

pip install --upgrade --user stata_setup


If you use Windows, it is probably C:\Program Files\Stata16\ado, but it might be someplace else. If you use Mac, it is /Applications/Stata/ado. That is, it is the ado folder in the official Stata folder. If you use Unix, it is /usr/local/stata16/ado.

First of all, you need to install the Anaconda Prompt (conda). Tou have to follow the instructions on the conda website: https://conda.io/projects/conda/en/latest/user-guide/install/windows.html.

Then, you have to install the jupyter notebook. The instructions are available on their website: https://jupyter.org/install.

In a third step, you have to install PyStata: https://www.stata.com/python/pystata/install.html.

In Stata, enter the following command to locate the folder containing Stata 17 : display c(sysdir_stata)

The software is in this folder 'C:\Program Files\Stata17/' in my case and I use the standard edition.

In conda, install PyStata : pip install --upgrade --user stata_setup

Lastly, you have to install the matplotlib library for an illustration with a 3D graph: https://matplotlib.org/stable/users/installing.html

In conda, you can type:

python -m pip install -U pip

python -m pip install -U matplotlib

Now, you are ready to launch Stata from the Jupyter Notebook.

Lastly, you have to install the matplotlib library for an illustration with a 3D graph: https://matplotlib.org/stable/users/installing.html

In conda, you can type:

python -m pip install -U pip

python -m pip install -U matplotlib

Now, you are ready to launch Stata from the Jupyter Notebook.


##### Stata Jupyter Kernel¶
There is also excellent documentation available.
The Stata Jupyter Kernel enables using stata directly in jupyter notebooks.

It is effectively an alternative interface to use stata if you like jupyter as an interface.

This can be useful if you want to write notebooks that are integrated with stata code.

It supports a wide range of interaction with stata

To install using anaconda tools you can use the following commands in a jupyter notebook:

Tip
It is important to specify -y when issuing install requests via conda as there is no way to accept the user requested y input to proceed with install. pip doesn’t have this issue as it doesn’t request user input.
!conda install -y -c conda-forge stata_kernel
Copy to clipboard
once the software is installed you need to install the jupyter kernel on your computer

!python -m stata_kernel.install
Copy to clipboard
Warning
[macOS] When I ran the kernel install step I got the following error:

Cannot import kernel
Installing Jupyter kernel spec
WARNING: Could not find Stata path.
Refer to the documentation to see how to set it manually:

https://kylebarron.dev/stata_kernel/using_stata_kernel/configuration
Copy to clipboard
and had to manually set the stata path in the .stata_kernel.conf file located in your home directory to the following:

# Path to stata executable. If you type this in your terminal, it should
# start the Stata console
stata_path = /Applications/Stata/StataIC.app/Contents/MacOS/StataIC

# **macOS only**
# The manner in which the kernel connects to Stata. Either 'console' or
# 'automation'. 'console' is the default because it allows multiple
# independent sessions of Stata at the same time.
execution_mode = automation
Copy to clipboard
Unfortunately StataIC is limited on mac os so I had to use automation instead of console as per this issue in the docs However this does enable the use of browse
If you start jupyter notebook you should now see a stata kernel option. If selected a jupyter notebook will open with a connection to stata. You can verify this on the top-right of the notebook

References:
https://kylebarron.dev/stata_kernel/
https://quantecon.github.io/2021-workshop-rsit/week2/session7/stata-and-jupyter.html