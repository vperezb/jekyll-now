---
layout: post
title: How to add SSH keys on Windows
categories: [tech]
tags: [devops, git, ssh]

---

Few easy steps to add new ssh keys to syncronize a computer with your Github/Gitlab/GitWathever accounts so you can start managing your versions.

> Git page: https://git-scm.com/

We will need to create a key pair,  a `public` for the Git server and a `private`  for the computer. And then add the key into our 
Gitlab or Github account.

## Generate the ssh pair and save the private one in the computer

I use `PuTTYgen`, you can download it [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) choose `puttygen.exe (a RSA and DSA key generation utility)`

Once is opened:

0. Click `Generate`.
0. Move the mouse through the blank area
0. (optional) Change `Key comment` field so you can identify the key i.e. `home-desktop`
0. Click `Conversions` > `Export OpenSSH key` on the toolbar
0. Save it into  `~/.ssh/my_custom_key_name`
0. Add the brand new created key entering (*ONLY TESTED USING GIT BASH*):
	+ `eval $(ssh-agent -s)` that returns something like `Agent pid 123456`.
	+ Then `ssh-add ~/.ssh/my_custom_key_name` returning `Identity added: /c/...blablabla`.

> If you need acess to two different git accounts, repeat the process by saving the key with a new name

## Add the public key to Gitlab or Github

0. Copy the public key you've created (is under the text `Public key for pasting into OpenSSH authorized_keys file`).
0. Open your Github or Gitlab account and go into SSH keys settings screen.
	+ GitLab: https://gitlab.com/profile/keys/
	+ GitHub: https://github.com/settings/keys
0. Create a `New SSH key` by pasting the content copied in step 1.


*GRATZ! Now you can start working with Git!*

## Common ssh error

```bash
Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
