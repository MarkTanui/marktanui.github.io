---
title: "AoC#2"
date: 2022-12-02
draft: false
toc: false
images:
tags: ["AoC 2022", "Log Analysis"]
---

## Aoc [Day 2] ```Log Analysis``` Santa's Naughty & Nice Log

*On the second day of christmas: I helped McBlue analyse log files.*

**Task 2** - Analyse the log files captured from the web server to understand what is happening and track down the Bandit Yeti APT group.

### Log Files
Log files are files that contain historical records of events and other data from an application. Some common examples of events that you may find in a log file:

* Login attempts or failures
* Traffic on a network
* Things (website URLs, files, etc.) that have been accessed
* Password changes
* Application errors (used in debugging)
* and many, many more

A useful log will contain at least some of the following attributes:

1. A timestamp of the event (I.e. Date & Time)
2. The name of the service that is generating the logfile (I.e. SSH is a remote device management protocol that allows a user to login into a system remotely)
2. The actual event the service logs (i.e., in the event of a failed authentication, what credentials were tried, and by whom? (IP address)).


### Common Locations of Log Files
Windows - The Event Viewer
Categories in the log file include: ```Application```, ```Security```, ```Setup & System```.

Linux - /var/log
Categories in the log file include: ```Athentication```, ```Package Management```, ```Syslog & Kernel```.

### Looking Through Log Files

The difficulty in analysing log files is separating useful information from useless. Tools such as Splunk are software solutions known as Security Information and Event Management (SIEM) is dedicated to aggregating logs for analysis.

It is however expensive and takes a lot of time to set up a SIEM. In that case, the grep tool in linux becomes very very useful.

### Grep 101

Grep is a command dedicated to searching for a given text in a file. Grep takes a given input (a text or value) and searches the entire file for any text that matches our input. 

See ```man grep``` for more options to use with the grep command.


###### End of AoC#2