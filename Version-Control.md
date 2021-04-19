[[_TOC_]]

#Version Control Basics

A version control system is based around one main concept, tracking changes that happen within directories. Version control is critical for today's development teams.  Having a good version control system in place helps teams in many ways:
- File names and project structure are consistent among team members
- Changes can be made with confidence, as they can always be reverted
- Can easily deploy different versions of the code for testing
- Helps teams to understand who made what changes and why
- Helps teams to collaborate from anywhere in the world
- Helps accelerate product development

#Basic Workflow for Clean Version Control

See [this diagram](https://drive.google.com/file/d/1Tvwnru1X8jOcKuXz_wCfuD9e52a_u4KQ/view?usp=sharing) as reference for these steps.

##1. Pull the most recent master

- Every morning, make sure you are pulling the most recent master so you have all the most recent updates. This will reduce conflicts with others team members' code, and it will make sure that you're seeing the same thing that the project manager is seeing on their local branch. If you don't have the same code, you may be missing something that is crucial to your story, or not know that a piece of it has already been solved, and waste time trying to solve it. 

##2. Create a Working Branch

- You never want to make changes directly to the master branch. The master branch should only ever contain fully tested and verified code. When you make changes to your local master you can mess it up, and that's considered a broken master. You can't make progress if your master branch is broken. To prevent this from happening, you create a "working branch" to make your edits and test the code. When you've finished making changes, you can then update your master branch with those changes.  

- Once your local master branch is updated with your changes, you can then pull that code into the remote master branch using a pull request. The Live Project Director will approve or disapprove the pull request after reviewing the edits. Not all pull requests will be accepted as part of a master branch. This can be because the code isn't what the project manager is looking for, or because there are bugs, errors, or the project has changed direction. For this reason, it is important to always create a working branch off the most recent master and not include any of your previous code in a new working branch. 

- (The only exception to this is when you are working on a story that builds upon the previous one and you need that code to complete your task. In that case, you should still make a new working branch, and merge the most recent master branch into it. That way if the branch for the second story has any issues, the branch for the first one is not corrupted.)

##3. Make Your Edits:

- This step seems fairly straightforward, but it can also be a tricky spot to be in. If you just stay on your working branch, and focus on your own edits, then there are no version control issues. But the reality is in a fast moving environment, you will need to be pulling the most recent master and updating your local branches, and possibly be switching between stories as code is sent back for edits. Not handling this properly can cause lots of issues. 

- Make sure every time you are going to switch branches that you save and commit the code you've been working on before you switch branches. If you don't you may accidentally apply your edits to the branch you are switching to. If you do accidentally apply edits to the wrong branch, make sure to undo the changes as soon as you notice it using "git revert". If you are worried about losing code you've created in this process, copy the code and paste it in a text file so you can reference it and re-apply it if that code is lost. If you've committed changes you didn't mean to commit, make sure to revert or reset that commit.

##4. Merge Master into Working Branch:

- The final step that needs to be performed before code can be added into the master branch is to bring the working branch current with the master and resolve any conflicts. Conflicts are a natural part of group projects, and resolving them means paying careful attention to what code is being overwritten. The steps for this process:
   1. Save and commit your final changes to your working branch
   2. Switch to the Master branch (aka checkout the master)
   3. Pull the most recent remote master branch (update project)
   4. Switch back to your working branch
   5. Merge the master branch _into_ your working branch
   6. Resolve any conflicts
   7. Check that your branch still works properly (this includes being able to run migrate)

- If you are not comfortable with the conflict resolution process at this time, your instructor will handle it, just abort the merge when conflicts occur. You will likely need to learn this skill on the job.

##5. Push Branch and 6. Pull Request:

- Once you have your working branch up to date with the master and working the way you want, you submit your work by pushing that branch to the remote server and creating a pull request. This nomenclature can be confusing. Just remember that you push up and pull down or pull into. The pull request is a request that your code be pulled into the master branch, and your instructor will pull your branch to check your work. 

#Other Notes:
- Once you've made a pull request for one story, you'll probably want to immediately start on another one. To get the commits you made on your previous branch to show up on your new branch, you'll want to merge from your previous branch into your new working branch. 
[Here's a short video explaining the process](https://youtu.be/v-ZsZPAUg9k)
- Cloning refers to the very first time you pull the master branch from the remote server. Re-cloning means deleting the entire project and cloning it again.

- To reduce switching back and forth between branches, utilize the remote repositories to view existing code. You can't run the code from the repository, but you can at least compare the actual code.

- Many stories you work on will take multiple days. Get in the habit of pulling the most recent master at least once a day, or more for very fast moving projects, and merging your master into your working branch. This will reduce the overall number of conflicts and make them easier to resolve. 

- Be sure you are not making edits to the master branch. If you've found you are making edits to it, you'll need to apply those edits to your working branch. If you forgot to make a working branch, just make a new one based off the current master and then revert the changes on the master. If you have a working branch and have not committed your changes to the master, you can stash those changes and then use those changes after you've switched to your working branch.

- If you ever corrupt your master beyond repair, you can always switch to any working branch, delete your master branch (it will only delete the local), and then checkout the master branch again. This will pull the remote master for you to checkout and reset your system.

- You can use the remote repository to store a version of your working branch at any time by committing your changes and pushing the branch to the server. This is also how you can ask your instructor to review your code.

- For merging the master into your working branch and resolving merge conflicts, we've created [this tutorial](https://docs.google.com/document/d/1sm7MpKOSeVj1jdmvpVM80Hv1g7iqqqu8EFQT2nRFF1o/edit?usp=sharing)

For more documentation on PyCharm version control, [look here](https://www.jetbrains.com/help/pycharm/settings-version-control.html)

