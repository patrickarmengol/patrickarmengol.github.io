---
title: "Projects"
menu: "main" # add link at top of home page
layout: "single"
---

# Projects

This page consolidates my projects and project ideas into one place for quick reference. 

---

## Ongoing/Completed

(sorted newest to oldest)

- **reciplease** - API to scrape recipes from your favorite site and output to simple, clean markdown
    - [github](https://github.com/patrickarmengol/reciplease) --- [demo](https://reciplease-frontend.up.railway.app/)
    - FastAPI backend
    - Vue.js frontend (just a demo)
    - uses recipe-scrapers library for scraping
    - uses jinja templates for markdown output
    - live demos are deployed to railway with docker
- **etherealink** - URL shortener API for self-destructible and expirable links 
    - [github](https://github.com/patrickarmengol/etherealink) --- [demo](https://etherealink-frontend.up.railway.app/)    
    - FastAPI backend
    - Vue.js frontend (just a demo)
    - create "short" links
    - set expiry datetime
    - set total number of clicks before link becomes inactive
    - use admin link to delete link or update expiry/num_clicks (account-less auth)
    - live demos are deployed to railway with docker
- **pptoml** - library and CLI tool for parsing, validating, modifying, and updating pyproject.toml files 
    - [github](https://github.com/patrickarmengol/pptoml)
    - just learning about python package management and toml
    - maybe prototype for alternative to hatch/poetry
- **haikugen** - generate haikus with markov chains trained on books available from Project Gutenberg 
    - [github](https://github.com/patrickarmengol/haikugen)
    - just learning a bit of NLP
- **haikuobs** - detects haikus in text; search tweets for valid haikus 
    - [github](https://github.com/patrickarmengol/haikuobs)
    - fun twitter api project before twitter dies
- **solidbackground** - generate solid color background image 
    - [github](https://github.com/patrickarmengol/solidbackground)
    - utility i actually use to generate my desktop background
    - can maybe expand this to generate art based on colorscheme
- **imgcolorplot** - rgb color space cube plotter 
    - [github](https://github.com/patrickarmengol/imgcolorplot)
    - learning about colors
- **infinitemonkey** - brute force hello world 
    - [github](https://github.com/patrickarmengol/infinitemonkey)
    - learning about multithreading
- **qrclock** - useless qr code clock 
    - [github](https://github.com/patrickarmengol/qrclock)
    - learning about Python GUI
    - silly project inspired by Atomic Shrimp
- **EPstripper** - defang malware samples by changing their Entry Point 
    - [github](https://github.com/patrickarmengol/EPstripper)
    - small utility inspired by the book Malware Data Science
- **pegreet** - static analysis and feature extraction of Portable Executable files 
    - [github](https://github.com/patrickarmengol/pegreet)
    - actually useful cli app for malware analysis and data science

---

## Ideas

### CLI

- bt client
- earthquake notification bot
- uwuicode
- scrape tea prices

### Web

- kanji of the day
- srs flashcards site like kanji.koohii
- endangered species info/tracker
- space news aggregator
- url shortener
- minimal markdown recipe site
- who ya gonna call? db of gov/help lines for each country
- minimal kanban
- youtube sub shuffle
- animaps
- hiking meetup app
- sc build order
- first-contribution gh issue list
- japan or taiwan tea map
- tf2center or old bnet style lobby management

### Creative Coding

- cellular automata simulation
- falling sand siimulation
- ant colony simulation
- matrix falling text
- something like cbonsai
- fractal generator
- atomic model simulation
- animations for algorithms
- generate color theme/palette from image
- korean typing game
- pretty 3d portfolio
- coding train challenges
- multiple neighborhood cellular automata

### Data Analysis/Science

- scrape something to create a dataset
- pyproject.toml data analysis
- no starch press data analysis
- air quality data analysis
- nobel prize winner data analysis
- arxiv submission data analysis
- TM COTD data analysis
- hydrogen fuel data analysis
- data vis dashboard with panel