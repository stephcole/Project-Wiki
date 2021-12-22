[[_TOC_]]
# General Questions:

## 1.  Who do I email my daily update email to? 
-The live project director at liveprojectdirector@learncodinganywhere.com

## 2. What are the minimum stories required to pass the live project?
-Four stories total and the prep story.

## 3. When are the live project instructors available?
-Monday-Friday from 10am - 6pm Pacific standard time. 

# Version Control Questions:

## 1. Where did my changes go? I created a new branch and now my changes from my previous story aren't in my new branch.
-This occurs when a new branch has been created before an instructor has had time to merge your previous branch into the master branch. There are two ways to approach this. One way is to merge your previous branch into your current branch or wait until an instructor has merged your previous branch into the master, keep in mind we are not here all the time, so don't feel the need to have to wait. Here are instructions for the first approach(merge the previous branch into the current branch):
[Tutorial](https://www.youtube.com/watch?v=v-ZsZPAUg9k)

## 2. When should I update my master branch?
  -Updating your master branch is important to do to prevent merge conflicts. Good practice would be to update the master branch at least every time you start your new story. 
## 3. What should I do when I have a merge conflict after I created my pull request?
 -Merge conflicts are common, so no need to worry. Instructors can take care of a merge conflict for you, just let us know. If you feel comfortable enough to try it out your self here is a step-by-step walkthrough on how to solve a merge conflict. 
[Merge Conflict Resolution](https://docs.google.com/document/d/1sm7MpKOSeVj1jdmvpVM80Hv1g7iqqqu8EFQT2nRFF1o/edit?usp=sharing)
## 4. What do I do if I forgot to create a new branch for my story card and all my changes were made on my previous story branch? 
-You would still need to create a new branch for your story card. Every story requires a new branch. In this instance, you would need to create a new branch within your story card. Once you do this go over to pycharm and you would need to follow the steps that can be found in the image for question 1. 
## 5. Why can't I commit and push my changes?
-Most of the time when you get an error when trying to commit and push your changes up, this problem comes back to the branch you are working on. Make sure you are not on the master branch trying to commit and push your changes up. You might need to save your code on notepad++ and paste it into the correct branch(not the master branch). Now you should be able to commit and push your changes up. It is always good practice to make sure you are in your working branch. Working on the master branch is not acceptable in the tech industry. However, if you are on your working branch and are getting an error when trying to commit and push your changes up, go ahead and reach out to an instructor on this issue. 

# Live Project Questions:

## 1. How do I start the process of creating my app, where do I even start?
-Make sure you are within the AppBuilder9000 directory and run the following command: 
python manage.py startapp nameofyourapp
this command will get you started.
## 2. Where should my virtual environment be located?
-It should be located outside of the project folder. For example, if your path looked like this:
![2021-10-27 11_40_39-Window.png](/.attachments/2021-10-27%2011_40_39-Window-94e59c83-b6c0-4b3d-9239-443377ee7932.png)
Then the virtual environment would need to be located in the PycharmProjects directory.
## 3. Why can't I run any manage.py commands?
-For this, you would want to make sure you are in the correct directory in which the manage.py file is located.
## 4. How long should I be working on a roadblock before I reach out for help?
-This is dependent on each person, however, we recommend giving yourself about an hour trying to debug the issue and/or doing research. If you don't know where to start in the process of debugging, go ahead and reach out to an instructor we can help point you in the right direction! Also, it is perfectly acceptable to clarify with an instructor exactly what kind of help you are looking for, have that be hints, resources, jumping on a screen-share, etc.
## 5. I accidentally made changes to another student's file and now it's in my commit window.
-There is a rollback feature on pycharm that will undo changes that you made to a file. You would want to select the file you are wanting to undo changes to. Make sure you don't have files selected that you wouldn't want to lose changes to.
![2021-10-27 13_04_12-Window.png](/.attachments/2021-10-27%2013_04_12-Window-a8854bcb-718b-40e9-be56-03d3ecaebdc9.png)
## 6. Why are some of my files red?
![2021-10-27 13_50_29-Window.png](/.attachments/2021-10-27%2013_50_29-Window-cf091720-ba6c-4727-bce0-0550351b8ce0.png)
-This means your files are untracked. You would want to add these files into the VCS(version control systems). To do this go over to your commit window and look within the unversioned files and add to VCS:
![new3.png](/.attachments/new3-1319356c-3340-45ef-b478-6591ddbb873e.png)
How do I prevent this from occurring again?
When you create a new file you will get a window pop-up. It will look something like this, see the image below:
![2021-10-27 13_15_06-Window.png](/.attachments/2021-10-27%2013_15_06-Window-d3492c34-eb77-4320-b3dd-e1b82e74ddc9.png)
You would want to add file to git, that file will now be tracked. The reason your file ended up untracked could be because cancel was clicked instead of add.
## 7. Where can I find an API?
-There are some websites where you can find API's, here is a shortlist of some:
(https://github.com/public-apis/public-apis)
(https://rapidapi.com/)


