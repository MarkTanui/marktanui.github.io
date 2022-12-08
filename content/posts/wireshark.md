---
title: Wireshark Analysis.
date: 2022-12-06
draft: false
toc: false
tags: ["Network Analysis", "Wireshark"]
---

# Wireshark Filters & PCAP File Analysis.
This piece is a prequel to [PCAP Analysis In 1, 2, 3…go]()

---

Wireshark is a **`free and open-source`** network protocol analyzer. It is used for network troubleshooting, `analysis`, software and communications protocol development, and education. Wireshark provides a graphical user interface (GUI) that allows users to interactively browse and analyze captured network traffic. It is available for various platforms, including `Windows`, `macOS`, and `Linux`.

Wireshark is pre-installed in KaliLinux and Parrot OS. You can however install it in *your OS. Checkout the download page [here](https://www.wireshark.org/download.html)

## Wireshark Filters.

Wireshark provides a large number of capture and display filters that can be used to analyze and filter network traffic. These filters allow users to focus on specific types of traffic or isolate packets of interest.

The two types are: `Capture` & `Display` filters.

### Capture filters:
Deviates from the standard Wireshark filter syntax(display filters), as there are no dots in between terms and no comparison operators, e.g. `tcp port 80` instead of `tcp.port == 80`. 

Here are some examples of common capture filters in Wireshark:

* "`host x.x.x.x`" - This filter captures packets to or from a specific IP address (replace x.x.x.x with the desired IP address).
* "`port x`" - This filter captures packets with a specific port number (replace x with the desired port number).
* "`tcp`" - This filter captures TCP traffic.
* "`udp`" - This filter captures UDP traffic.
* "`icmp`" - This filter captures ICMP traffic.

### Display filters:
After capturing packets, display filters are used to separate the traffic from the general noise.
Display filters follow a different syntax from the capture filters. The display filters allow use of dots in it's syntax. 
Expressions in display filters specify the protocol or header to use for filtering. Comparison, equal and logic operators are 
also used together with this filters.

**i.e:** 
`http` - displays http packets only,
`tcp.port == 80` - displays packets that have destination/source of port 80
`tcp.window_sixe_value >= 8000` - displays packets with a window size value of atleast 8000 bytes.

## Wireshark PCAP File Analysis.

Wireshark is really powerful and provides a summary of the PCAP immediately when it's loaded. The statistics come in handy when you start the mannual search to get specific details.

### Viewing Capture Statistics:

Different statistics about the traffic in the capture file – such as the percentage `proportions of protocols`, the `amount of bytes` transmitted to different `hosts`, the `IP addresses` of all the hosts that has appeared in the capture. They are helpful in certain scenarios, such as finding potential exfiltration vectors and identifying the exfiltrating host based on network usage.

This section will discuss **three** of the statistics windows:

#### Protocol Hierarchy,
-  Organized from layer 2 to layer 7, this hierarchy displays the percentages of the packets/bytes in the protocol conversation, against the entire traffic.

#### Conversations,
- Provides information on the traffic, including the hosts(source & destination), ports, bytes and packets in the conversation.
- This window is great for identifying the different MAC or IP addresses that a host has communicated with, and the volume of traffic between them.

#### Endpoints.
- Shows all of the different hosts that appear in the capture and the amount of packets/bytes they sent and received. This window is useful in sorting hosts by their network activity, by either transmission or receiving volume, or by both. 

Thanks for reading that.
Checkout the sequel to this [here](https://marktanui.github.io/posts/wireshark-analysis)

---
---
That was fun.
Follow me on twitter [@themadbit](https://twitter.com/@themadbit)