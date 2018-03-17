# Intro: git 

Many people think "git" and "GitHub" are interchangeable, but _they are not_!
*Git* is a version control system created by Linus Torvalds that resides upon
every Linux and most UNIX-based computers (Macs are UNIX-based, so as long as
you have Apple's command line developer tools installed, you can do git
commands). *GitHub* is a company that produces the site github.com, hosts all
the code you see on there for free, and provides a bunch of additional services
you can pay for.

Ok great. Now let's delve into the bread and butter of using git as your
version control system.

# Fork a repo

Because we don't want to push code changes directly from your local computer to
the master branch, we're going to do what is known as "forking"--creating your
own copy of the repo that you can make changes to.

### What to do

Go onto a repo's site and click "Fork" (on the upper right).

# Clone your own copy of the repo

Once you've forked and gotten your own copy, you want to download your own copy
onto your local machine (your laptop) so that you can make edits. You can also
make edits in the browser, but that's ugly and I shall not stand for it. 

### What to do

Go on your profile and click on the repo. Click the green "Clone or download"
button. If you have your SSH keys set up with your Github, hit the "copy to
clipboard" button when the heading in the box says "Clone with SSH." Otherwise,
click the blue "Use HTTPS" link on the upper right of the box and hit the "copy
to clipboard" button once you see the header become "Clone with HTTPS."

Now, go on command line (Terminal) and `cd` to the directory where you want the
repo to live. This could be ~/Desktop, or ~/Documents, etc. 
```
$ cd ~/path/to/where/I/want/this/repo/to/be
```
Now, type `git clone` and paste in the link you just copied.
```
$ git clone <link>
```

# Editing the repo

Great, now you have your own copy of the repo on your local machine! To see
changes, make commits, push, and pull, you always have to be inside the repo
folder:
```
$ cd ~/path/to/the/repo
```
All of the following commands assume you are inside the repo directory (you can
check that you are inside for sure by running `pwd` on command line--it prints
your *p*resent *w*orking *d*irectory).

## Checking the status

You can check how many changes you've made to your local copy by doing
```
$ git status
```

Under "Untracked files," it'll list all the files you are not currently keeping
track of. You usually want to keep track of everything you downloaded when you
cloned, so go ahead and do this:
```
$ git add *
```
That adds all the files you just downloaded to the list of tracked files, 
meaning git will now keep track of the changes made to all those files.

After you've made some changes to the files in the repo, there will be a
section that says "Changes not staged for commit." The files listed under this
are all the files that you are tracking and have made changes to. You have to
individually add each file you want to document changes for--for example, if
you made changes to `code.js` and you want to commit (document) these changes,
type
```
$ git add code.js
```

On the other hand, if there's a file you suddenly want to stop tracking, do
```
$ git rm <filename>
```

## Seeing changes

You can see what you changed about all the changed files by running
```
$ git diff
```
This, however, usually is difficult to parse if you've had a lot of changes
since your last commit, so what I usually do is the individual file that I know
has changed:
```
$ git diff <filename>
```

# Documenting changes

## Making a commit

To document changes made to your local repo, you have to first add the file(s)
individually (as described in the section "Checking the status"), and then type
a commit message summarizing what you did since the last commit. THESE MESSAGES
SHOULD BE IN THE IMPERATIVE. As in, NOT any of the following:
- deleted comments
- refactoring functions
- changed structure
Instead, please use _the imperative_:
- delete comments
- refactor functions
- change structure

Once you've thought of your commit message, create the commit by doing
```
$ git commit -m "<message>"
```
Don't forget to put your message in quotes.

## Pushing

Once you've made at least one commit (you can make as many commits as you want,
but they won't get pushed to the copy of your repo in the cloud until you
"push"), you need to push. This is as simple as 
```
$ git push
```
The first time you push, you may have to do 
```
$ git push -u origin master
```
But try `git push` first and see what they tell you to do.

# Getting up-to-date copies of the remote repo (i.e. pulling)

The beauty of having forked and cloned your own copy of the repo means that no
one besides you is editing it. However, if you were ever working on a different
branch of the actual repo or--god forbid--the master branch, you should
periodically "pull" to get the changes that other people made into your local
copy.
```
$ git pull
```

# Conclusion

You are now a git master! Go forth and conquer (maybe with a handy-dandy [cheat
sheet](https://www.git-tower.com/blog/git-cheat-sheet/) by your side).
