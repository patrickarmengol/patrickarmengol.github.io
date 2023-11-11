---
title: "Golang Learning Plan"
date: 2023-07-22T01:47:07Z
tags: ["backend", "golang", "learning"]
---

## Why

**Golang** (yes, I think I'm going to call it golang because it makes it easier to search and because I associate the word _go_ with the [board game](<https://en.wikipedia.org/wiki/Go_(game)>)) is a nice language. It seems simple but capable. Looks like I should be able to use it to dive deeper into things like systems programming, devops, sre, concurrency-driven apps, and most importantly, backend web dev.

Up until now I have been using python for basically anything and everything and I'm quite comfortable with it, but it often doesn't really feel like the best tool for any job other than maybe data science/analysis. If I want to get serious about backend web dev, golang seems like a no-brainer. My foray into exploring python's options for backend has left me with little satisfaction. The most popular frameworks, _django_ and _flask_, are old and seem to have stalled in development. The most "promising" modern framework the community has chosen is _fastapi_, which is really just a layer on top of _starlette_, with a bus factor of one, and a big problem with community submitted contributions/issues. The framework that should be on top, in my opinion, is _litestar_. Its fairly new, has a great community and group of devs behind it. I tried building a more sophisticated app with it, but I ran into a multitude of python-related problems outside of the framework that just annoyed me, so I abandoned the project.

Golang, on the other hand, seems to be more suitable for the kinds of things I want to do. The general consensus/recommendation for golang projects, particularly web dev projects, is to heavily utilize the standard library, and build out most of the functionality yourself so that you know exactly how everything in your project works. This is greate because I don't quite know too much about certain concepts associated with backend web dev, like database interactions, session management, caching, quirks of browsers, and have been relying on magic abstractions provided by the python frameworks and ORMs.

## Goals

I want to be proficient at golang. I want golang to be my default for backend web dev work and cli apps.

I want to build a few sites using golang + htmx that I can feel proud of; avoiding tutorials and copying other open source projects.

I want to get a job that heavily involves coding in golang.

## How

Books. Always books.

---

## Books

- [x] [Learning Go](https://www.oreilly.com/library/view/learning-go/9781492077206/)
- [x] [Let's Go](https://lets-go.alexedwards.net/)
- [x] [Let's Go Further](https://lets-go-further.alexedwards.net/)

## Exercises

- [ ] [gophercises](https://gophercises.com/)
- [ ] [fly.io distributed systems challenge - Gossip Glomers](https://fly.io/dist-sys/)
- [ ] [codecrafters](https://app.codecrafters.io/catalog)

## Online Resources

- [standard library](https://pkg.go.dev/std)
- [go by example](https://gobyexample.com/)

## Blogs

- [Alex Edwards](https://appliedgo.com/blog/go-project-layout)

## Podcasts

- [go time](https://changelog.com/gotime)
