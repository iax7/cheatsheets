# GIT

# Reset
```
https://www.websequencediagrams.com/
participant HEAD
participant Index
participant WorkingTree

HEAD->WorkingTree:checkout
WorkingTree->Index:add
Index->HEAD:commit

   HEAD       Index     WorkingTree
    |           |             |
    o------- checkout ------->o
    |           |             |
    |           o<--- add ----o
    o<--commit--o             |
    |           |             |
   soft
   mixed      mixed
              hard          hard
```

* `--soft`  leaves index file & WorkingTree untouched. Undoes the last commit you made.
* `--mixed` resets index but not WorkingTree (default). You rolled back to before you ran all your `git adds` AND `git commit`
* `--hard`  resets index & WorkingTree
