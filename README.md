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

   The word "git" is always put first when we're invoking a command with git. The **clone** command means we're copying a repository that already exists somewhere else and putting it on our computer. The next argument (the url) marks where the pre-existing repository is.

4. Navigate into that directory by entering the command `cd GitTutorial`. You can view the folder contents by using the command `ls` (short for List), which should show a file called *README.md* (this file) and *Members.txt*, which we'll be modifying in future steps.
5. Before we forget, let's also configure Git to know who we are. Enter the following two commands, one after another, in Git Bash, with your appropriate information filled in:
```
$ git config --global user.name "Your Name Comes Here"
$ git config --global user.email you@yourdomain.example.com
```

## Next up: Making Changes and Using Branches ##

Typically with Git, we'd like to work on making changes to a repository without affecting things that already work, at least until we've confirmed our new changes also work. This is done using **branches**. When you first clone a repository, or start a new one, usually you end up in the *master* branch, which is typically the stable, working version of your project. Working directly in the *master* branch can make the repo stop working for other users, so we're going to make changes in a different branch. Best practice is to work on major modifications in a *develop* branch, or sub-branches of *develop*, until all the changes are tested to be working.

1. You can view what branches are available in the repository by typing `git branch --list`. This returns only the *master* branch, as it's the only one we have on our computer. 

   We've again used "git" to invoke a git command. This time, we want to know about our **branch** information, specifically which ones are available using "--list". 

   However, if we enter the command `git branch -a` (this lists all branches, local and remote) and look at the red text, there are actually a few branches in the remote repository, including *master* and *develop*.
   
2. ~~We'd like to go work in the *develop* branch. Type the command `git checkout develop` and hit Enter. Even though we don't have *develop* on our computer, it should still grab the stuff on the *develop* branch from the online repository. There should be a message like "Branch develop set up to track remote branch develop from origin." Don't worry about what this means, just let me know if that doesn't work out that way.~~

   ~~Hopefully the "git" part here makes sense. The "checkout" command is used to "check out", or switch to, another branch, in this case that branch being "develop". Note that you can only checkout a branch if there are no changes to the branch you're currently on - you have to save modifications before you go so you don't lose them! We'll talk about how to do this in a bit.~~

3. ~~There should be an updated README file with new instructions in this new branch. Close this README (don't save it if prompted), and re-open it using File Explorer. The tutorial continues there!~~

4. Welcome to the *develop* branch! This is typically the branch that new features will be added into the overall architecture before we know they work. However, we're going to be making our own branches to add our individual changes, and then make those branches feed into *develop*. (If this doesn't make sense now, hopefully it will in a few steps.) To make a new branch, that branches *from develop*, enter the commands (with your last name filled in):

```
git branch develop_<lastname>
git checkout develop_<lastname>
```

   We've used the **branch** command again, this time with a new argument, "develop_lastname". This actually creates a new branch called *develop_lastname* for you to work in. Then, we **checkout**, or basically move to, that branch. If you close and re-open this file, you'll notice that it's the same as the version that was in *develop*. This is an important concept - when you make a new branch, it has the exact same files and contents as the branch you were in when you created it. So right now, *develop* and *develop_lastname* are exactly the same! Let's change that.
   
5. Using the File Explorer, open the *Members.txt* file, and add the details of you and your group members in the same format as I used for my information. The hope is that, after all is said and done, we have a full list of everyone that attended the lecture. When you're done modifying the file, hit save and close your text editor.

6. Return to the Git Bash window and type `git status` . This should show a readout of information about the current state of your git repository: what branch you're on, what files are modified/added/removed, etc. In this case, it shows that *Members.txt* is modified, and that there are changes not staged for commit. This basically means that Git knows we changed the file, but doesn't know we want to save those changes.

7. In Git Bash, enter the command `git add Members.txt` . If we now type `git status` again, it will show that *Members.txt* now has changes ready to be committed.

   Git **add** is used to "stage changes for commit", which basically means that we're telling Git we want to save these files when we enter the **commit** command in the next step. This can be done for every file individually, or you can add all files in the repository at once using `git add --all` .
   
