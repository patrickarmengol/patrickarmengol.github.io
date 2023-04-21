---
title: "Editor Hopping"
date: 2023-04-21T00:15:28Z
tags: ["meta"]
---

Throughout my years sitting in front of a screen, there has been one constant: editing text. This post is a short digression into my history with text editors and what has led me to what I'm using today.

## Humble Beginnings - Notepad

My memory of childhood is a bit fuzzy so I don't quite remember much about when I first started using computers. I believe my family's first PC was running some early version of Windows connected to the internet via dialup and all I ever did on it was play games like Freddi Fish and Pajama Sam. Eventually, we upgraded to a Dell desktop running XP and that is when my interest in computers really took off. I have a vivid memory of opening the case up and being stunned by what I saw inside. My feeling was of absolute wonder and curiosity; "how the heck does this all work".

To bring this back to the topic of the post, most of my text editing was limited to Microsoft Word to do homework and perhaps Notepad for a quick note. The main purpose of the computer was for doing work, printing and scanning documents, looking up info on real-world stuff. Of course that didn't stop me from using it for what I thought was the most important thing in the world, playing video games. Mostly I used Notepad to organize my notes about game strategies, names of characters that I often forget, and tracking progress. Back then, most games were also pretty bare and configuration required digging into a _.ini_ file with Notepad.

Of course Windows Notepad wasn't anything special. For me, it served its purpose well and I never even thought that a text editor should require any additional features (some people still believe this).

## Upgrading - Notepad++, SublimeText

Often on the internet, I saw screenshots and videos of people using other text editors that had more buttons at the top and the text was highlighted with fancy colors. I decided to explore some alternatives to Notepad and found Notepad++. It had a familiar name and worked very similarly to Notepad, but had plethora of extra features (most of which I never used). Around this time I also started learning about the web and programming. I learned about building websites with HTML. I used a dialect of BASIC to make silly games for my TI-84 calculator. I started building mods in lua for World of Warcraft. The experience of using Notepad++ for these tasks along with my usual quick notes was more than pleasant; I didn't have any gripes.

Some of the people I interacted with online were fans of Sublime Text, so I decided to give it a try. It was great. It had most of the features I liked from Notepad++, but came with a more modern UI. But... it was paid software, and I didn't see a reason to stick with it over Notepad++.

## IDE Revolution - CodeBlocks, Eclipse, IntelliJ IDEA, Android Studio

When I started properly learning how to program (with C), my instructor required us to use his IDE of choice, CodeBlocks. My first impressions were not great. It felt convoluted to use and the UI looked ancient. The only good thing that came of it was learning how to debug. For C, I eventually I moved on to using gdb on the commandline, but the IDE provided a great visualization of what was happening when I stepped through the code, what values were in the variables, and how the memory looked like.

Later coursework involved Java, so the new instructor required us to use his IDE of choice, Eclipse. I had a similary poor impression of it, though my thoughts on the Java language may have had an overwhelming impact on my feelings. Some of my classmates recommended I look into IntelliJ IDEA and my outlook on IDEs changed completely. I thought why can't all IDEs be this good? Why did I have to struggle through learning how to code with two IDEs that I felt actively tried to ruin my experience.

I also did a bit of Android development using Android Studio, which is built on top of IntelliJ IDEA.

## Devolving - Vim, Atom

During university, I decided to dive into the world of Linux by replacing Windows on my laptop with Arch Linux (btw). Oof, what a struggle that was. But that's not the point of this post. As you may know, a lot of configuration in Linux is done in text files, but Linux doesn't support my preferred text editor that I was using up until that point, Notepad++. Arch Linux (or maybe every Linux distro?) ships with Nano, a fairly simple editor, with quite a few rough edges. Digging into the Linux ecosystem, I found that users were mostly divided into two camps when it came to editor choice: the Church of Emacs and the Cult of Vi. I succumbed to the temptations of Vim. The problem was that I did not learn vim past the basics presented in vimtutor. I didn't configure it, learn many keybindings, or figure how to effectively code with it. I only used it when I needed to edit a simple config text file or bash script.

My later years in university involved a lot of lower level languages like x86 and MIPS assembly as well as hardware description languages like Verilog and VHDL. I also spent some of my free time programming in Python. The IDEs that I was comfortable using didn't really support editing in those languages and I didn't really find any good alternatives. But I needed to have some tool to write my code with. One day, one of my friends was using a cool new editor called Atom, so I gave it a try. I remember thinking it felt a lot like Sublime Text, but had more features, a cleaner design, and had support for plugins that enabled it to act kind of, but not entirely, like an IDE for any language I needed to use. And on top of that, unlike Sublime Text, it was free. What more could I ask for?

## The End Times - VSCode

To the point that I felt I was becoming a shill, I loved using Atom. I dug deep into each of its features and learned how to use it quite effectively. I even built a plugin for it.

But as we know, all good things must come to an end. Eventually, support for Atom started waning and all signs were pointing at it soon becoming abandonedware. At the same time, I started doing a lot of work with Jupyter notebooks at my job. So in comes VSCode to the rescue.

VSCode is a fantastic IDE and there is a huge community behind it. You can do pretty much anything you want to that involes text. Their implementation of Jupyter notebooks is a superior experience in every way. VSCodium is also available for those that don't want to deal with MS telemetry.

## Rebirth - Neovim

Coding for multiple hours every day can fatigue me both mentally and physically. Recently I've been getting frustrated with my coding workflow. Specifically the fact that I have to rely on using a mouse. The rest of my system is set up to use various keybindings for navigation and performing actions (tiling window manager and cli/tui apps).

I always inteded to give vim a second chance as I've often heard the cries of the cult members at the sight of a mouse and I wondered how much better it could be. A certain Rust focused youtube creator mentioned AstroNvim as their editor of choice. It seemed like a VSCode-ified Neovim setup with most of the benefits of both. I put it on the backburner as I was focused on prepping for a job hunt and I thought that learning a new workflow would be too disruptive.

Another video eventually came into my feed: [Neovim With AstroNvim | Your New Advanced Development Editor](https://www.youtube.com/watch?v=GEHPiZ10gOk). The video guides you on the installation and configuration of AstroNvim and explores some of its features. Of course, I could still stick with VSCode and utilize the Neovim extension to get vim motions, but I think it would be better to use the real thing.

For the past few weeks, I have been entranced by the editor and its features as well as figuring out how to effectively use modal editing. It's what I am using to write this blog post. The transition has not been as bad as I anticipated. Still, often when I'm editing something, I stop dead in my tracks to try to figure out what the best way to accomplish it is. I think soon enough I'll be flying.
