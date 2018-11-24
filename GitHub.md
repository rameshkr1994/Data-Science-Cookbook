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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUxODQ2MTI1MF19
-->