This documentation is presented for sharing the most important git feature and bug fixing methods

### **Check last *local* commit version**

```shell
$ cat .git/HEAD
$ cat .git/refs/heads/master
$ git log -1
```
### **Show Global Config**

```shell
$ git config --list --show-origin
$ git config --global user.name
$ git config --global user.email
```

## **Mac Credential Configuration Files**

```shell
$ /Library/Developer/CommandLineTools/usr/share/git-core/gitconfig
$ /Users/abdullah/.git-credentials
``` 