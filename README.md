# GitTutorial #

This package contains the Git Tutorial for the Robotics Club.
By the end of this tutorial, this repository should have a list of everyone that attended the Robotics Club Git Lecture, and attendees should hopefully have an understanding of basic concepts such as add, commit, checkout, merge, push/pull, and merge conflict resolution.

## First Steps: Installing Git and Cloning this Repository ##

If you haven't already, you'll need to download Git [here](https://git-scm.com/downloads). For the most part, you can use the default installation options. However, I recommend changing these:

* On the "Choosing the default editor used by Git" step, open the dropdown menu and pick the text editor of your choice. Vim is notoriously difficult for beginners so I do not recommend it, even if it is the default option.
* On the "Adjusting your PATH environment" step, select "Git from the command line and also from 3rd-party software". We won't use this now, but it gives you options later down the road without messing anything up now.

Once the installation process is complete, we'll **Clone** this repository onto our computers:

1. Open Git Bash from the Start Menu. This should open a Bash terminal in your home user directory.
2. Enter the command `cd Documents` and press Enter. This should move the Bash session into your Documents folder (cd is short for Change Directory), as indicated by the colored text. Alternatively, if you'd like to change where you put the folder, just change the cd command, e.g. `cd Documents/CodeFolder`. Note that the folder/path you're trying to navigate to must already exist. If not, make the folder using File Explorer first.
3. Enter the command `git clone https://github.com/mbenson182/GitTutorial.git` and hit Enter. This should make a new folder, called "GitTutorial", with this repository in it. 

   The word "git" is always put first when we're invoking a command with git. The "clone" command means we're copying a repository that already exists somewhere else and putting it on our computer. The next argument (the url) marks where the pre-existing repository is.

4. Navigate into that directory by entering the command `cd GitTutorial`. You can view the folder contents by using the command `ls` (short for List), which should show a file called *README.md* (this file) and *Members.txt*, which we'll be modifying in future steps.
5. Before we forget, let's also configure Git to know who we are. Enter the following two commands, one after another, in Git Bash, with your appropriate information filled in:
```
$ git config --global user.name "Your Name Comes Here"
$ git config --global user.email you@yourdomain.example.com
```

## Next up: Making Changes and Using Branches ##

Typically with Git, we'd like to work on making changes to a repository without affecting things that already work, at least until we've confirmed our new changes also work. This is done using **branches**. When you first clone a repository, or start a new one, usually you end up in the *master* branch, which is typically the stable, working version of your project. Working directly in the *master* branch can make the repo stop working for other users, so we're going to make changes in a different branch. Best practice is to work on major modifications in a *develop* branch, or sub-branches of *develop*, until all the changes are tested to be working.

1. You can view what branches are available in the repository by typing `git branch --list`. This should show the *master* branch and the *develop* branch.

   We've again used "git" to invoke a git command. This time, we want to know about our "branch" information, specifically which ones are available using "--list". 
   
2. ~~We'd like to go work in the *develop* branch. Type the command `git checkout develop` and hit Enter.~~

   ~~Hopefully the "git" part here makes sense. The "checkout" command is used to "check out", or switch to, another branch, in this case that branch being "develop". Note that you can only checkout a branch if there are no changes to the branch you're currently on - you have to save modifications before you go so you don't lose them! We'll talk about how to do this in a bit.~~

3. ~~There should be an updated README file with new instructions in this new branch. Close this README (don't save it if prompted), and re-open it using File Explorer. The tutorial continues there!~~

4. Welcome to the *develop* branch! This is typically the branch that new features will be added into the overall architecture before we know they work. However, we're going to be making our own branches to add our individual changes, and then make those branches feed into *develop*. (If this doesn't make sense now, hopefully it will in a few steps.) To make a new branch, that branches *from develop*, enter the commands (with your last name filled in):

```
git branch develop_<lastname>
git checkout develop_<lastname>
```

   We've used the "branch" command again, this time with a new argument, "develop_<lastname>". This actually creates a new branch called *develop_<lastname>* for you to work in. Then, we "checkout", or basically move to, that branch. If you close and re-open this file, you'll notice that it's the same as the version that was in *develop*. This is an important concept - when you make a new branch, it has the exact same files and contents as the branch you were in when you created it. So right now, *develop* and *develop_<lastname>* are exactly the same! Let's change that.
   
