# Example Git Commands

### github first (clone repo)
```
$ git clone <url>
$ git push origin master

```

### git first
```
$ git remote add origin <ssh>
$ git fetch origin
$ git push -u origin master
``` 

### remote
```git $ 
$ git remote
$ git remote -v

// re-assign the origin
$ git remote set-url origin <new.git.url/here>
```

### restore old versions
```git 
$ git restore --source head~5 .
```

### undo staged and unstaged
```git
$ git restore --staged .
$ git restore .

// or alias "undo"
$ git config alias.undo "!f(){ git restore --staged $1 && git restore $1; }; f"
```

### reset old versions (deletes commits)
```git
// hard reset eliminates working tree and all changes from head to head~5
$ git reset --hard head~5 

// soft reset keeps working tree, can dump all of your changes from head to head~5 to a new branch if you wnat to
$ git reset head~5  
$ git sw -c <branch-dump-changes-to>
```

### pull with unrelated histories
```git
$ git pull origin master --allow-unrelated-histories
```

### checkout
```
$ git co head~5
$ git sw -c <new-branch>
```