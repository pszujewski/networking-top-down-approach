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

A a transport protocol can provide an application with one or more security services. For example, in the sending host, a transport protocol can encrypt all data transmitted by the sending process, and in the receiving host. A transport protocol (like TCP) might guarantee that a given stream of bytes will be reliably delivered to the end host.  

The main difference between UDP and TCP is in terms of data reliability. This is guaranteed by TCP but not by UDP. UDP is more lightweight. There is no "handshake" step to set up the connection in UDP. You just start sending data via a UDP Socket, but there is no guarantee that all data packets will make it to the destination. So this is ok for video or telephony applications which need faster data transfer but if there is a little bit of data loss it's ok. 

TCP can be enhanced at the application layer with SSL to provide data encryption.

### The Web and HTTP

HTTP defines how web clients request web pages from web servers and how servers transfer web pages (and any other web objects) to clients.

Web "objects" are identified by a URL, which has 2 main components: the hostname of the server that houses the object, and second the object's path name.

Web browsers implement the client-side of HTTP in the context of the web. Web servers implement the server side of HTTP and house the web objects, each addressable by a URL. Popular web servers in clude Apache and Microsoft's IIS. HTTP uses TCP. TCP as a protocol is implemented in the [OS' Network stack](https://stackoverflow.com/questions/40428474/where-is-http-protocol-implementation-in-linux#:~:text=So%20the%20answer%20is%2C%20http%20is%20not%20implemented,implemented%20in%20applications%20-%20some%20client-side%2C%20some%20server-side.). 

HTTP responses include a Last-Modified http header which helps with object caching both in the local client and in network cache servers (aka Proxy servers).

Cookies allow site to keep track of users even though TCP is completely stateless. Cookies include a header line the HTTP request and response messages and a cookie file kept on the user's end system and managed by the user's browser. A cookie might include a user id, for example. The browser passes a cookie header to the server, thereby identifying the user to the server. Cookies can thus be used to create a user session layer on top of stateless HTTP.

Web cache: both a server and a client at the same time. For example, a university might install a cache on its campus network and configure all campus browsers to point to the cache. 

Content Distribution Networks (CDNs) are a particular approach to web caching. A CDN company installs many geographically distributed caches throughout the internet, localizing a lot of traffic for users. Developers leverage cdns as a network. 

A proxy server cache can handle a Conditional GET message from a browser client, sending an HTTP message along to the origin server along with the header:

`If-modified-since: {dateOfLastRcvOfObject}`

If the origin server responds with a `304` `Not Modified`, the cache forwards its cached version on to the browser host. Otherwise, the origin server responds with a `200` and its message body contains the requested internet object. 

### DNS - The Internet's Directory Service

**hostname**s are a "human-readable" way of naming an internet host. **IP addresses** are another way of "naming" a host for the purpose of sending or receiving internet traffic to or from that host. An IP Address consists of 4 bytes like `121.7.106.83`, where each period separates a byte within the address. An IP Address tells us within which network in the "network of networks" we should direct our requests to. 

The main task of the internet's **domain name system** is to translate hostnames into IP Addresses. The DNS is 1) a distributed database implemented in a hierarchy of **DNS servers**, and 2) an application-layer protocol that allows hosts to query the distributed database (client-server paradigm). The DNS servers are often UNIX machines running the Berkeley Internet Name Domain (BIND) software. The DNS protocol runs over UDP and uses port 53. All DNS query and reply messages are sent within UDP datagrams to port 53.

In HTTP, the browser extracts the hostname, passing it off to the client-side of a DNS application, which queries the DNS server to translate that hostname to an IP address. Once the browser receives the IP address from DNS, it can initiate a TCP connection to the HTTP server process located at port 80 at that IP address. 

DNS can also perform **load distribution** among replicated servers. In this case, DNS maps a set of IP addresses to a hostname. It rotates between these when providing IP addresses to clients. 

The DNS is distributed and hierarchical by design. No single DNS server has all of the mappings for all of the hosts in the internet. Three classes of DNS servers: root DNS servers, top-level domain (TLD) DNS servers, and authoritative DNS servers. So for top-level domain, you might have `.com` DNS servers, `.edu` DNS servers, etc. Root name servers provide the IP Addresses of TLD servers, etc. The network infrastructure supporting a TLD can be large and complex.

Each ISP also has a local DNS server. When a host connects to an ISP, the ISP provides the host with the IP addresses of one or more of its local DNS servers. Avery basic outline of how a DNS message results in translating hostname to IP address:

host requests example.com IP address to Root server -> Root DNS Server sends DNS messages with address to TLD `.com` server -> host requests IP address to TLD server -> TLD server sends back the address to the Authoritative DNS server -> so on...

DNS servers store and send **resource records** like:

`[Name, Value, Type]`

`relay1.bar.foo.com, 145.37.93.126, A`, where record type `A` is a simple hostname to IP Address mapping. A DNS server provides a `A` type of record when it is an authoritative DNS server for a particular hostname.

Type `NS` records map a domain name to an authoritative DNS server capable of supplying the `A` record for that domain.

`foo.com, dns.foo.com, NS`

The DNS server providing this `NS` record would also provide an `A` record for this DNS server:

`dns.foo.com, 128.119.40.111, A`

A type `CNAME` record provides the canonical hostname for an alias hostname, i.e:

`foo.com, relay1.bar.foo.com, CNAME`

By providing a CNAME record to your DNS server(s), you can alias a hostname.

A type `MX` record does the same thing as a `CNAME` record but for mail servers instead. You can have the same aliased name for your mail server as you do for another server, such as the web server. 

`foo.com, mail.bar.foo.com, MX`

A DNS "reply" can have multiple IP Addresses, for example, for replicated web servers.

A **registrar** is a commercial entity that verifies the uniqueness of a domain name and enters it into the distributed DNS database. These registrars are accredited. 

So you might register the following DNS records with a registrar:

```
(networkutopia.com, dns1.networkutopia.com, NS)
(dns1.networkutopia.com, 212.212.212.1, A)
```


[p. 175 Top - 2.5 Peer..]

## Approach 

Use 7th edition text book pdf and watch youtube lectures based on the 8th edition. Use "resources" found below to spplement learning as it makes sense. 

## Resources

Rent e-text book for 4 months
https://www.pearson.com/en-us/subject-catalog/p/computer-networking/P200000003334/9780135928615

https://www.pearsonhighered.com/cs-resources

https://media.pearsoncmg.com/aw/ecs_kurose_compnetwork_7/cw/

https://gaia.cs.umass.edu/kurose_ross/online_lectures.htm

https://gaia.cs.umass.edu/kurose_ross/interactive/
