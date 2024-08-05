# Computer networking: a top-down approach

The book breaks down the "layers" in modern computer networking, starting at the "top" with the application layers and working "down" to the physical layers.

"An internet focus" pg 8

## Chapter 1: Computer Network and the Internet

The internet is a specific network that is in fact a network of networks. The book bases its exploration of networks on the internet.
Note, "servers" typically refers to "machines" connected to the internet that store and transmit information, such as web pages or email messages, to "hosts" or "end systems", such as desktop PCs or laptops.

For example, a "home network" may include many "hosts", such as a laptop, a tv, a fridge etc. These "hosts" may connect to the wider "network" via a base station, router and modem, which are responsible for interfacing with the wider network. 

"hosts" are connected by a network of **communication links** and **packet switches** (routers or link-layer switches). There are many types of communication links made up of different types of **physical media**, including coaxial cable, copper wire, optical fiber, and radio spectrum. Different links can transmit data at different rates, with these **transmission rates** measured in bits/second. Packet switches "direct" packets towards their final destination along the "route".

Data is segmented with header bytes added to each segment. This results in "packages" of information known as **packets** that are sent through the network to be reassembled at its final destination. 

End systems or "hosts" access the internet through **Internet Service Providers (ISP)**, which are contained networks or more packet switches and communication links. There are residential ISPs, cellular data ISPs, etc. Each ISP network is managed independently and runs the IP protocol.

**Services**

The internet could be described as an infrastructure that provides services to applications. Internet applications run on "end systems"/"hosts." They do not run in the packet switches in the network core. So they run on servers and "hosts." Think client web app and REST API HTTP web server. Packet switches facilitate the exchange of data only.

The internet depends on protocols, which fundamentally define specific actions an internet service can take in response to a specific message or "event" it has received. All activity in the Internet that involves two or more communicating remote entities is governed by a protocol. These protocols can be implemented in hardware or sofware. For example, the physical flow of bits between network "cards" and other hardware devices in governed by protocols (i.e standards for interfacing). Protocols in routers determine a packet's path from source to destination. 

**The network edge**

The "edge" here refers to the end systems or hosts in the network. So for the internet that might laptops, smartphones, web servers and email servers. These systems sit at the edge of the internet. Whereas the "network core" refers more to the infrastructure by which data moves on the internet, so we look at switching and routing in networks.

End systems are also referred to as hosts because they host (that is, run) application programs such as a Web browser program, a Web server program (a software package that implements certain network protocols, like http, for interfacing with clients), an e-mail client program, or an e-mail server program. Today, most "servers" reside in data centers.

q: What is the difference between a modem and a router in a home network? A modem brings the internet to your home, has a public IP address and interfaces with a WAN (wide area network). A router brings the internet to your individual devices within your home network, assigns local IP addresses for each connected device and operates a LAN network (local area network). The modem is the router's gateway to the "larger" network. The modem is responsible for interfacing with wider network maintained by your ISP (internet service provider). [SOURCE](https://www.xfinity.com/hub/internet/modem-vs-router)

How do homes connect to the internet? Usually with a Digital Subscriber Line (DSL) or cable. A DSL line is usually supplied by a local telephone company that provides wired local phone access. Thus a customer hooks up a DSL modem to a DSL telephone line (copper wire..) to echange data. 

The residential telephone line carries both data and traditional telephone signals simulataneously, which are encoded at different frequencies. The DSL modem translates digital data into high-frequeny tones for transmission over telephone wires. These "tones" are translated back into "digital data" by a DSLAM in the telcom where your data interfaces with the wider network.

The residential telephone line carries both data and traditional telephone signals simultaneously, which are encoded at different frequencies:
A high-speed downstream channel, in the 50 kHz to 1 MHz band
A medium-speed upstream channel, in the 4 kHz to 50 kHz band
An ordinary two-way telephone channel, in the 0 to 4 kHz band

Question: What does it mean to carry data at "a certain frequency"? What is "frequency" exactly?

DSL makes use of existing local telephone infrastructure, and cable internet access makes use of cable television's existing cable infrastructure. Pg 41 image. In a optical fiber network, optical signals are converted to electrical signals, which can be interpreted as digital data (bits). 

**Physical media**

