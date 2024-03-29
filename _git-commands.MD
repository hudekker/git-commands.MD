# Git Cheatsheet

### creat on github first

```console
// establish local repo on git
$ git clone <url>

// push to github
$ git push origin master

```

### create on git first

```console
// link git to gibhub repo
$ git remote add origin <ssh>

// update and push to github
$ git fetch origin
$ git push -u origin master
```

### remote

```console
// view the remotes
$ git remote
$ git remote -v

// re-assign the origin
$ git remote set-url origin <ssh>

// add another account (remotes= origin, hudekker, tainan, gist-origin, gist-hudekker, gist-tainan)
$ git remote add hudekker <git@hudekker:hudekker/my-repo.git>
$ git remote add tainan <git@tainan:tainanapps/my-repo.git>
$ git remote add gist-origin <git@gist.github.com:<hash>.git>
$ git remote add gist-hudekker <git@gist.hudekker:<hash>.git>
$ git remote add gist-tainan <git@gist.tainan:<hash>.git>

// remove
$ git remote rm origin2

// rename
$ git remote rename origin2 hudekker
```

### Restore Lost Code Sequence

```console
// 1. Identify the Lost Code
$ git log -- background.js

// 2. Create a New Branch
$ git switch -c restore-lost-code

// 3. Switch to the Relevant Commit
$ git restore --source=<commit_hash>

// 4. Copy the Lost Code
// Open background.js in your editor and manually copy the lost code.

// 5. Switch Back to the Original Branch
$ git switch <original_branch_name>

// 6. Paste and Commit the Restored Code
// Open background.js in your editor, paste the copied code, and commit the changes.
$ git add background.js
$ git commit -m "Restore lost code in background.js"
```

### pull with unrelated histories

```console
$ git pull origin master --allow-unrelated-histories
```

### undo staged and unstaged

```console
// Undo staged and unstaged
$ git restore --staged .
$ git restore .

// or alias "undo"
$ git undo .

// alias for undo
$ git config alias.undo "!f(){ git restore --staged $1 && git restore $1; }; f"
```

### :trophy: restore old versions : **adds to commit log**

```console
$ git restore --source head~5 .
$ git add .
$ git commit -m 'restore version from 5 back'
```

### :shit: reset old versions : **deletes from commit log**

```console
// hard reset deletes all changes from head to head~5,
// but brings with you the working directory changes (staged and unstaged)
$ git reset --hard head~5

// to go back if you made a mistake, look at reflog for your starting point then
$ git reflog
$ git reset --hard <hash from starting point before your reset>

// soft reset keeps working tree, adds all changes from head to head~5 to working tree
// Can dump all of your changes from head to head~5 to a new branch if you wnat to...
$ git reset head~5

$ git sw -c <branch-dump-changes-to>
$ git add .
$ git commit -m 'dump additions after version(-5) stuff here'
```

### checkout

```console
$ git co head~5

// To save the changes from head to head~5 to a branch
$ git sw -c <new-branch>

// To abandon this view with no changes
$ git sw -
```

### stash

```console
// un-named stash save, and use it
$ git stash
$ git pop

// named stash in list
$ git wip 'my-new-stash'
$ git stash list
$ git apply stash@{n}

// alias for stashing in list, using 'wip' does htis
$ git config alias.wip2 --global 'stash push -m'
```

### aliases: create, view, edit

```console
// create
$ git config --global alias.ac '!git add $1 && git commit -m'

// view
$ git config --get-regexp '^alias\.'

// edit
$ git config --global -e
```

### change default on git from master to main

```console
// change branch from master to main and push it to github
$ git branch -m master main

$ git push -u origin main
```

```console
// on github update default to main
$ git push origin --delete master
```

```console
// config git to use main as the default branch
$ git config --global init.defaultBranch main
```
