---
title: Practical Analysis of PCAP Files
date: 2022-12-08
draft: false
toc: false
tags: ["Network Analysis", "Wireshark"]
---

# PCAP Analysis In 1, 2, 3...go:

This piece is a sequel to [`Wireshark Filters & PCAP File Analysis.`](https://marktanui.github.io/posts/wireshark)
I'd recommend you read that first, to farmiliarize yourself with some terms and concepts. Otherwise, go ahead.

---

I have two files that I'm required to do an analysis on, and thereafter, answer some questions. What can PCAP files help us discover? Let's find out.

Find the two PCAP files [**here**](https://github.com/MarkTanui/marktanui.github.io/tree/main/assets/posts/wireshark-sbt)

### PCAP 1
***1. Which protocol was used over port 3942?***

I start by looking at the `Statistics` of the PCAP.
I discover that there are two main protocols(`tcp & udp`) in the conversation.
Using the two protocols I specify a filter to get the protocol used over port 3942.

![](https://i.imgur.com/6vxnxZQ.png) 


***2. What is the IP address of the host that was pinged twice?***

`ping` uses the ICMP protocol. Knowing this, I specified the `icmp` display filter that showed all the ICMP requests and responses.

![](https://i.imgur.com/JBGbNMo.png)

From the displayed packets above, `8.8.8.8` & `8.8.4.4` were pinged twice. However, only `8.8.4.4` received the request and replied successfully.

***3. How many DNS query response packets were captured?***

It's prudent to highlight that, I use **key words** in the questions to determine which filter I would use. In this case, the word `dns` prompts me to check if there's a `dns` display filter.

Oh my! There is. What do I get:

![](https://i.imgur.com/X8U9dBD.png)
Well, I get over 200 packets. I'm now close to getting the dns query responses captured.

To get more specific packets, the `dns` filter has some options that can be chained together with it:

`dns.flags.response == 1` - This filter checks through the over 200 dns packets, to determine which packets have a response flag in them. The `"== 1"` ensures that only dns packets with a response flag are displayed.

After using that filter, `90 packets` were displayed.


***4. What is the IP address of the host which sent the most number of bytes?***

The Endpoint statistics was the saviour. Wireshark's pre-analysis of PCAP files, lists all discovered hosts along with the number of bytes that each sent.
So I did: `statistics` --> `Endpoints` --> `TCP` and then sorted the list in ascending order.

![](https://i.imgur.com/oHgZlw8.png)

---


## PCAP 2

***1. What is the WebAdmin password?***

`http(s)` is the protocol used for GET/POST and other requests in the world wide web.
I figured that this should be the first filter to apply.

![](https://i.imgur.com/u9quAW6.png)
And yes, a http `GET` request was sent for `/password.txt` - `http` traffic is always in plain text making it unsafe to use it in sites that require logins/credit cards or other credentials.

Following the `http` stream, the password is there in plain sight!

![](https://i.imgur.com/70RKN58.png)



***2. What is the version number of the attacker’s FTP server?***

Used the `ftp` display filter.
Followed the FTP stream, and got the version.

![](https://i.imgur.com/9793TDu.png)


***3. Which port was used to gain access to the victim Windows host?***

Following through the PCAP file, I noticed that just before the file transfer started, there was an attempt to connect to victim's `port 8081`. Using that lead, I found that a response from `8081` provided the attacker an `ftp server`.

I concluded that this port was used to gain access. Is there another way around this? Kindly share it.

***4. What is the name of a confidential file on the Windows host?***

Filtering and following streams is the rule of this game: pcap analysis.
For this question, I decide to use the `data` display filter. Why? I figured out that if I'm supposed to get a file name, then it would as well mean that there's a data transfer that occurred.

![](https://i.imgur.com/QRtYc67.png)
Very nice! Down to 103 packets.

Next, I decided to follow the `tcp stream`.

![](https://i.imgur.com/6dKnEB5.png)

With that I could see all the commands used on the victim's machine, and their output as well. I also could tell the confidential file in the machine. Can you?

***5. What is the name of the log file that was created at 4:51 AM on the Windows host?***

Easy-Peasy!
It's in plain text from the above stream.

![](https://i.imgur.com/sGNR1P1.png)


---
That was fun.
Follow me on twitter [@themadbit](https://twitter.com/@themadbit)
