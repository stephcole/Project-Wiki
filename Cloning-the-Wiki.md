#After your Live Project
___
After your time on Live Project is complete, you will still have the project on your device. You will be able to continue working on your App and add more detail, polish, and complete any stories you didn't get to during your 2 week sprint.

You are able to take this wiki and it's resources with you. To do so, follow these steps.


# 1. Navigate to the Wiki
    - Click the three dots to the right.
    - Select "Clone wiki".
    - Copy the URL provided.
    - You may need to "Generate Git credentials" so leave this page open.
# 2. Open GitHub Desktop
    - Click "Current Repository" -> "Add" -> "Clone repository..."
    - Click to the URL tab
    - Paste the Wiki's URL then click the blue "Clone" button
    - You may be prompted for credentials. If so, click the "Generate Get credentials"
    - Paste the username and password to continue

#The Result
___
The wiki will be downloaded to the folder specified. Each 





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