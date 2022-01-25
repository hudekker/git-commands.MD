# Example Git Commands
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

### reset old versions (deletes commits)
```git
// eliminates working tree
$ git reset --hard head~5 

// soft reset keeps working tree, can dump it off to a new branch if you wnat to
$ git reset head~5  
$ git sw -c dump-it
```

### undo staged and unstaged
```git
$ git restore --staged .
$ git restore .

// or alias "undo"
$ git config alias.undo "!f(){ git restore --staged $1 && git restore $1; }; f"
```