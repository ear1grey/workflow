## A Git Workflow ##

This is an example-workflow for developing apps and web content.  It is likely to evolve.  You're welcome to fork it, improve it, and send pull requests to assist in the evolution.

Primarily this aims to be a mini-cookbook.  Just basic steps - enough to work simply, and efficiently, with git and github.

### MindSet

1. Keep development and use of modules separate.  If you develop a tool, do not develop it where it is used.  You have two hats, module developer and module user.  You can only wear one hat at a time.

### Clone 

1. Get a local copy of the repo you're going to edit:
    git clone git@github.com:user/repo.git

### Developing 'featurename'
1. Decide what featurename should do.
2. Add an issue to `github.com/user/repo/issues` describing the intended content/functionality.  Use this as an opportunity to think about potential inputs and outputs. 
3. Then branch, hack, merge and share.


#### Branching 'featurename'
 
1. From the list of available issues decide what feature you are going to change or add.
1. Work on one issue at a time.
1. Create a new branch for the issue with `git checkout -b featurename`.
1. Hack until it works.
1. Complete your change doing as many commits as necessary, e.g. `git commit -a -m 'rewrote description of x'`, or 
    git add example.js
    git commit -m 'fixes user/repo#42
([explanation](https://help.github.com/articles/closing-issues-via-commit-messages))
 
#### Merge

1. If you have changes that are not comitted or stashed, commit them or stash them.
1. Switch to the master branch with `git checkout master`.
1. Update the master repository with `git pull`.
1. Merge your changes into the master with `git merge featurename`.
1. Check the results of the merge (if you have tests, runthem) then delete the branch using `git branch -d featurename`

#### Stash

1. You need to stash some uncommitted changes to work on something else or to try a different approach to the problem
1. Stash the changes with `git stash`
1. When you're ready, get your changes back with `git stash apply`. You could also use `git stash pop` to apply the changes and clear the top most stash item in one command.
1. Alternatively, use `git stash list` to view all your stashed changes and apply a specific one with `git stash apply stash@{1}`

### Tidying up your Git Log with Rebase

Many commits by multiple authors can make the `git log` difficult to follow.  Using `git rebase` before pushing to a remote repo can help solve this problem.  NB: Use `git rebase` **only** on a local branch that you have created - using it on a remote branch affects other users (not usually a good thing).  
Caution: rebase is an extremely powerful tool - it rewrites Git History, your work can easily be lost.

1. Working on a local branch, commit incremental changes as necessary, leaving detailed comments for each commit.
1. Invoke rebase interactive mode with `git rebase -i HEAD~x` (where *x* is the number of commits you would like to combine).
1. A list of commits is presented preceeded by the keyword 'pick' change the first instance to 'reword' as this will allow you to change the commit message to something more suitable. Alternatively if you are happy with the message leave it set to `pick`.
1. Change the remaining instances of `pick` to `squash` and close the editor
1. An editor will open allowing you to change the reword commit message to something suitable.  Reword and close the editor.
1. A final editor will show the expected results of the rebase - Just close this.
1. If all is successful the refs/head will be updated - Continue to merge and push.
1. If you made a mistake you can abort the rebase by using `git rebase --abort`

Optionally use `git log` to verify the rebase. After the rebase, several chosen commit messages will be shown under a single commit hash. Additionally use `git rebase branchname` with which git will attempt to do an automatic rebase. Interactive Mode offers control and the ability to abort if need be.

#### Share

1. You've not finished until you push the change to github using `git push`.
