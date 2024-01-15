---
title: "Sheet 3 Answers"
date: 2024-01-15T17:39:18+02:00
draft: false
---
# Sheet 3 - Answers

![](https://i.postimg.cc/tJGmVw5K/image.png)

1 - What are the source and destination port values in the segments flowing from the server back to the clients’ processes? What are the IP addresses in the network-layer datagrams carrying the transport-layer segments?

| Host     | Process            | Source Port | Source IP Address | Dest Port | Dest IP Address |
|----------|--------------------|-------------|-------------------|-----------|-----------------|
| A        | -                  | 80          | b                 | 26145     | a               |
| C (left) | -                  | 80          | b                 | 7532      | c               |
| C (right)| -                  | 80          | b                 | 26145     | c               |

------------


2 - Suppose a process in Host C has a UDP socket with port number 6789. Sup- pose both Host A and Host B each send a UDP segment to Host C with desti- nation port number 6789. Will both of these segments be directed to the same socket at Host C? If so, how will the process at Host C know that these two segments originated from two different hosts?

**Yes**.

**For each received segment, at the socket interface, the operating system will provide the process with the IP addresses to determine the origins of the individual segments.**


------------

3 - Suppose that a Web server runs in Host C on port 80. Suppose this Web server uses persistent connections, and is currently receiving requests from two different Hosts, A and B. Are all of the requests being sent through the same socket at Host C? If they are being passed through different sockets, do both of the sockets have port 80? Discuss and explain.

**Each persistent connection in a web server is associated with a unique "connection socket," identified by a four-tuple: (source IP, source port, destination IP, destination port). Host C uses these fields to route TCP segments to the appropriate socket. Although both A and B share a destination port (80), their sockets differ in source IP addresses. Unlike UDP, TCP doesn't explicitly specify the source IP when passing a segment's payload to the application process; it's implicitly defined by the socket identifier.**


------------

4- UDP and TCP use 1s complement for their checksums. Suppose you have the following four 8-bit bytes: 10011001, 11100010, 00100100, 10000100. 
- What is the 1s complement of the sum of these 8-bit bytes? 
- Why is it that UDP takes the 1s complement of the sum; that is, why not just use the sum? 
- With the 1s complement scheme, how does the receiver detect errors? 
- Is it possible that a 1-bit error will go undetected? 
- How about a 2-bit error?

a. Note, wrap around if overflow.
**1 0 1 1 1 0 0 1** 
+
**0 1 1 0 0 1 1 0**
=
**0 1 0 1 0 0 1 1**

and then
**0 0 1 0 1 1 1 0**
+
**0 1 1 1 0 1 0 0**
=
**1 0 1 1 1 0 0 1**

One's complement = **1 1 0 1 0 0 0 1**.

**b. To detect errors, the receiver adds the four words (the three original words and the checksum).**

**c. If the sum contains a zero, the receiver knows there has been an error.**

**d. All one-bit errors will be detected.**

**e. Two-bit errors can be undetected (e.g., if the last digit of the first word is converted to a 0 and the last digit of the second word is converted to a 1).**


------------

5- Consider a reliable data transfer protocol that uses only negative acknowledgments. Suppose the sender sends data only infrequently. Would a NAK-only protocol be preferable to a protocol that uses ACKs? Why? Now suppose the sender has a lot of data to send and the end-to-end connection experiences few losses. In this second case, would a NAK-only protocol be preferable to a protocol that uses ACKs? Why?

**If the sender sends the data infrequently (occasionally), then the NAK-only protocol is not preferred. It is good to use the protocol that uses ACKs.**

**The NAK-only protocol realize the loss of packet after a long time when it receives the data packet with wrong sequence number as the sender sends the data packets occasionally.**

**If the sender sends the data frequently, then the NAK-only protocol is preferred. The protocol that uses ACKs is not preferred as it require to send more number of acknowledgements**.

-----

6- Suppose Host A sends two TCP segments back-to-back to Host B over a TCP connection. The first segment has sequence number 90; the second has sequence number 110. a. How much data is in the first segment? b. Suppose that the first segment is lost but the second segment arrives at B. In the acknowledgment that Host B sends to Host A, what will be the acknowledgment number?


**a)**
**Consider sequence numbers,First segment=90**

                                               Second segment=110

                                               Data in the first segment=110-90

                                                                                      =20

 

**b) When Host B receives the second segment with sequence number 110, it will send an acknowledgment with an acknowledgment number equal to the next expected sequence number, which is 91. The acknowledgment number indicates the sequence number of the next byte that Host B is expecting to receive. Since the first segment with sequence number 90 was lost, Host B will assume that the next byte it expects to receive is byte 90, which is the first byte of the lost segment. Therefore, the acknowledgment number in the acknowledgment sent by Host B to Host A will be 90.**

------
7- Host A and B are communicating over a TCP connection, and Host B has already received from A all bytes up through byte 126. Suppose Host A then sends two segments to Host B back-to-back. The first and second segments contain 80 and 40 bytes of data, respectively. In the first segment, the sequence number is 127, the source port number is 302, and the destination port number is 80. Host B sends an acknowledgment whenever it receives a segment from Host A

**a) In the second segment sent from A:**

In the second segment from Host A to B:
- Sequence Number: 207
- Source Port Number: 302
- Destination Port Number: 80

**b) If the first segment arrives before the second segment:**

If the first segment arrives before the second:
- Acknowledgment Number: 207
- Source Port Number: 80
- Destination Port Number: 302

**c) If the second segment arrives before the first segment:**

If the second segment arrives before the first:
- Acknowledgment Number: 127 (indicating it is still waiting for bytes 127 and onwards)

**d) Support the two segments sent by A arrive in order at B. The first acknowledgment is lost and the second acknowledgment arrives after the first timeout interval. Draw a timing diagram, showing these segments and all the other segments and acknowledgments sent. Assume that there is no additional packet loss. For each segment in your figure, provide the segment number and the number of bytes of data; for each acknowledgment you add, provide the acknowledgment number.**

![](https://i.postimg.cc/W4gM8FWx/image.png)
-----
#### Extra question on flow control

8- Hosts A and B are directly connected with a 100 Mbps link. There is one TCP connection between the two hosts, and Host A is sending to Host B a very large file over this connection.

Host A can send application data into its TCP socket at a rate as high as 120 Mbps but Host B can read out of its TCP receive buffer at a maximum rate of 20Mbps. Describe the effect of TCP flow
control.


**Since the link capacity is only 100 Mbps, so host A’s sending rate can
be at most 100Mbps. Still, host A sends data into the receive buffer
faster than Host B can remove data from the buffer. The receive buffer
fills up at a rate of roughly 80Mbps. When the buffer is full, Host B
signals to Host A to stop sending data by setting RcvWindow = 0. Host A
then stops sending until it receives a TCP segment with RcvWindow > 0.
Host A will thus repeatedly stop and start sending as a function of the
RcvWindow values it receives from Host B. On average, the long-term
rate at which Host A sends data to Host B as part of this connection is
no more than 20Mbps.**
