[[_TOC_]]



## Planning your process
Planning is one of the most important parts of coding. This is how you make sure you understand how complicated the different requirements are and where you determine what you still need to research or learn to complete the story. Break the requirements down into a step by step list of what you need to accomplish. Make notes how you plan to accomplish it. Do this in the comments so you can help yourself track what goes where and how things interact. This will also help you keep track of your progress when you take breaks.

## Dealing with Roadblocks
Roadblocks are common in programming, but persistence and practice will help you learn and get better. First start with researching what you don't know. If you don't know where to start, or feel you need better search terms, ask your instructor for help. Even just defining the roadblock to someone else can help clear it up. Create pseudocode if necessary and then approach figuring out how to implement it. If you get frustrated with this process and are not making progress, walk away and take a break. While doing something else, your brain will continue to process your problem in the background, and you may suddenly figure it out. Even if you don't, you'll come back to the block refreshed and may see something new. Another set of eyes can always help too.

##Debugging
Some programmers hate debugging and some love it (some even have a love/hate relationship with it). It's a big part of programming. Make sure you are testing your code as frequently as possible to reduce big huge bugs that are difficult to decipher. Print to the console if that helps you figure out what's going on.

#Simplicity vs Cutting Corners
Simplicity in coded solutions is a wonderful goal. The more simply you can make something work, the more robust it tends to be. But this does not mean that you should cut corners. Trying to modify a story to fit your code or creating code that is narrowly construed will just cause problems for future programmers. You want to solve the problem, not create new ones. For instance, if you're trying to verify input from a user, there are lots of data annotation statements that can make this fairly simple. That's a good solution. Utilizing a single format and saying that's the only way something can be inputted is not. It is not only frustrating for the user, but can hinder progress on the project. 

A real example of this is dates. Setting dates so they can only be entered as MM/dd/yyyy may seem like a reasonable solution, but it would need to be reworked to use a date-picker as an input helper, and is also culturally limiting, as many countries write dates as dd/MM/yyyy. To go a step further, imagine a programmer builds custom validation for all DateTime elements based on this model and then someone wants to utilize a DateTime element that includes the hour and minutes. Suddenly that entire custom validation method must be rewritten. Solve the problem as simply as you can without putting unnecessary restrictions on its use.
