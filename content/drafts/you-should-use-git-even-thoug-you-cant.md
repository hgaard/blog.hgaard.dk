+++
author = "Jakob Højgaard"
categories = ["git", "versioncontrol", "tfs"]
date = 0001-01-01T00:00:00Z
description = ""
draft = true
slug = "you-should-use-git-even-thoug-you-cant"
tags = ["git", "versioncontrol", "tfs"]
title = "You shoudl use git even though you can't"

+++

# You shoudl use git even though you can't

## Intro

## Why

## How

* Backup -
    * THis is a sensitive area but important
    * Can be to a networkdrive

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

## Caveats

- Pusing to extra remote can be problematic
- Always use rebase - after all tfs only have one branch
- tfs branches - try to avoid