+++
author = "Jakob Højgaard"
categories = ["hugo","blogging"]
date = 2018-02-21T12:00:00Z
description = ""
draft = true
slug = "..."
tags = ["hugo", "blogging"]
title = "Moving to Hugo and Github pages"

+++
## Why

Well sometimes I just need to change something, and to be completely honest, that's probably the main reason for this change. However I do also have a few other reasons that just might be of value to you. Previously the blog was hosted on a [DigitalOcean]() droplet and using Ghost blogging and had a Postgres database for storage. It was fairly simple to setup and maintain, but the thing that was not that smooth was keeping up with updates from Ghost. It wasn't to be fair a lot of work, but still some work and in the end that made me just leave it and not update anything. Because of that I started thinking about moving to the official Docker image for Ghost. That would make it more or less pain free, but then another reason kept me from doing that. 

The thing is that I have never really appeciadet the editign experience in Ghost. Not that it in any way is bad, in fact I think it's amazing! It's just not for me. THe reason is that I kind of a editor and terminal guy (these days VS Code and Hyper) and having to write in a web broweser is just not for me. Not completely sure why, but drak theme plain editor and controlling versioning with git and terminal, just clicks for me.

So enter static pages and generators.

## Picking a generator, a theme and hosting

There are many static generators out there ... Hugo

Next thing is picking a theme... Cactus bacasuse of simplicity and I'm scandinavian


## How

* Install Go
* Install Hugo
* Download/clone/copy theme
* Migrate content
  * editing in existing posts to because of different interpretation of md i.ie `####`
  * Images
* Setup github pages
  * docs folder - easiest
  * publish dir
  * cname
* Add cloudflate for caching
  * dns
  * cache all (make sure to purge when publishing)

## A few tweaks

permalink to match existing url's
    
```
[permalinks]
  post = "/:slug/"
  blog = "/:slug/"
```

## Resources

- [Ken Cochrane's blog](https://www.google.com.au/url?sa=t&rct=j&q=&esrc=s&source=web&cd=5&cad=rja&uact=8&ved=0ahUKEwiq6crMmtjWAhVGmpQKHXlEA6QQFgg_MAQ&url=https%3A%2F%2Fwww.kencochrane.net%2F2016%2F11%2F20%2Fi-rebuilt-my-blog-with-hugo-and-moved-to-netlify%2F&usg=AOvVaw0YLFz-0fayRaiV4IWVn19K)