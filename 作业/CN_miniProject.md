# CN_miniProject

## Q 1.1

My own IP address: 100.80.176.18

IP address of sse.tongji.edu.cn :192.168.67.3、192.168.66.4

![image-20231228185902489](C:\Users\WWWsy\AppData\Roaming\Typora\typora-user-images\image-20231228185902489.png)

## Q 1.2

I saw that in addition to the website I visited before, there are other three-way handshakes for network connection establishment.

I opened QQ to log in, and then opened the Baidu web page. First, I need to know what the IP addresses of the two pages I open are connected to. So I filtered the data packets related to the domain name through the dns filtering conditions, and saw a lot of data packets with "qq.com" or "baidu.com" information, so I further refined the filtering conditions and used `dns.qry.name contains "qq.com"`  filter, and the data packet sent during the domain name resolution process is found. 

There are many data packets, and I only selected one of them to find the domain name. I clicked on the last response packet, found the domain name of one of the qq servers in the answer part of the application layer message.In the picture below, you can see that the IP related to qq obtained by domain name resolution is 175.27.5.225.

<img src="D:\university\计网\第三次作业截图\image-20231118095121193.png" alt="image-20231220150035999" style="zoom:50%;" />

Then I used `ip.addr==175.27.5.225` again to filter the relevant packets. I can see my computer and this IP has a three-way handshake process to establish a connection, and the fourth message uses the HTTP protocol to send content.

connection to IP:175.27.5.225 

![image-20231220145512864](D:\university\计网\第三次作业截图\image-20231220145512864.png)

To search for a network connection after opening the Baidu webpage, use `dns.qry.name contains "baidu.com"` to locate the packet related to domain name resolution. Extract the response’s answer to get the IP address. Then, use the `ip.addr` filter to find the process of establishing a connection with this IP. This process is identical to the one described above. The details are shown in the figure.

<img src="D:\university\计网\第三次作业截图\image-20231220151028508.png" alt="image-20231220151028508" style="zoom:50%;" />

Then use the filter statement of `ip.addr==182.61.200.48 `to find the process of establishing a connection with this IP.

connection to IP:182.61.200.48

![image-20231210211520631](D:\university\计网\第三次作业截图\image-20231210211520631.png)

## Q 2.1

1. The sequence number is 4249678530,the relative sequence number is 0

   ![image-20231229145247283](D:\university\计网\第三次作业截图\image-20231229145247283.png)

2. The Flags:0x002(SYN) identifies the segment as a SYN segment

   ![image-20231229145533939](D:\university\计网\第三次作业截图\image-20231229145533939.png)

## Q 2.2

1. The sequence number is 3069923765,the relative sequence number is 0

   ![image-20231229145648165](D:\university\计网\第三次作业截图\image-20231229145648165.png)

2. The value of relative ack number is 1,the raw acknowledgment number is 3112092635

   ![image-20231229145822001](D:\university\计网\第三次作业截图\image-20231229145822001.png)

3. The value in the acknowledgment field is the sequence number in the received SYN packet + 1

4. Flags:0x012(SYN,ACK) identifies the segment as a SYNACK segment

   ![image-20231229145822001](D:\university\计网\第三次作业截图\image-20231229145822001.png)

## Q 2.3

In a two-way handshake, only the initiator’s starting sequence number can be confirmed, not the other party’s.

Consider this: The Client sends a request to the Server, which gets delayed in the network. The Client resends the request. The Server receives it, sends a confirmation, establishes the connection, and begins data transfer. Once data transfer is complete, the connection is disconnected.

However, the Client’s first request reaches the Server after disconnection. The Server sends a confirmation, establishing a connection. But the Client, having completed its data service, does nothing, leaving the Server waiting for data interaction and wasting resources.

Thus, a handshake can’t confirm a client’s connection request, making it unfeasible.

## Q 2.4

I chose the No.2 segment.

1. 2023-06-30 14:29:20.844658  

   ![image-20231211092250057](D:\university\计网\第三次作业截图\image-20231211092250057.png)

2. 2023-06-30 14:29:20.844669

   ![image-20231211092310577](C:\Users\WWWsy\AppData\Roaming\Typora\typora-user-images\image-20231211092310577.png)

3. 1424

   <img src="D:\university\计网\第三次作业截图\image-20231220151508240.png" alt="image-20231220151508240" style="zoom: 50%;" />

4. 0.000011000 seconds.

   The sending time of the selected data packet is 2023-06-30 14:29:20.844658, and the arrival time of the acknowledged data packet is 2023-06-30 14:29:20.844669. From this, the RTT can be calculated to be 0.000011000 seconds. 

   In the TCP Stream Graph,we can see the RTT of the selected packet is 0.011ms

   <img src="D:\university\计网\第三次作业截图\image-20231211093506980.png" alt="image-20231211093506980" style="zoom:50%;" />

   Another method: Click to view the detailed information of the ACK datagram, which will display its RTT.

   ![image-20231211093312208](D:\university\计网\第三次作业截图\image-20231211093312208.png)

   

## Q 2.5

1. The concept is the full-duplex nature of TCP, which means that data can flow independently in both directions. That's why in full-duplex communication, tcptrace follows the direction of transmission. Changes as they change. For example, when you open a web page in a browser, the computer (client) sends a request to the server (this is one direction), and the server responds and sends the content of the web page back to your computer (this is another direction). one direction).

