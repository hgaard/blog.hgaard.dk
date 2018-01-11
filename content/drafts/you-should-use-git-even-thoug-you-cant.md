+++
author = "Jakob Højgaard"
categories = ["git", "versioncontrol", "tfs"]
date = 2018-01-10T00:00:00Z
description = ""
draft = true
slug = "you-should-use-git-even-thoug-you-cant"
tags = ["git", "versioncontrol", "tfs"]
title = "You should use git even though you can't"

+++

## Why

As a consultant I work in places where source control is not always updated to the latest version. This sometimes means that git is not the preferred tool for source control.

But just because you can't control the infrastructure of your work place, don't let that be an excuse to stick with suboptimal tools to do your job. You are better than that!

My main gripe with  TFS or any centralized source control for that matter is the branching story, lack of easy branching and sharing of these really inhibits a good flexible CI/CD pipeline. The server part of this is a fundamental problem with choosing TFS and cannot be solved without changing away from TFS, hence I will not discuss this further in this post. Another almost as severe problem is the lack of local history and the lack flexibility caused by that. I guess I'm just no longer comfortable not being able to commit many times a day without having to think about how I might disturb my team mates.

Luckily there is actually a tool to bridge this. Enter [git-tfs](http://git-tfs.com/)

## What

Well as the name implies it's a git to tfs and tfs to git bridge. Which kinda makes it possible for you to work with regular git locally and "just" have tfs acts as your remote repository. There are a few caveats to be aware of and I have outlined some in the end of this post.

## How

First of all you need to install git-tfs. Follow the instructions [Here](https://github.com/git-tfs/git-tfs). I usually use [Chocolatey](https://chocolatey.org/) to install my development dependencies if possible. You can also just download the binary. An important detail is to remember to add git-tfs.exe to your path.
An important thing to note is that you need Team Explorer installed because git-tfs uses tf.exe to sync back to tfs. But if you are already using Visual Studio (not Visual Studio Code) you already have it installed.

Next step, to clone a repo and start working with the code. There are a few ways to get started.

1. Clone the whole history
1. Quick clone
1. Clone from specific changeset

### Clone the whole history

This is the natural choice if you want to have the whole history locally, there are a few drawbacks though. First of all if the repo already has a lot of history this process will take a long time, as in minutes to potentially hours.

```bash
git tfs ... clone
```

### Quick clone

If you don't want to wait that long and can live without previous history, just quick clone. This will essentially just get latest and initialize a git repo from there.

```bash
git tfs quick-clone
```

### Clone from specific changeset

Last options is somewhere in between. To clone from a specific changeset in TFS. And of course the longer back you go the longer time it will take

```bash
git tfs clone ... -c id-of-changeset
```

### Working with the repo

After you have successfully cloned the repo, you can start working with the code in the repo just as if it was an ordinary git repo. That is just until you want to pull changes from the remote or push your changes back to the remote.

### Pulling from remote

This is almost like just plain git, just adding `tfs` after the `git` command. However there is one thing to be aware of here. Since TFS keeps a linear history it is strongly encouraged to always pull changes with the `-r` or `--rebase` switch.

```bash
git tfs pull -r
```

### Pushing back to to remote

The semantics here differ a bit from git semantics and aligns closer with TFS as the command (there are more ways to do this - but this is the way I prefer). The reason for this is that git-tfs has to replay any local changes against TFS as separate checkins, thus the command is called `rcheckin` or recursive checkin

```bash
git tfs rcheckin
```


## Backup of local repo

When it comes to source code I'm very paranoid so having changes laying around on my local machine only, tend to freak me out quite fast. So sometimes I want to be able to backup my local changes without having push my changes to the main branch. Luckily it's very easy to add multiple remotes to a git repo and it does not even have to be anything else than a disk drive. Since most of the places I work from have personal network drives mapped, this is an easy way to add a second remote and in most cases a network drive will also be backed up. Now it might be tempting to use Dropbox, google drive or OneDrive for this, but remember if you working from a closed network this will can accidentally expose code publicly and you don't want to be the one responsible for that.


### Create folder on network drive for repos

in this case my networkdrive is x:

```bash
x:
mkdir repos
```

create folder for projoct to "host"

```bash
mkdir my-project
```

create new "bear" project

```bash
cd my-project
git init —bare
```

add the network folder as origin to the working repo

```bash
$ cd <path to the working repo>
$ git remote add origin file://x:\Repos\my-project
```

push to origin

```bash
$ git push -u origin master
```

One thing to note here is that if you are not very careful about ensuring a linear history locally (do rebase) pushing to a second remote can become difficult and can result in unexpected merge conflicts. But remember the second remote in this case is just a backup and is not shared with anyone, thus you can safely force push and not care about the conflicts (I know one should never really need to force push).


## Managing branches

A last useful nugget is managing branches. Managing branches TFS have alway felt a but clunky to me and I have multiple times experienced code on one branch referencing code in a different project.

With git-tfs, TFS branches can be managed as regular branches it git like this.

First to find the branches to pull call `list-remote-branches`.

```
git tfs list-remote-branches  http://tfs-server
```

Pull a branch from tfs:

```bash
$ git tfs branch --init $/Repository/ProjectBranch
```

This will initialize a git branch with the name corresponding to the branch path in TFS.


## Caveats

- Pusing to extra remote can be problematic
- Always always use rebase - after all tfs only have one branch
- tfs branches - try to avoid
- Always use rebase - after all tfs only have one branch
- tfs branches - try to avoid


Well off you go now. Do it!

