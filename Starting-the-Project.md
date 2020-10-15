[[_TOC_]]

# Cloning the Project:
- To start, you're going to need to clone the project onto your own computer.
    - In Azure DevOps, navigate into "Repos" and then into "Files"
    - Click "clone" in the upper right hand corner and copy the URL to your clipboard.
    - Open up PyCharm, close any existing project
    - Click "Check out from Version Control" and select Git from the menu
    - Paste the URL from Azure into the URL input
    - Generate Git credentials if needed
    - Click the "Clone" button


# Starting a new Django project:

- _First_ — Create a virtual Environment
  - You should always create a virtual environment when using Django
    - 'venv' allows you to have a virtual installation of python and packages on your computer
     - This is important because python packages get updated often and these changes can mess up backwards compatibility
      - You can create different virtual environments to test out different versions of packages on your project
    - If using venv, activate it before running any commands
  - To create a virtual environment using venv:
    - Navigate to a folder outside your current project
    - command: _python -m venv [name-of-virtual-env]_
    - Be sure to activate the virtual environment before running any other commands!

- _Second_ — Make sure we have the latest version of pip, the software that we use to install Django:
    - command: _python -m pip install --upgrade pip_
- _Third_ — Run the requirements.txt file
    - A requirements file keeps a list of dependencies to be installed for a project
    - To install the requirements:
      - command: _pip install -r requirements.txt_

[Cloning and Setting Up the Project Demo](https://drive.google.com/file/d/1O7kLTby5iLOo9tAdMX0-SPLtfl1_OPqf/view?usp=sharing) - done on a Mac with instructions for PC.

=========== This is where you should get to before Sprint Planning =========
# Completing your First Story (Prep Story)

The first story for every student will be to sign their name to our signin file. You will also need to include 3 elements of your planned project with this sign in:
  - The collection/hobby you want to work with
  - A free API associated with this topic
  - A web page you want to pull information from

Below are the steps to complete this story. Remember these steps whenever you are choosing stories, creating branches, and creating pull requests.

[Sign In Story Demo](https://drive.google.com/file/d/1jtjKTZNbLiFrVS9bwg6WFI3ws3_4BXqa/view?usp=sharing) done on Mac with instructions for PC.

- Find your Sign-In story and move it into the Active column
- Create a new working branch 
    - From within PyCharm, navigate in the menus to VCS > Git > Branches > New Branch
        - Name your branch with initials-story#-SignIn convention
- Verify you're on the new branch before making changes
- Make local changes
    - Open project in PyCharm
    - Enter your name as a comment within the 'Sign In Sheet' (at the bottom of the files list), include information about your plan for your app
- Save changes to the Sign In Sheet
- Commit changes
    - Select Commit from the VCS menu
    - Write commit message
    - Click commit Button 
- Check all changes were committed
    - Check Event Log or use $ git status from terminal (should say Clean Working Tree)
- Push your branch to DevOps VCS > Git > Push
- Return to Azure DevOps to Create a Pull request
        - Go to Repos > Branches and locate your branch
        - Make sure there are commits ahead of the master
        - While hovering over your branch, click New pull request
        - Fill in Title, Description, and make sure your story item is attached under Work Item
        - Click Create
        - Ignore all options of clicking on the next page (do not approve, set for auto-complete, or abandon)
- Take Story # 1 and begin building your app within the HobbyTracker project!




