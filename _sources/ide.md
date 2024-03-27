
# IDE's (interactive development environments)

This section will provide you with information on the recommended IDE's to use with the Python and R programming languages. Here we will cover their installation, setup and basic use.

## Python

### Visual Studio Code

VS Code is a robust IDE for working in Python. It has a wide variety of extensions that support python programming and integration with other languages and tools.

#### Installation

The easiest way to install VS Code is directly from the website <https://code.visualstudio.com/Download>

#### Setup

When you start using VS Code you will want to install some core extensions for working with Python. These are:
- Python (which should also install Pylance)
- Jupyter (which will install several related Jupyter extensions)

#### Basic usage

- Start by opening the folder for the project you are working on. This might be a git repo or an empty project folder
- Setup a virtual environment. Virtual environments make it easier to manage the package dependencies for a project during development and deployment
- To initialise a new virtual environment:
    1. Ensure you have opened the project folder you are working on. The virtual environment data (.venv) will be stored here
    2. Open a new terminal in VS Code by going to the tool bar at the top, clicking on 'Terminal', then selecting 'New Terminal' from the dropdown. This will open a new terminal at the bottom of the window
    3. Open the command palette by pressing cmd + shift + P
    4. The command palette will open at the top of the window
    5. Start typing 'Python: Create Environment' and select this option
    6. From the dropdown select the environment type venv
    7. Select a Python interpreter version
    8. You will see in the terminal that the current location is preceded by (.venv)
- To initialise an existing virtual environment
    1. Open the project folder (likely a git repo you have cloned)
    2. Open a new terminal in VS Code by going to the tool bar at the top, clicking on 'Terminal', then selecting 'New Terminal' from the dropdown. This will open a new terminal at the bottom of the window
    3. In the terminal type `source 'name_of_virtual_environment'/bin/activate` the name of the virtual environment will likely be venv unless otherwise specified
    4. Open the command palette by pressing cmd + shift + P
    5. The command palette will open at the top of the window
    6. Start typing 'Python: Select Interpreter' and select this option
    7. From the dropdown select the Python interpreter specified in the virtual environment. This can be found in the 'name_of_virtual_environment'/bin folder
- Installing packages in your virtual environment
    - To install new packages to your virtual environment simply go to the terminal and type pip install 'package_name'
    - The package name to be used at installation can easily be found by googling something like 'Python pip install pandas'
    - You can also specifiy a specific version of a package if necessary otherwise the latest stable version compatible with you version of Python should be installed

#### Resources

VS Code Python tutorial <https://code.visualstudio.com/docs/python/python-tutorial>

## R

### R base and R Studio

#### Installation

To you R with R Studio, you need to first install R base then install R Studio. R Studio will then automatically locate R base if installed in this order.

- Go to <https://cran.r-project.org/bin/macosx/>, download the base R version suitable for your Mac chipset, either Intel or M1/M2 and install
- Go to <https://posit.co/download/rstudio-desktop/>, download R studio and install

#### Setup

R Studio should work straight out of the box. It has a built in package manager function that allows you to easily install packages such as shiny, tidyverse, psych, dplyr, ggplot etc.

#### Basic usage

The main thing to note when using R is to ensure that you set your working directory. This is done using the `setwd()` function or can be manually set within the IDE in the file explorer.

#### Resources

- The R for healthcare website which has useful information on getting started with R and R studio <https://rforhealthcare.org>
