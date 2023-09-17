```sh
# create new branch
git checkout -b <branch-name> 
```

```sh
git checkout <merge-into-branch>
git merge <merge-from-branch>
```

``` sh
git pull origin staging
```

```sh
git push --set-upstream origin component-testing
```

```sh
git fetch origin
```

```sh
git config --list
git config --global user.name <FIRST_NAME LAST_NAME>
git config --global user.email <MY_NAME@example.com>
git config --global color.ui auto
git config --global init.defaultBranch main
git config --global pull.rebase false
git config --global core.excludesfile ~/.gitignore_global
git config --get user.name
git config --get user.email
echo .DS_Store >> ~/.gitignore_global
ls ~/.ssh/id_ed25519.pub
ssh-keygen -t ed25519 -C <myemail>
cat ~/.ssh/id_ed25519.pub
```

```sh
git log
git reset --hard <specified_commmit>
```

```sh
# delete branch locally
git branch -d <local_branch_name>

# delete branch remotely
git push origin --delete <remote_branch_name>
```

```sh
# initialising a repo with bitbucket
git init
git add --all
git commit -m "initial commit"

git remote add origin <url>
git push -u origin main
```

```sh
# for when git push hangs
killall ssh-agent; eval `ssh-agent`
```

```sh
git config --global push.autoSetupRemote true
```

```sh
# .gitignore
git rm --cached <git-ignored>    
```
