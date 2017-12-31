---
layout: post
title: How to add SSH keys on Windows
categories: [tech]
tags: [devops, git]

---

Few easy steps to add new ssh keys to syncronize a computer with your Github/Gitlab/GitWathever accounts so you can start managing your versions.

> Git page: https://git-scm.com/

We will need to create a key pair,  a `public` for the Git server and a `private`  for the computer. And then add the key into our 
Gitlab or Github account.

### Generate the ssh pair and save the private one in the computer

I use `PuTTYgen`, you can download it (here)[https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html] choose `puttygen.exe (a RSA and DSA key generation utility)`

Once is opened:

0. Click `Generate`.
0. Move the mouse through the blank area
0. (optional) Change `Key comment` field so you can identify the key i.e. `home-desktop`
0. Click `Conversions` > `Export OpenSSH key` on the toolbar
0. Save it into  `~/.ssh/id_rsa`

> In my computer I will place the file called `id_rsa` *without extension* inside the folder `.ssh` located in `C\Users\vperezb`
> The file path will be: `C\Users\vperezb/.ssh/id_rsa`


### Add the public key to Gitlab or Github

0. Copy the public key you've created (is under the text `Public key for pasting into OpenSSH authorized_keys file`).
0. Open your Github or Gitlab account and go into SSH keys settings screen.
	+ GitLab: https://gitlab.com/profile/keys/
	+ GitHub: https://github.com/settings/keys
0. Create a `New SSH key` by pasting the content copied in step 1.


*GRATZ! Now you can start working with Git!*

### Brief introduction to Git

First, you need to tell Git who you are:

```git
git config --global user.email "victor.perez.berruezo@gmail.com"
git config --global user.name "vperezb"
```

Clone the repo:

```git
git clone git@path/user/repo
```

To stash all:

```git
git add .
```

To stash specific file:

```git
git add <file>
```

To commit:

```git
git commit -m  "this is the commit message"
```

To push to the server:

```git
git push origin master
```


### Common ssh error

```bash
Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
