---
title: "AoC With Go"
date: 2023-12-28T23:15:58Z
tags: ["golang", "learning"]
---

This year (2023), I participated in the Advent of Code challenge (an advent calendar of programming puzzles). These are my thoughts on the experience.

## Background

Last year (2022), I also tried to complete the challenge. I had heard of it from a friend that was excited to start. Back then, the DSA concepts were far more fresh in my mind than this year, and I was working with a language I was quite familiar with (Python). Even so, my attempt ended on the 16th. I remember the coffee shop I was in as I struggled to think of a solution to the problem for the better part of the day. I gave up and went hiking instead. I didn't get back to it later or even look at other people's solutions. I didn't attempt the rest of the days. I just wanted to forget about my failure. It left a bitter feeling.

## Go

As I've endeavored to learn Go relatively recently, I thought I would try my hand at this year's challenge while practicing DSA in the language. Although I felt pretty comfortable with what some people call the easiest language to pick up, I encountered many confusing and frustrating obstacles. Just as a note, I have no authority to go on this rant-tangent, but here I go anyway.

Go is simple. Go is boring. It's designed to be simple and boring. I thought I was ok with that. When learning Go, I felt I understood most of the concepts of the language with ease, and I was able to use that knowledge to build some projects. But I never really had the need for fancy algorithms, and didn't stray far from the language built-ins and standard library. Every now and then, I would do some leetcode problems, but I would do them with Python. I mean, the language is a perfect fit for those types of problems. This year, I found out just how much less fit Go is for those types of problems.

Go doesn't have a hashset. Go doesn't have a deque, a queue, a heap, a stack, a bimap, a graph, a trie, a tree. Go doesn't have anything but a dynamic array and a hashmap. To use these missing, basic data structures, you need to either find a third-party package that provides a generic-compatible structure that implements the methods you need, or you have to whip out a textbook for reference and write the thing yourself. What I found was that the third-party implementations of the essential data structures in Go were so wildly varying in style from one another and only provided a fraction of the methods/functions needed for actual utility. So I wrote my own. Reinventing the wheel seems to be the status quo amongst Go devs.

I mean ok... I get it... Go only recently (1 year ago) implemented generics. The Go team seems to be experimenting with and trying to figure out how they want the standard library implementations of these structures to look like before they release them. They have a backwards compatibility promise to worry about. But to me, a newcomer to the language, it just feels like it's incomplete.

## Stars

Anyway, I'm mostly proud of my performance this year. I worked through most of the problems myself, being spoiled mildly on a few days with some visualizations from r/adventofcode, and looking at hints for a few others. I'm pretty ok with having used hints, although I'm sure some would call it "cheating". To that, I say: it's a for-fun challenge that rewards digital, golden stars. Also, I doubt anyone would think it would be cheating to use a stackoverflow result from a search.

I ended it with 47 stars, only missing part 2 of day24 and both parts of day25. I just don't have the knowledge required to complete them, my google-fu failed me, and the hints I found were too mind boggling. I need to study some math. I learned a ton from the challenge and it kept me busy at my many cafe trips (I apologize to the people that had to sit next to the crazy dude mumbling to himself while scratching his eyebrow and fistpumping the air intermittently). After finishing each day, I looked at solutions on the subreddit, and watched some youtube videos from Jonathan Paulson (Python) and Chris Biscardi (Rust). It was nice seeing different perspectives. Sometimes, went back and rewrote an embarrassingly inefficient solution with new ideas. Sometimes, I felt great about my solution.

I like these puzzles far more than leetcode problems, though they are pretty heavy on 2d grid use. I think I'm going to spend some time doing past years' challenges. I'm going to start with redoing 2022 with Python.

## Code

I've put [my code](https://github.com/patrickarmengol/advent-of-code/tree/master/2023) from this year's challenge up for all to see.
