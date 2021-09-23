> [CompTIA Network+ (N10-007) Bootcamp](https://www.udemy.com/course/networkplus/) 
> Udemy

[TOC]

# Networks and Their Basic Components
&nbsp;
&nbsp;
&nbsp;
## Overview of Networks

> **Networks**  
> Used to make connections between machines

Not just limited to computers, the internet or Wi-Fi / Ethernet, there's a ton of different types of networks out in the wild. A smartwatch connected to your smartphone via Bluetooth is a type of network, a personal area network.

At one point in history, networks served a specific purpose like a telephone network which only made analog phone calls, but nowadays it's all digital and converged.

> **Converged Network**  
> Combines multiple types of traffic like data, video, and voice in a single network

So with this, we basically can't function without our computers and devices so we expect to have high availability otherwise referred to as **uptime**. As a society we expect that to be 100%, but let's be real that's unachievable as circumstances will arise (but people will still be like, but mah internets).

Instead business networks have established a 99.999%, otherwise known as the five-nines of availability, meaning that a business can have lost availability or **downtime** for _five minutes_ throughout the year.

With these networks up what type of traffic can go through them?

* File Sharing
* Video Chatting
* Web Surfing
* Social Media
* Video Streaming
* Email
* Messaging
* VoIP
* and many more!
&nbsp;
&nbsp;
&nbsp;
## Network Components

What comprises a network?

> Client  
> A device used by an end-user to access the network

A workstation, laptop, tablet, smart TV, smartphone, server and any kind of IoT device like a smart thermostat. Basically, any device that connects to the network.

> Server  
> A device that provides resources to the rest of the network

There are different types of servers depending on what functionality it needs to accomplish. Like an email server, a file server, a print server, a web server and so forth of which can be running on dedicated hardware or specialized software.

> Hub  
> Older technology that connects network devices together (like clients and servers)

This is some old-school hardware -- antiquated and phased out by the switch. They were daisy-chained by going from one hub port to another to provide more ports if needed. A side effect of this was increased network errors as information came in through one hub port and then rebroadcasted out information to all the other ports.

> Wireless Access Point (WAP)【 ͡❛ ͜ʖ ͡❛】  
> A device that allows wireless devices to connect into a wired network

Like your smartphone when it is connected to Wi-Fi, it is connected to a wireless access point, which is essentially a wireless hub.

> Switch  
> A device that connects network devices together

Smarter version of a hub as they can learn which devices are in which port. So instead of rebroadcasting the information out to all ports, it broadcasts it only to the desired port based on who it needs to communicate with. More secure and efficient than Mr. Crotchety (Hub).

> Router  
> Connects two different networks together and intelligently forwards traffic to and from a network based on its logical address (IP Address, Internet Protocol)

Most modern routers rely on IP but there are other types of routing protocols.

> Media  
> Connects two devices or a device to a switch port and is made from copper cable, fiber optic cable or radio frequency waves

This is what connects everything, the cable/media breaks, your networks are gonna be kaput. Not all media is the same, each has their strengths and limitations.

> Wide Area Network (WAN) Link  
> Physically connects two geographically dispersed networks together

Take the internet, it's a massive series of WAN Links. If you were at home and connected to your network but had no WAN Link, you'd have no internet you would only have access to your local network (LAN) inside your home. 

Connects an internal network to an external network.
&nbsp;
&nbsp;
&nbsp;
## Network Resources

How does data get moved around the network? It comes down to two main models:

### Client/Server Model

> Client/Server Model  
> Uses dedicated server to provide access to files, scanners, printers and other resources

Administration and backup is simple, as it's a centralized machine (server) where all the files are sitting on.

#### Benefits

* Centralized Administration
* Easier Management
* Better Scalability

#### Drawbacks

* Higher Cost
* Requires Specialized OS
* Requires Dedicated Resources

### Peer-to-Peer Model

> Peer-to-Peer Model  
> Peers share resource (files/printers) directly with others

Administration and backup is very difficult, as the files are located amongst different machines on the network.

### Benefits

* Lower Cost
* No Dedicated Resources
* No Specialized OS

### Drawbacks

* Decenralized Management
* Inefficient for Large Networks
* Poor Scalability
&nbsp;
&nbsp;
&nbsp;
## Network Geography

So how can we connect to a network? Starting from the smallest type of network to the largest.

### Personal Area Network (PAN)

Smallest type of wired or wireless network and covers the least amount of area (few meters), like Bluetooth and USB.

An example would be the Bluetooth on your mobile connecting to your car stereo, that's an established network between your car and your mobile phone.

A USB hard drive connected to your computer is a personal area network as it is a serial connection.

### Local Area Network (LAN)

Connects components within a limited distance, about 100 meters/300 feet. They can consist of Ethernet (IEEE 802.3) or WiFi (IEEE 802.11) standards.

An example would be the network you connect to at home, that's your home local area network.

### Campus Area Network (CAN)

Connects building-centric LANs across a university, industrial park or business park and covers many square miles and buildings.

### Metropolitan Area Network (MAN)

Connects scattered locations across a city or metro area which can cover about 25 miles. 

### Wide Area Network (WAN)

Connects geographically-disparate internal networks and consits of leased lines or Virtual Private Networks tunneled over the internet. Remember, the internet itself is a WAN, the LARGEST WAN. WAAAAAAAAN

A company with two office at either side of the world can connect their local office private networks with each other via a private WAN connection.