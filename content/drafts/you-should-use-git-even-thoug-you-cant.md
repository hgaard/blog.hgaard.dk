+++
author = "Jakob Højgaard"
categories = ["git", "versioncontrol", "tfs"]
date = 2017-11-30T00:00:00Z
description = ""
draft = true
slug = "you-should-use-git-even-thoug-you-cant"
tags = ["git", "versioncontrol", "tfs"]
title = "You shoudl use git even though you can't"

+++

# You shoudl use git even though you can't

## Why

as a consultant you work in places where source control  
so when you can't take control of the infrastructure dont let that be an excuse to 

* The TFS version control lacks basic concepts that impeads CI and CD 
  * Lack of easy branching
    * Problem for building separate branches
    * Bigger problem for introducing short lived feature branches

## What

Well as the name implies it's a git to tfs and tfs to git bridge. Which kinda makes it possible for you to work with regular git locally and "just" have tfs acts as your remote repository

## How

First of all you need to install git-tfs. Follow the instructions [Here](https://github.com/git-tfs/git-tfs). I usually use [Chocolatey](https://chocolatey.org/) to install my development dependencies if possible. But you can also just download a binary. Imporatant detail to note is to remember to add git-tfs.exe to your path.
Another important thing is that you need Team Explorer installed because git-tfs uses tf.exe to sync back to tfs. But if you are already using Visual Studio (not Visual Studio) you already have it installed.


Now you want to clone a repo to start working with the code. There are a few ways to get started.

1. Clone the whole history
2. Quick clone

### Clone the whole history

This is the natural choice if you want to have the whole history locally, there are a few drawbacks though. First of all if the repo already has a lot of history this process will take a long time, as in minutes to potentially hours. As this 

* Backup -
    * THis is a sensitive area but important
    * Can be to a network drive

### Create folder on network drive for repos

in this case my networkdrive is x:

``` 
$ x:
$ mkdir repos
```

create folder for projoct to "host"

```
$ mkdir my-project
```

create new "bear" project

```
$ cd my-project
$git init —bare
```

add the network folder as origin to the working repo

```
$ cd <path to the working repo>
$ git remote add origin file://x:\Repos\my-project
```

push to origin

```
$ git push -u origin master
```

A last useful nugget is managing branches. Managing branches have also been a a bit..

With git-tfs, TFS branches can be managed as regular branches it git. here goes

Pull a branch from tfs:

```bash
git tfs branch --init $/Repository/ProjectBranch
```

this will initialize a git branch with the n


## Caveats

- Pusing to extra remote can be problematic
- Always use rebase - after all tfs only have one branch
- tfs branches - try to avoid