# Pratical GIT

### Main git commands

Throughout this document, we will have a brief explanation to facilitate understanding.

**Create repository** 
Create a new directory, go to and type:

```sh
$ git init
```
Create a working copy in a local repository by running the command:
``` sh
git clone </path/to/resository>
```
When using a remote server, your command will be:
``` sh
git clone <user>@<server>:</path/to/repository>
```
**Workflow**

Local repositories consist of three "trees" maintained by git:

* First is your **WORK DIRECTORY** that contains the current files;
* Second **INDEX** that functions as a temporary area;
* And, finally, the **HEAD** that points to the last commit.
Add and confirm.


|WORK DIRECTORY||INDEX||HEAD
:-:|:-:|:-:|:-:|:-:|
![IMAGE ALT TEXT HERE](https://cdn1.iconfinder.com/data/icons/line-mix-vol-3/128/-60-128.png) | **add** |![IMAGE ALT TEXT HERE](https://cdn4.iconfinder.com/data/icons/aami-web-internet/64/aami14-02-128.png)|**commit**|![IMAGE ALT TEXT HERE](https://cdn3.iconfinder.com/data/icons/basic-mobile-part-2/512/folder_tree-128.png)
|||**STAGE**|||

To propose the changes (add them to Index) and inform git that you should control the file, use the command:

``` sh
git add <file>
git add *
```

This is the first step in the basic git workflow. To confirm changes and commit changes, commit, like this:

``` sh
git commit -m "Changes Comments"
``` 
Now the files will be loaded into HEAD, but will not yet be uploaded to the remote repository.

**Sending changes**
The changes are now in the HEAD in your working working copy. To send these changes to your remote repository, run:
``` sh
git push origin master
```
Change master to any desired branch by sending your changes to it.

If you have not cloned an existing repository and want to connect your repository to a remote server, you must add it with:
``` sh
git remote add origin <servidor>
```
You are now able to submit your changes to the selected remote server.
Branched.

The branches are used to develop characteristics isolated from each other. The master branch is the "default" branch when you create a repository. Use other branches to develop and merge them into the master branch upon completion.

Create new branch the name **"function_x"** and select use:
```sh
git checkout -b function_x
```
Return to branch master, with command:
``` sh
git checkout master
```
Remove the branch, Remove the branch as follows:
``` sh
git branch -d function_x
```
A branch is not available to others unless you send the branch to your remote repository
``` sh
git push origin <function_x>
```
**Refresh and merge**

To update your local repository with the newest version, run:
```sh
git pull <branch source> <destination branch>
```

In your working directory to get and merge remote changes.
To merge another branch to its active branch (eg master), use:
``` sh
git merge <branch>
```
In both cases, attempt to merge the changes automatically. But, it does not always happen and results in conflicts. You will need to resolve the merge of these conflicts manually by editing the files displayed by git. After you change, you need to mark them as fused with:
```sh
git add <file>
```
Before you merge the changes, you can also preview them using:
```sh
git diff <branch source> <destination branch>
```
**Labeling**

It is recommended to create labels for software releases. This is a well-known concept, which also exists in SVN. You can create a new label called 1.0.0 by running the command:
```sh
git tag 1.0.0 1b2e1d63ff
```
The **1b2e1d63ff** Represents the 10 characters you want to refer to your report. You can get the commit id with:
``` sh
git log
```
It can be used less, but it must be unique.

**Overwrite** 

If you have done something wrong, you can overwrite the local changes using the command:
```sh
git checkout -- <file>
```
This replaces as in your tree with the latest content. Changes added to the index as well as new files will be retained.

If instead you remove remove all changes and commit locations, retrieve the latest history from the server, and then point to your local master branch this way:
```sh
git fetch origin
git reset --hard origin/master
```
