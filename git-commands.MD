# Git Cheatsheet

### github first 
```console
// establish local repo on git
$ git clone <url>

// push to github
$ git push origin master

```

### git first
```console
// link git to gibhub repo
$ git remote add origin <ssh>

// update and push to github
$ git fetch origin
$ git push -u origin master
``` 

### remote
```console
$ git remote
$ git remote -v

// re-assign the origin
$ git remote set-url origin <new.git.url/here>
```

### undo staged and unstaged
```console
$ git restore --staged .
$ git restore .

// or alias "undo"
$ git config alias.undo "!f(){ git restore --staged $1 && git restore $1; }; f"
```

### :trophy: restore old versions : **adds to commit log**
```console 
$ git restore --source head~5 .
$ git add .
$ git commit -m 'restore version from 5 back'
```

### :shit: reset old versions : **deletes commit log**
```console
// hard reset deletes all changes from head to head~5, 
// but brings with you the working directory changes (staged and unstaged)
$ git reset --hard head~5 

// to go back if you made a mistake, look at reflog for your starting point then
$ git reflog
$ git reset --hard <hash from starting point before your reset>

// soft reset keeps working tree, can dump all of your changes from head to head~5 to a new branch if you wnat to
$ git reset head~5  

$ git sw -c <branch-dump-changes-to>
$ git add .
$ git commit -m 'dump additions after version(-5) stuff here'
```

### pull with unrelated histories
```console
$ git pull origin master --allow-unrelated-histories
```

### checkout
```console
$ git co head~5

// To save the changes from head to head~5 to a branch
$ git sw -c <new-branch>

// To abandon this view with no changes
$ git sw -
```