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
1. When you're ready, get your changes back with `git stash apply`
1. Alternatively, use `git stash list` to view all your stashed changes and apply a specific one with `git stash apply stash@{1}`

#### Share

1. You've not finished until you push the change to github using `git push`.

