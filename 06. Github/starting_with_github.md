# Git & GitHub

![Cheatsheet](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/Git%20cheat%20sheet%20light%20(FINAL).png)

[Link](https://dev.to/doabledanny/git-cheat-sheet-50-commands-free-pdf-and-poster-4gcn)

## Install Git

```Shell 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```

## Link git to your Github account

### Create a SSH key
To login into github you need a **SSH-key**. Here is how to generate one.

1. Create an SSH key linked to your email.

```console
me@laptop:~$ ssh-keygen -t ed25519 -C "your_email@example.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/*user_name*/.ssh/id_ed25519):
Created directory '/c/Users/*user_name*/.ssh'.
```
OR
```console
me@laptop:~$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```


2. Save it to default location: (/home/*user_name*/.ssh/id_rsa): 
```console
Enter passphrase (empty for no passphrase):[Leave blank and press `Enter`]
Enter same passphrase again:[Leave blank and press `Enter`]
Your identification has been saved in /c/Users/*user_name*/.ssh/id_ed25519
Your public key has been saved in /c/Users/*user_name*/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:SZ...............pur4MtDI your_email@example.com
The key's randomart image is:
+--[ED25519 256]--+
|
|
```

3. Check that the SSH key is created 
```console
me@laptop:~$ eval "$(ssh-agent -s)"
Agent pid #### [four digits]
```


4. Add the SSH key in the right location in your local machine
```console
me@laptop:~$ ssh-add ~/.ssh/id_ed25519
Identity added: /c/Users/*user_name*/.ssh/id_ed25519 (your_email@example.com)
 ```

### Add the SSH key to your github account

1. Copy the content of the file to your clip
With clip
```console
me@laptop:~$ clip < ~/.ssh/id_ed25519.pub
```
OR
With xclip
```console
me@laptop:~$ sudo apt-get install xclip
me@laptop:~$ xclip -sel clip < ~/.ssh/id_rsa.pub
```

2. On github, go to your **Settings** > **SSH and GPG keys** > **New SSH key**

3. Paste the key, add a title and save it.

## Cheatsheet
[PDF cheatsheet](https://github.github.com/training-kit/downloads/fr/github-git-cheat-sheet.pdf) from github.com

### How to: Commit your code
```shell
git add file.js # Add your new files.
git commit # Commit the changes
git push # Update a Github branch with local changes
```

### How to: Create a branch and commit your code
```shell
git branch bugFix # Create a bugFix branch
git checkout bugFix # Switch HEAD to bugFix branch
git commit
```

### How to: Merge branches
```shell
# To merge branch "bugFix" to "master", be sure to HEAD to master branch:
git checkout master
git merge bugFix # merge bugFix to master
```
### How to: Rebase
Useful to merge and "remove" (make invisible forever) a branch.

```shell
# To rebase branch "bugFix" to "master", be sure to HEAD to bugFix branch:
git checkout bugFix
git rebase master

# Then rebase master into bugFix.
git checkout master
git rebase bugFix
```

### How to: Keep your fork synced with the original repo

```shell
# 1. Fork the repo on github
# 2. Create a local clone of YOUR fork
git clone https://github.com/Joffreybvn/CRL-Turing-4.22.git

# 3. Go to your local repo
cd CRL-Turing-4.22

# 4. Add the ORIGIN repo as upstream
git remote add upstream https://github.com/becodeorg/CRL-Turing-4.22

# 5. Update your local clone with the changes made on the origin repo
git fetch upstream
git merge upstream/master

# 6. Save the changes on github
git add -A
git commit
git push
```
