## A quick Git troubleshooting guide

### Conflict management
If you did a mistake or small change in a file and want to forget about it (keeps unversioned files): 
`git reset --merge` gets back to the state before the merge. 

To pull a clean version ignoring local not commited changes:
```
git fetch
git reset -hard HEAD
```
**Caution**: `git clean` is in general a bad idea as it will remove all files. 

