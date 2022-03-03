[[_TOC_]]

Welcome to the Python Live Project! You will need to complete these steps prior to the Sprint Planning session. Please read the steps below carefully.

#Web Development Students
_If you are a student on the **Web Development Live Project**, you will need to install [PyCharm Community edition](https://www.jetbrains.com/pycharm/download/#section=windows)(the IDE we will be using) and Python. Please take a look at [this document](https://docs.google.com/document/d/16qNrvX4t7KAhHU0q1Y6te-C0xo7IfOa-NzXpctCSN18/edit?usp=sharing) to install Python before proceeding with cloning the project._

# 1. Cloning the Project:
- To start, you're going to need to clone the project onto your own computer.
    - In Azure DevOps, navigate into "Repos" and then into "Files"
    - Click "clone" in the upper right hand corner and copy the URL to your clipboard.
    - Open up PyCharm, close any existing project
    - Click "Check out from Version Control" and select Git from the menu
    - Paste the URL from Azure into the URL input
    - Generate Git credentials if needed
    - Click the "Clone" button


# 2. Create a Virtual Environment
  - You should always create a virtual environment when using Django
    - 'venv' allows you to have a virtual installation of python and packages on your computer
     - This is important because python packages get updated often and these changes can mess up backwards compatibility
      - You can create different virtual environments to test out different versions of packages on your project
    - If using venv, activate it before running any commands
  - To create a virtual environment using venv:
    - Navigate to the parent folder of your current project
    - command: _python -m venv [name-of-virtual-env]_
    - **Be sure to activate the virtual environment before running any other commands!**
    - Getting an error when trying to activate your virtual environment? Try running this command:
      Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Unrestricted

# 3. Install Packages for the Project
- Make sure you have the latest version of pip, the software that we use to install Django:
    - command: _python -m pip install --upgrade pip_
- Next, run the requirements.txt file
    - A requirements file keeps a list of dependencies to be installed for a project
  - Navigate to the location of the requirements.txt file
  - To install the requirements:
      - Run the following command after activating your virtual environment.
      - command: _pip install -r requirements.txt_

# 4. Set the Python Interpreter
- Take a look at this document for more guidance in setting the  [Python Interpreter ](https://docs.google.com/document/d/1V_Tq9yoVGBVbyjLB3dn6FNG-ThEMO-l8MXtRNWWVqJs/edit)
     - In Pycharm, go to File > Settings > Project:Appbuilder9000 > Python Interpreter
  - Click on the gear icon next to the drop down menu for the Project Interpreter > Add
  - In Virtualenv Environment, select the radio button for 'Existing Environment' and click on the ellipsis '...'.
  - Navigate to your virtual environment's folder > Scripts > python.exe
  - Select the python executable file and click ok. 


[Cloning and Setting Up the Project Demo](https://drive.google.com/file/d/1O7kLTby5iLOo9tAdMX0-SPLtfl1_OPqf/view?usp=sharing) - done on a Mac with instructions for PC.

