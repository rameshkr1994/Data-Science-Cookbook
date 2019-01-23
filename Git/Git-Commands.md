> Written with [StackEdit](https://stackedit.io/).

### [Git's rejected push error](https://blog.plover.com/prog/git-ff-error.html)

When the following error arise after using `git push origin master`:


```
! [rejected]        master -> master (fetch first)  
    error: failed to push some refs to '../remote/'  
    hint: Updates were rejected because the remote contains work that you do  
    hint: not have locally. This is usually caused by another repository pushing  
    hint: to the same ref. You may want to first integrate the remote changes  
    hint: (e.g., 'git pull ...') before pushing again.  
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.  
```
The steps to follow are:

First: git fetch origin master using:

```
git fetch origin master
```

Second: Rewrite the local changes:

```
git rebase origin/master
```

Third: Try the push again:

```
git push origin master
```

###  git init

This initializes a new Git repository, and you'll notice that it creates a `.git` folder so that you can start your project (this is hidden by default on Unix-based and Windows operating systems).

### git clone

The other situation you might find yourself in is working on an existing project and needing to create a local repository. This can be done with the `git clone` command. You specify a URL with a protocol (such as https:// or git://) and Git fetches all of the information for that repository before putting it in a folder for that project. It also constructs a working copy from the latest commit on master so that you can begin working on the files immediately.

### git add



----

### Creates a working repository using Git

```bash

```

### How to stop tracking and ignore changes to a file in Git - Create a `.gitignore` file
First create a `.gitignore` file:
```bash
project $ touch .gitignore
```
Then add the name of the file or files you want to ignore:
```bash
project $ echo ".remote-sync.jason" > .gitignore
```
Now Git stops tracking the file `.remote-sync.jason`. The `.gitignore` file is also ignored.




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNTEzMjU3NDcsMjA0MDI2NzYwOSwyND
I2ODk3MzNdfQ==
-->