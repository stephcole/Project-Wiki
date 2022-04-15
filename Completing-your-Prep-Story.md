# Completing your Prep Story

The first story for every student will be to sign their name to our signin file. You will be expected to complete this **after** attending the Sprint Planning session. You will also need to include the topic you want to work with.

---
# Branch Naming Conventions
For the sake of readability we have a naming convention to use for all your branches

Branch Naming Format:
XX-####-[short_title]

- XX = Your initials
- \#### = Work Item number
- [short_title] = short title of the Work-Item
---

Below are the steps to complete this story. Remember these steps whenever you are choosing stories, creating branches, and creating pull requests.

[Sign In Story Demo](https://drive.google.com/file/d/1jtjKTZNbLiFrVS9bwg6WFI3ws3_4BXqa/view?usp=sharing) done on Mac with instructions for PC.

1. Find your Sign-In story and move it into the Active column
2. Create a new remote working branch on Azure
    -  Open your story on the Board. 
    - Under 'Development', click on 'create a branch'
![image.png](/.attachments/image-52868905-e322-4837-aa5b-21553ba12a53.png)
     - Follow our branch naming convention outlined in [Project Overview](/Project-Overview): **[Your initials]-[story#]-[SignIn]** 
3. Checkout your branch on Pycharm
   - In Pycharm, check out the master branch and update project. This both updates the master branch as well as the list of remote branches on Pycharm.
   - You will now see your branch listed under 'Remote Branches'. Check out your branch.
   - Verify you're on the new branch before making changes
4. Make local changes on your branch in Pycharm
    - Scroll to the bottom of the the project files and folders in Pycharm. Open signin.html.
    - At the bottom of the list, enter your name and chosen topic for your app.
5. Commit changes
    - Select Commit from the VCS menu or click on the green checkmark on the Git toolbar to commit your changes
    - Write a short but descriptive commit message
    - Click 'Commit' button 
6. Check all changes were committed
    - Check Event Log or use $ git status from terminal (should say Clean Working Tree)
7. Push your branch to Azure DevOps 
   - Method 1: VCS > Git > Push
   - Method 2: Click on the green arrow in the top right corner of Pycharm
8. Return to Azure DevOps to Create a Pull request
        - Go to Repos > Branches and locate your branch
        - Make sure there are commits ahead of the master
        - While hovering over your branch, click New pull request
        - Fill in Title, Description, and make sure your story item is attached under Work Item
        - Click Create
        - Ignore all options of clicking on the next page (do not approve, set for auto-complete, or abandon)
- Take Story # 1 and begin building your app within the Appbuilder9000 project!