Examples: fiber cable, coaxial cable, copper wire, radio spectrum for WIFI or satellite radio spectrum, and more. Bits are sent by propagating **electromagnetic waves or optical pulses** across one of these physical media. Transmitter-receiver pairs along the network translate these "waves" or "pulses" into bits/data.

Different medias **guided media** vs **unguided media**. "With guided media, the waves are guided along a solid medium, such as a fiber-optic cable, a twisted-pair copper wire, or a coaxial cable. With unguided media, the waves propagate in the atmosphere and in outer space, such as in a wireless LAN or a digital satellite channel." For more specifics see page 46.

An optical fiber is a thin, flexible medium that conducts pulses of light, with each pulse representing a bit. A single optical fiber can support tremendous bit rates, up to tens or even hundreds of gigabits per second. They are immune to electromagnetic interference and have very low signal attenuation up to 100 kilometers, so they are good for long distance data transfer. 

**To learn more about: the physics behind the electromagnetic spectrum/ physics for networking?**

#### 1.3 The Network Core

In a network application, end systems exchange messages with each other. Messages perform a "control" function (i.e establishing a connection) or can contain data, like an email message or image file. Messages are broken up into **packets** that travel along packet switches. A **router**'s job is to "switch" an incoming packet into an outbound link. 

Each router in the link has a **forwarding table** that maps destination addresses to that router's outbound links. The internet router examines the IP address of a packet and maps this address to the outbound link according to the forwarding table. 

In a circuit switching network approach the switches on the path between end systems maintain a constant connection while sending/receiving data. This is different from packet switching, where packets might be queued up based on traffic in the system. Traditional telephone networks are circuit-switched networks. A connection is called a **circuit**. Telecom networks are largely migrating towards packet switching. 

End systems access the internet via an **access ISP**, which in turn exchanges packets with a regional and tier-1 ISP across the globe if necessary. 

#### Protocol Layers and their Service Models

A layered architecture allows us to discuss a well-defined, specific part of a lage and complex system. Network designers organize protocols (and the hardware and software that implements the protocol) in **layers**. Each protocol belongs to one of the layers. Some common aplication layer protocols include HTTP (which provides for web document request and transfer), SMTP (which provides for the transfer of e-mail messages) and FTP (which provides for the transfer of files between two end systems). Application layer protocols are implemented in end systems. The internet's transport layer transports application-layer **messages** between application **endpoints**. TCP and UDP are 2 internet transport protocols.

End systems implement all protocol layers, which is consistent with the view that the Internet architecture puts much of its complexity at the edges of the network. 

At each layer, a packet has two types of fields: a header field and a pyaload field. The paylod is typically the packet from the layer above.

## Chapter 2: Application Layer

Programs that run on different end systems and communicate with each other over the network. You do not need to write software that runs on network-core devices, such as routers or link-layer switches. 

In client-server architecture, ther is an always-on host, called the server, which services requests from many other hosts, called clients. Most applications consist of pairs of communicating processes (client and server processes). A process sends messages into, and receiveds messages from, the network through a software interface called a **socket**, which is the interface between the application layer and the transport layer within a host. It is also referred to as the API between the application and the network.

To identify the process that is supposed to receive a message, 2 pieces of info need to be specified: 1) the address of the host and 2) an identifier that specifies the receiving process (or socket a process is "attached" to) in the destination host. 1 is the IP address and 2 is the port number. A host could be running many network applications at once. 

A a transport protocol can provide an application with one or more security services. For example, in the sending host, a transport protocol can encrypt all data transmitted by the sending process, and in the receiving host

[p. 123 - middle - 2.1.4 Transport Services Provided by the Internet]

## Approach 

Use 7th edition text book pdf and watch youtube lectures based on the 8th edition. Use "resources" found below to spplement learning as it makes sense. 

## Resources

Rent e-text book for 4 months
https://www.pearson.com/en-us/subject-catalog/p/computer-networking/P200000003334/9780135928615

https://www.pearsonhighered.com/cs-resources

https://media.pearsoncmg.com/aw/ecs_kurose_compnetwork_7/cw/

https://gaia.cs.umass.edu/kurose_ross/online_lectures.htm

https://gaia.cs.umass.edu/kurose_ross/interactive/
