# Computer networking: a top-down approach

The book breaks down the "layers" in modern computer networking, starting at the "top" with the application layers and working "down" to the physical layers.

"An internet focus" pg 8

## Chapter 1

The internet is a specific network that is in fact a network of networks. The book bases its exploration of networks on the internet.
Note, "servers" typically refers to "machines" connected to the internet that store and transmit information, such as web pages or email messages, to "hosts" or "end systems", such as desktop PCs or laptops.

For example, a "home network" may include many "hosts", such as a laptop, a tv, a fridge etc. These "hosts" may connect to the wider "network" via a base station, router and modem, which are responsible for interfacing with the wider network. 

"hosts" are connected by a network of **communication links** and **packet switches** (routers or link-layer switches). There are many types of communication links made up of different types of **physical media**, including coaxial cable, copper wire, optical fiber, and radio spectrum. Different links can transmit data at different rates, with these **transmission rates** measured in bits/second. Packet switches "direct" packets towards their final destination along the "route".

Data is segmented with header bytes added to each segment. This results in "packages" of information known as **packets** that are sent through the network to be reassembled at its final destination. 

End systems or "hosts" access the internet through **Internet Service Providers (ISP)**, which are contained networks or more packet switches and communication links. There are residential ISPs, cellular data ISPs, etc. Each ISP network is managed independently and runs the IP protocol.

page 31 - bottom - 1.1.2

## Approach 

Use 7th edition text book pdf and watch youtube lectures based on the 8th edition. Use "resources" found below to spplement learning as it makes sense. 

## Resources

Rent e-text book for 4 months
https://www.pearson.com/en-us/subject-catalog/p/computer-networking/P200000003334/9780135928615

https://media.pearsoncmg.com/aw/ecs_kurose_compnetwork_7/cw/

https://gaia.cs.umass.edu/kurose_ross/online_lectures.htm

https://gaia.cs.umass.edu/kurose_ross/interactive/
