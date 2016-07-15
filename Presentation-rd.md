https://github.com/Randynamic/git-training-examples.git

# Config
`git config`

```
    git config  --global user.name "Mr. Awesome" 
    git config  --global user.email Awesome@randynamic.com
    git config  --global color.ui true
    git config  --list
```

# Start 
- `git help` is a command that will show teh available commands
- `git clone [url]` creates a local repo
- `git status` checks the current status of your repo

- `git commit -m "Modify readme & add todo.txt."` commits a message
- `git commit -a -m "Modify readme & add todo.txt."` commits all untracked files as well
- `git commit --amend -m "Modify readme & add todo.txt."` adds to last commit
- `git push origin/master` pushes changes to master branch
- `git log` shows the log files <= commits
- `git log --pretty=oneline` shows the log files on a single line (summary)

# Second
what is the difference between fetch and pull?

But what if we make a mistake?
- `git reset --soft df71a27`
- `git reset --hard HEAD^` undo last commit
- `git reset --hard HEAD^^` undo last 2 commits

- `git branch awesomeness` creates a branch
- `git branch -d awesomeness` deletes a branch on my comp but still present on everyone else his/here comp and remote
- `git branch -d origin/awesomeness` => deleted on my comp and remote but still present on yours if you have pulled it

There is also a possibility to work with multiple remotes <= is not something we will do here so if you want to now more about that get into the books

## After push never ever ever do this!

```
    git reset --soft HEAD^
    git commit --amend -m "New Message"
    git reset --hard HEAD^ $ git reset --hard HEAD^^
```

## Merge
```
    To https://github.com/randynamic/git-training-exampes.git
    ! [rejected]        
    master -> master (non-fast-forward)
    error: failed to push some refs to 'https://github.com/randynamic/git-training-exampes.git' 
    hint: Updates were rejected because the tip of your current branch is behind hint: its remote counterpart. 
    Merge the remote changes (e.g. 'git pull') hint: before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

What is the difference between rebase and merge?

```
Master   dev
    |    |
    |    8
    0    |
    |    |
    |    8
    0    |
    |   /
    |  /
    | /
```

### git rebase:

```
Master  dev
    |    |
    |    8
    0    8
    |    |
    0    0
    |    0
    |   /
    |  /
    | /
```


### git merge
```
Master   dev
    |    -
    |    8
    0    0
    |    |
    |    8
    0    0
    |   /
    |  /
    | /
```


### Squasing

```
    df71a27 - 1 (4 minutes ago)
    ba9dd9a - 2 (15 minutes ago)
    f392171 - 3 (1 day ago)
```

`git rebase -i HEAD~3` squash from head 3 commits back

```
    pick f392171 1
    pick ba9dd9a 2
    pick df71a27 3
```

```
    pick f392171 1
    squash ba9dd9a 2
    squash df71a27 3
```

`git rebase --continue`

! Never ever ever do this on items that are pushed to origin !

## Check the diffs between commits

`git diff HEAD`
`git diff master awesomeness`
`git diff 58768797685865..9868767589`


# Other stuffies

`git blame README.md --date short`

`git rm README.txt` deletes an item
`--cached` will not delete it from the file system


## Git Aliases
```
    git config --global alias.st status 
    
    git config --global alias.co checkout
    git config --global alias.br branch 
    git config --global alias.ci commit
```