8. Now it's time to save what we've done to git. Enter the command `git commit` . This will open your text editor so you can enter a commit message, which is used to tell others (and yourself) what's changed. In this case, enter something like "Added member info for (your name).", then save and close the text editor. The Git Bash window should say something like "1 file changed, x insertions, x deletion". Congratulations, you've made your first git commit! A **commit** is basically a snapshot of the repository at a given iteration in the development process. You can actually **checkout** individual **commits**, and see how the code was at that point in time, but we won't go into that today.

## Push and Pull: Interacting with Online Repositories and Others ##

1. First up, let's **push** our new *develop_lastname* branch to this repository. Enter the command `git push origin develop_<lastname>` . Note that this will prompt you for a Github username and password to track who made these changes; you'll have to go make one if you don't have one already.

   This attempts to **push** (effectively, upload) your branch *develop_lastname* to the remote repository *origin*, adding it to the available branches/commits there. Note that *origin* is the default remote repository name when you clone a repository from the internet. If you made your own from scratch, you'll have to add your remote, which I won't go into here, but it's pretty easy to look up.
   
   Anyway, the Git Bash window should display a bunch of lines, then on the last line something like `develop_<lastname> -> develop_<lastname>`, which means your branch was pushed successfully. If you type `git log --branches --remotes --tags --graph --oneline --decorate`, the top should show `develop_<lastname>` and `origin/develop_<lastname>` on the same line, meaning that the local and remote version of the branch have the same information.
   
2. Now that we've pushed our content to the remote respoitory under its branch name, we'd like to add that information to *develop* and, eventually, *master*. Enter the command `git checkout develop` , which should bring us back to the develop branch (if you re-open *Members.txt*, your changes should be gone!).  We'd like to **merge** our changes from *develop_lastname* into develop.

3. Enter the command `git merge --no-ff develop_<lastname>`. Your text editor should open with the line "Merge branch 'develop_lastname' into develop". Don't change it, just hit save and exit. If you open *Members.txt* again, your changes from before should now be there!

   Git **merge** tries to combine the changes from branch *develop_lastname* into whatever branch you're currently working in. Don't worry about what *--no-ff* does, it's just to help keep a nice organized branch structure.
   
4. Now, we'd like to share our new, merged version of *develop* with the world. Try to enter `git push origin develop`. If you're lucky, it will go through. However, it's likely that you'll get an error. But it's okay! Type `git log --branches --remotes --tags --graph --oneline --decorate` to find out what happened. 

   Now we know the culprit - somebody else already made and pushed changes to develop while we made our own branch, and Git won't let us push until we integrate those remote changes first. Git prioritizes remote content over local content. That's okay, we can deal with this. Let's learn how to reconcile this.
   
5. First, type `git fetch origin`. This **fetch** command will basically ping the remote repository and find out what's changed there, without touching anything on our local copy of the repository. The resulting readout should show that *develop* has changed, as well as hopefully a few new *develop_lastname* branches from different groups. We want to *pull* the changes from the remote copy of *develop* into our local copy, reconcile the two, and then try to **push** again.

6. Make sure you're in the *develop* branch (you can run `git status` to check), then enter the command `git pull origin develop`. This will try to **pull** the *develop* branch from the remote *origin* into your local version of *develop*. If you're lucky, it will just pop up the commit message window like when we merged *develop_lastname* into *develop* before. However, more than likely,  you'll get an error about what's called a **merge conflict**. This means that there are changes to the two things we're trying to combine that Git can't figure out how to reconcile nicely.

7. Open *Members.txt* and clean up the contents of the file so that all the information we want (from all members) is there. Also delete  all the lines with the <<<<<, =======, and >>>>> stuff. Now, we have a reconciled copy of *Members.txt* with all the correct info. Save and close it, then go back to the Git Bash window and enter `git add Members.txt` and `git commit`. It should open a text editor with a line about merging the two branches. Just save and exit. We now have a local version of *develop* with both the remote and local changes, but we still need to send that to Github!

8. Enter the command `git push origin develop` one more time. Hopefully, it should now push without any errors, in which case you're all done! 

   Unfortunately, because everyone will be trying to do this at the same time you may have to repeat Steps 5-8 a few times. When you finally get it worked out, let me know! I'd like to discuss just a few more things once everyone is done.
