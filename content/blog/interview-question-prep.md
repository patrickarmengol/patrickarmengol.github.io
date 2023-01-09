---
title: "Interview Question Prep"
date: 2023-01-07T05:34:35Z
tags: ["learning", "meta"]
draft: True
---

## Programming / Python

### General
- what programming languages do you prefer to work with and why?
    - python, bc it's powerful, easy to prototype with, easy to write quick scripts with, and have robust libraries for working with data
    - since it's a popular language, it makes it easy to collaborate with other programmers
- sofware development methodologies?
    - agile, waterfall
- ci?
    - devops practice where developers regularly merge code changes to central repository, after which builds and tests are run
- duck typing
    - Duck typing is a concept related to dynamic typing, where the type or the class of an object is less important than the methods it defines. When you use duck typing, you do not check types at all. Instead, you check for the presence of a given method or attribute.
    - runtime duck typing with hasattr() vs runtime goose typing with isinstance() vs static type checking with external tools
- software development life cycle?
- concurrency vs parallel
- multithreading vs multiprocess

### OOP

- what is object oriented programming
- what are the differences between OOP and functional programming?
- what is a class?
- what is an object?
- what is a constructor?
- what is an attribute?
- what is a class method?
- what is a static method?
- what is multi-inheritence?
- what is self?
- what problems can arise from multi-inheritence?

---

## Backend

### Databases
- nosql vs relational?
    - relational
        - structured, tables and columns
        - consistency, data fits models, easy to understand what is in the db
        - relations between objects in multiple tables
        - security, ensure field constraints, apply encryption or uniqueness to columns
        - ease of backup and recovery
        - storage is concentrated
        - scale vertically, better machine (horizontal can only have read replicas, not write)
        - more traditional workloads
        - accessed through raw queries or ORMs with direct db connections
        - used when:
            - access patterns aren't defined
            - perform flexible queries
            - perform relational queries
            - enforce field constraints
            - you want to use well documented access language SQL
    - nosql
        - key-value, each key maps to one value, simple
        - column store, data organized into columns, optimized for performance
        - graph, shows network rep of obj in db
        - document store, group of documents is collection
        - structure more flexible, queries are less flexible
        - need to know the key when performing query
        - high scalability, add more partitions
        - access through rest apis or crud in vendor specific languages
        - cost effective
        - use when:
            - access pattern is defined
            - primary key is known
            - data model fits (graphs)
            - high performance, low latency

### APIs
- what is an api and why do we use it?
- what is a rest api?
- what is a soap api?
- what is a restful web service? what are its features?
- what are disadvantages of restful web service?
- what are restful payloads?
- what markup language is used in restful api?
- what is xml? json? diff?
- what is resource in rest? what is a way to represent it?
- what is adv of using rest apis?
- what is statelessness in rest?
- what is URI?
- what is CORS?
- what is postman? why do we use it?

### HTTP
- what are http methods
    - difference get post
    - difference put patch
- http status codes?
- components of http requests and responses
- is it possible to send a payload in get or delete methods?
- what is the max payload size for post?


## Frontend