2. If the receiver's buffer space is insufficient, the sender's data transmission will be limited by adjusting the TCP window size, allowing the sender to send slower, and wait until the receiver has more buffer space before continuing to send. It can be seen from this picture that as soon as the yellow line rises (the receiving end confirms), the blue line rises (the sending end starts sending) until the green line is filled. After the blue line rises for a period of time, it is close to the green line (the receiving end starts sending). (Insufficient buffer space on the other side) will stagnate and rise for a period of time. During this period, no data is sent, indicating that the sending rate of the sender is limited. When the green line is farther away from the blue line, the blue line rises again, which indicates that the receiver has enough buffer space, so the sender starts sending data quickly again.

   <img src="D:\university\计网\第三次作业截图\image-20231211143659293.png" alt="image-20231211143659293" style="zoom:50%;" />

3. We can see three lines: a blue line, a yellow line and a green line. The blue line represents the sending sequence number, while the green line represents the upper limit of the sending window. The yellow line represents the sequence number confirmed by the receiving end.
   At about 20 seconds, the blue line suddenly dropped and remained stable. After zooming in on the picture, you can see in the figure below that the parallel distance between the blue line and the yellow line has also become larger, indicating that the RTT time has become larger, which may mean that Data packet loss occurs, causing the TCP sending end to reduce the sending window, thereby reducing the data sending speed and avoiding network congestion. Therefore, from this tcptrace graph, we can deduce that network congestion may have occurred at about 20 seconds.

   I think this congestion is not serious, because there are not a large number of red lines in the picture, only a few scattered ones, which means that there are just some repeated ACKs and the RTT time is getting longer, which means that the receiver’s confirmation information can still arrive. On the sender side, there is just some network congestion. It is not serious enough that the receiver's information cannot be sent back.

   <img src="D:\university\计网\第三次作业截图\image-20231211194230864.png" alt="image-20231211194230864" style="zoom:50%;" />

4. When a TCP connection needs to retransmit data, it follows certain steps:

   1. Retransmission Trigger: If an acknowledgment (ACK) for a segment is not received within the retransmission timeout (RTO), the sender retransmits the segment. This is often triggered by the expiration of the time-out timer or the receipt of three duplicate ACKs at the sender.
   2. Sequence Number: The sequence number of the retransmitted segment remains the same as the original segment. This allows the receiver to correctly order the received segments.
   3. Window Size Adjustment: TCP uses congestion control mechanisms to adjust the window size. When packet loss is detected, TCP assumes it’s due to network congestion and reduces the congestion window size. This slows down the rate of data transmission to alleviate the congestion.

   Transmission failures can be due to network congestion, hardware issues, or software bugs. These can cause packet loss as the network becomes overloaded, hardware malfunctions, or software errors occur.

   Preventing transmission failures involves implementing advanced congestion control algorithms, maintaining hardware and software, and designing the network to avoid congestion, ensure capacity, and provide redundancy.

## Q 2.6

Because TCP is byte-stream oriented, you only need to count the sequence number of the first segment sent and the last segment acknowledged within a certain period of time. The difference between the two is the number of bytes sent. The throughput is obtained by dividing this number of bytes by this period of time.

## Q 2.7

One set of connections between the two IPs 100.75.250.48 and 120.233.43.93 specified in Q2.5: 100.75.250.48:50384 and 120.233.43.93:16617 was terminated at 2023-06-30 14:29:52.786767.

![image-20231214145238749](D:\university\计网\第三次作业截图\image-20231214145238749.png)Usually, if you want to find when two connections are disconnected, you can look for TCP packets with the FIN flag bit, and then look for whether there are four wave-disconnection processes in the nearby time period, so that you can find the time when the connection is terminated.

In the four-way handshake:

<img src="D:\university\计网\第三次作业截图\image-20231214153446302.png" alt="image-20231214153446302" style="zoom:50%;" />

1. The first device begins the termination process by sending a FIN (Finish) packet to the second device.The sequence number `u` of the datagram depends on the context.
2. The second device responds with an ACK (Acknowledgment) packet, acknowledging the receipt of the FIN packet.
3. Subsequently, the second device sends its own FIN packet to the first device, indicating that it also wants to end the connection.
4. The first device completes the handshake by sending an ACK packet in response to the second device's FIN packet.

This process ensures an orderly closure of the connection where both devices agree to terminate the communication. Each step includes the necessary confirmation before proceeding to the next, allowing both sides to close their respective end of the connection gracefully.

## Q 2.8

TCP connection can be terminated by waving three times. As long as the end that passively receives the disconnection request message combines the acknowledgment packet for the incoming FIN datagram and its own data packet with the FIN flag and sends them together, it can achieve TCP disconnection by waving three times.

For example, the example in the figure below achieves disconnection by sending data packets three times.

![image-20231214154340106](D:\university\计网\第三次作业截图\image-20231214154340106.png)

But I think this is essentially still four waves, but two of them are sent in the same piece of data.

## Feedback

I think this assignment is relatively new. This way of analyzing real cases gave me a concrete understanding of the theoretical knowledge I learned. And there are many complex situations in reality that are not as ideal as what the textbooks say.

It took me about 8 hours to completely complete this task.

One problem is that the description of the question occasionally has some ambiguities, such as the first question in 2.4 and the third question in 2.4. But I think this may be a problem with English expression. Maybe it can be described more clearly in Chinese.
