
# Git and Github

### Basics

To create new files:
```shell
touch foo.py
```

To clone a git repository:
```shell
git clone URL
```

### Committing changes

To add files to next commit:
```shell
git add foo.py
```

To commit:
```shell
git commit -m “message”
# to add and commit all files:
git commit -am “message”
```

To check the status of the added files:
```shell
git status
```

To push changes to origin:
```shell
git push
```

To pull changes from origin:
```shell
git pull
```

### Resetting

- [ ] Git reset —hard <commit>
- [ ] Git reset —hard origin/master



### Branching


- [ ] Master vs feature branches
Use branching to work on new features without disturbing main code
- [ ] Switch HEAD, refers to which branch youre working on
- [ ] Can merge branches

To know what branch you are currently on:
- [ ] Git branch

```shell
git checkout -b NEW_BRANCH_NAME
git checkout EXISTING_BRANCH_NAME
```

``` shell
git merge FEATURE_BRANCH
```

fork means to copy repo to personal github, can make edits and make a pull request

use GitHub pages to host personal website
kmccoy3.github.io

