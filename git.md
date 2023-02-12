This documentation is presented for sharing the most important git feature and bug fixing methods.

### **Make local folder git repo**
```shell
$ git init -b main
$ git add . && git commit -m "initial commit"
# create a repo in githug and copy the url
$ git remote add <name> <url>
$ git push --set-upstream <name> main
```

### **Restoration of local branch and its files**
```shell
$ git restore file_name #with that clean last uncommitted file change back
```

### **Delete file from repository**
```shell
$ git rm file/name
$ git commit -m 'commit note'
$ git push
```

### **Update latest commit comment**
```shell
$ git commit --amend -m "New commit message." # if did not push yet
```

### **Check last *local* commit version**

```shell
$ cat .git/HEAD
$ cat .git/refs/heads/master
$ git log -1
```

### **Create new branch in Repo**

```shell
$ git checkout -b <branch-name> # Create a new branch and check it out
$ git push --set-upstream <remote-name> <branch-name> # then you branh is ready , Where <remote-name> is typically origin -> git push --set-upstream origin main
```

### **Change Global Config**

```shell
$ git config --global user.name "User Name" &&
git config user.password "Password" &&
git config --global user.email "e-mail address"
```

### **Show Global Config**

```shell
$ git config --list --show-origin
$ git config --global user.name
$ git config --global user.email
```

### **Change Branch Name**

```shell
$ git checkout <old_name> #old name is main originally, I tested with this repo
$ git branch -m <new_name> # changed to head
$ git push origin -u head
# then here -we using github- we need to change ongoing branch main->head then after we can delete 
$ git push origin --delete main ## finito
```

### **Difference between file in local repository and origin**

After running this script, you will be finished comparing the local Git and remote Git using the last commit number.

```shell
#!/bin/bash
git fetch

var_local=`cat .git/refs/heads/master`
var_remote=`git log origin/master -1 | head -n1 | cut -d" " -f2`

if [ "$var_remote" = "$var_local" ]; then
    echo "Strings are equal." #1
else
    echo "Strings are not equal." # 0 if you want
fi
```


## **Mac Credential Configuration Files**

```shell
$ /Library/Developer/CommandLineTools/usr/share/git-core/gitconfig
$ /Users/abdullah/.git-credentials
``` 

## **Check previous commits with id and commit note**

**full id and commit note**
```shell
$ git log --pretty=oneline
``` 

<details><summary>output example</summary>
<p> 

681860bc03b89e607c568570f7e95b901b4fedf0 (HEAD -> master, origin/master, origin/HEAD) adapt json schema for batch results (#1033)

31abbe1e4b6e3a0bc7d60a72fd3802cb928654dc Minor updates to UWP samples (#1035)

3ad8fe15d27dbcc25feb4ca0e41cf26be65a460c Renaming batch ingestion client solution, refactoring, removing LID (#1027)

e6924c9cee0b3a6bfa44721779af0b9e4c2cdeb8 pronunciation assessment javascript browser sample (#1010)

37619365c40f98b419f98865163aa5617e6910e7 Update dependent-verification.html (#1019)

5d698988e1b3ae36bb5169330f8e37e0623d0a44 Add keys to KV in ARM, cleanup (#1015)

</p>
</details>

**short id, name, date and commit note**
```shell
$ git log --pretty=format:"%h - %an, %ar : %s"
``` 
also can filter with keyword if need
```shell
$ git log --pretty=format:"%h - %an, %ar : %s" | grep python
``` 

<details><summary>output example</summary>
<p> 

681860bc - Christian Landsiedel, 7 hours ago : adapt json schema for batch results (#1033)

31abbe1e - Darren, 8 days ago : Minor updates to UWP samples (#1035)

3ad8fe15 - Henry van der Vegte, 8 days ago : Renaming batch ingestion client solution, refactoring, removing LID (#1027)

e6924c9c - Yulin Li, 2 weeks ago : pronunciation assessment javascript browser sample (#1010)

37619365 - Glenn Harper, 2 weeks ago : Update dependent-verification.html (#1019)

</p>
</details>



## Referances

[Online Git Book](https://git-scm.com/book/en/v2/)
[web-branch](https://stackoverflow.com/questions/1519006/how-do-you-create-a-remote-git-branch)
