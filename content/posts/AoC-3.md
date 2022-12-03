---
title: "AoC#3"
date: 2022-12-02
draft: false
toc: false
images:
tags: ["AoC 2022", "OSINT"]
---

## [Day 3] 
```OSINT``` Nothing escapes detective McRed.

*On the third day of christmas: I find the source code of Santa's website.*

Task 3: Through OSINT, I find the registar of Santa's website and most importantly, the source code of Santa's website. Oh my, 
the source code has the **config file exposing credentials!!**

### OSINT
OSINT is short for Open Source Inteligence. 

This is the process of gathering and analysing data that is publicly available.
Information or the digital fingerprint left behind unknowingly is sometimes indexed making it easier for threat actors to find and use it.
Search engines if queried appropriately, give more accurate info that can be used for identity theft and much more.

### OSINT Techniques

The most common technique used is dorking. This includes: google (replace with other search engine) dorking and github dorking.

Special filters are used to limit and enhance the search scope. This helps you to get filtered information which can be used to make decisions for escalating 
of an attack.

Such filters(google dorks) include:
* inurl: - to check for string in the url of result.
* type: - to specify the file type to be searched.
* site: - specify the site to check search string in.

### Other tools

Tools like `whois`, `nslookup`, `theharvester` and others can be used to automate the process of finding useful information(emails, calendar, spouses,identification numbers... e.t.c) on a target.


###### End of AoC#3