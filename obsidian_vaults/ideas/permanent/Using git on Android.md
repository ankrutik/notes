# Using git on Android
Tags: #git #android

## Install Termux
https://play.google.com/store/apps/details?id=com.termux

## Enable storage access for Termux
Start Termux

Enter following command
```shell
$ termux-setup-storage
```

The app will ask for storage access at this point. Allow.

https://wiki.termux.com/wiki/Internal_and_external_storage

## Install git and ssh
Run command
```shell
$ apt install git openssh
```

## Setup git
```shell
$ git config --global user.email "ankrutik@gmail.com"

$ git config --global user.name "Krutik Arekar"

$ git config --global credential.helper store

## Clone
```shell
$ git clone https://github.com/ankrutik/notes notes
```

## Credentials
If using GitHub, you will be asked to enter username and password. 
- Here username will be your email
- Here password is not account password, but **personal authentication token**. 
	- These need to be created in the GitHub settings. 

> [!attention] Export on Personal Auth Tokens
> 
Personal authentication tokens have an expiry so authentication may suddenly start failing as you are using git.

Having setup the credential helper as `store` will make got remember the credentials you enter.

## Archive
### Mgit
Stopped using Mgit as it does not detect new files. 

The github app doesn't let you pull, commit, push, etc. Just view a codebase.
Install app called MGit.
Generate ED25519 ssh keys on laptop. 
Upload public key to github. Import private into MGit.
Clone github repo in MGit at a location on your phone storage.
Mgit will still try to authenticate using password. For GitHub, here password is not account password, but personal authentication token needs to be created and used. THESE TOKENS HAVE EXPIRY so authentication may suddenly start failing suddenly.
After this you will be able to pull, push, commit, etc. using Mgit.


#### Links

#### References