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
4. Navigate into that directory by entering the command `cd GitTutorial`. You can view the folder contents by using the command `ls` (short for List), which should show a file called *README.md* (this file) and *Members.txt*, which we'll be modifying in future steps.
5. Before we forget, let's also configure Git to know who we are. Enter the following two commands, one after another, in Git Bash, with your appropriate information filled in:
```
$ git config --global user.name "Your Name Comes Here"
$ git config --global user.email you@yourdomain.example.com
```
