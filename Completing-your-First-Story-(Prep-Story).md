# Completing your First Story (Prep Story)

The first story for every student will be to sign their name to our signin file. You will also need to include the collection/hobby you want to work with.

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




