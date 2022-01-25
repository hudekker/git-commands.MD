# Example Git Commands

### github first (clone repo)
```console
$ git clone <url>
$ git push origin master

```

### git first
```console
$ git remote add origin <ssh>
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
```

### :shit: reset old versions : **deletes commit log**
```console
// hard reset eliminates working tree and all changes from head to head~5
$ git reset --hard head~5 

// soft reset keeps working tree, can dump all of your changes from head to head~5 to a new branch if you wnat to
$ git reset head~5  
$ git sw -c <branch-dump-changes-to>
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