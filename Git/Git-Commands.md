> Written with [StackEdit](https://stackedit.io/).

### Remove directory from remote repository

```bash
git rm -r --cached node_modules
git commit -m 'Remove the now ignored directory node_modules'
git push origin master
```
[Reference](https://gist.github.com/sabarasaba/3080590)

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

If you want to ignore all files with an specific extension, for example, `.txt` files, just use:
```bash
project $ echo "*.txt" > .gitignore
```
You can also ignore all files with the same path on the title, for example, all files starting by `video.`:
```bash
project $ echo "*.txt video.*" > .gitignore
```
Or just video on their titles:
```bash
project $ echo "*.txt video*" > .gitignore
```
In order to ignore folders:
```bash
project $ echo "*.txt Temp/" > .gitignore
```
The `/` signify that `Temp` is a directory. Adding a * ignores all files in that directory:
```bash
project $ echo "*.txt Temp/*" > .gitignore
```
If you want to ignore all Temp folders within the folder:
```bash
project $ echo "*.txt */Temp/*" > .gitignore
```
[Reference](https://www.google.com/search?q=how+to+use+gitignore&rlz=1C1GGRV_enUS765US765&oq=how+to+use+gitignore&aqs=chrome.0.0l6.6549j0j9&sourceid=chrome&ie=UTF-8#kpvalbx=1
)

### How can I determine the URL that a local Git repository was originally cloned from?
If you want only the remote URL, or referential integrity has been broken:
```bash
git config --get remote.origin.url
```
This is the output:
```bash
https://gitlab.com/magkey/test_project.git
```
If you require full output or referential integrity is intact:
```bash
git remote show origin
```
When using `git clone` (from GitHub, or any source repository for that matter) the default name for the source of the clone is "origin". Using `git remote show` will display the information about this remote name. The first few lines should show:
```bash
* remote origin
  Fetch URL: https://gitlab.com/magkey/test_project.git
  Push  URL: https://gitlab.com/magkey/test_project.git
  HEAD branch: master
  Remote branch:
    master tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':

    master pushes to master (up to date)
```
[Reference](https://stackoverflow.com/questions/4089430/how-can-i-determine-the-url-that-a-local-git-repository-was-originally-cloned-fr)

 












<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxOTI3OTM4NiwyMDE5Mjc5Mzg2LDE2MD
E4MTY5NzEsLTEzMDIxNTI2NTAsLTE5MjU3MDg0NjAsLTEwNTEz
MjU3NDcsMjA0MDI2NzYwOSwyNDI2ODk3MzNdfQ==
-->