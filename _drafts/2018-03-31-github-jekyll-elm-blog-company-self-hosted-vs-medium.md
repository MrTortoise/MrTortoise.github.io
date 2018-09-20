---
layout: post
title:  "Self hosted blog vs hosted (Eg github pages, medium et al)"
date:   2017-03-05 21:27:48 +0000
categories: blog hosting
---
# Self Hosting blog vs Github pages (and maybe Medium)

## The problem

1. I cannot get github pages to highlight elm syntax at all.
1. On the back of this I got into building a local Jekyll setup and try to fix the problem. I could write a few thousand word on what I discovered (short version is that Jekyll is actually pretty good for hosting a simple site describing services and a blog attached) but basically neither does exactly what I want.
1. One of the goals of writing blog posts is to figure out what I want to be doing as a business IE find the areas that I care about and think I offer some kind of tactical advantage.

In getting into this I am not going to stick to the chronological order of my discoveries. From what I did I think I came to the conclusion that if Jekyll is good for you then github pages is probably good for you too (unless you managed to solve a specific problem in Jekyll that github does not support Eg need to use a non rouge/kramdown/redcarpet syntax highlighter)

## Home rolling a jekyll setup

Pros:

- If you have hosting, need some customization github pages doesn't support then this is probably pretty good
- Can build a really flexible site layout and there are literally hundreds of templates out there
- Can easily take a gem based template and override parts
- Good docs and tons of tutorials

Cons:

- you probably want to go and install [rbenv](https://github.com/rbenv/rbenv) and whatever else it suggests you install.
- If it's not out of the box in github what makes you think you are going to do any better?
- Need to figure out own hosting / deployment

## Github

Pros:

- It just works - you can have a live post in about 5 minutes and your second in a few minutes after that.
- Can very easily write and add blog posts and get syntax highlighting for the vast majority of languages out there.
- Can even host a custom domain
- Good docs

Cons:

- Can be less than obvious what the error is when it goes wrong - at which point you probably install everything you need to set up your own anyway (CI/CD withstanding)
- If it doesn't work well you may as well (knowledge wise) just installed jekyll yourself and built your own.

## Medium

Pros:

- Works, popular site

Cons:

- You give away your traffic
- Lost control oer your content 


