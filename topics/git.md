
# Git and Github

### Basics

To clone a git repository:
```console
$ git clone <URL>
```

To create and open new files:
```console
$ touch foo.py
$ atom foo.py
```

### Committing Changes

To add files to next commit:
```console
$ git add foo.py
```

To commit:
```console
$ git commit -m “message”
```

To add and commit all files:
```console
$ git commit -am “message”
```

To check the status of the added files:
```console
$ git status
```

To push changes to origin:
```console
$ git push
```

To pull changes from origin:
```console
$ git pull
```

To show all commits and descriptors:
```console
$ git log
```

### Merge Conflicts

When attempting to push/pull change to/from git, if a line was edited differently in 2 commits, you will run into a merge conflict.

It will look something like this in your editor:
```python
<<<<<<< HEAD (Current Change)
  <code>
=======
  <code>
>>>>>>> <commit_hash> (Incoming Change)
```

Edit the code directly in your editor, remove the git markings, and commit changes.

### Resetting

To reset to a previous commit:
```console
$ git reset —-hard <commit_hash>
```

To reset to whatever is on GitHub:
```console
$ git reset —-hard origin/master
```

### Branching

Use branching to work on new features without disturbing main code
- Master vs feature branches
- HEAD refers to which branch you are currently working on

To know what branch you are currently on:
```console
$ git branch
```

To change branches:
```console
$ git checkout -b NEW_BRANCH_NAME
$ git checkout EXISTING_BRANCH_NAME
```

To merge branches:
```console
$ git merge FEATURE_BRANCH # While on master branch
```

### Miscellaneous

* `fork` means to copy repo to personal github, can make edits and initiate a pull request.
* You can use GitHub pages to host your personal website.
  * Create github repository that follows the format `kmccoy3.github.io`


### Github Documentation

* Include the following when adding a README.md
  * Project Name
  * Description
    * Keep it short and simple!
  * Table of Contents
  * Installation
    * Include directions for setup, or even a gif!
  * Usage
    * Good use for screenshots.
  * Contributing
    * Outline how you would like others to contribute to your work.
  * Credits
    * Link to the authors.
  * License

If documentation becomes too long, create a wiki instead!
* Unfortunately, wikis only available for public repos
