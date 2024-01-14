#  Homework 

> 2151894 王姝谕

1. 

   a)  **Transport Layer.**The transport layer provides process-to-process reliable and transparent data transmission services for the Session Layer and Network Layer.

   b)  **Data Link Layer.**It provides media access and link management and is responsible for establishing and managing links between nodes.MAC specifically controls access to shared channels.
   
   c)  **Data Link Layer.** On the basis of providing bit stream services at the physical layer, the bit information is encapsulated into a data frame to perform functions such as establishing, canceling, identifying logical links, link multiplexing, and error checking on the physical layer.
   
   d)  **Network Layer.** The Network Layer uses routing algorithms to select the most appropriate path for messages or communication subnets.
   
2. 

   a)     ASK(Amplitude Shifted Keying)

   ​	PSK(Phase Shifted Keying)  {BPSK,QPSK,8PSK...}

   ​	FSK(Frequency Shifted Keying)

   ​	QAM(Quadratic Amplitude Modulation)

   b)     Geostationary (GEO)

   ​	Medium-Earth Orbit (MEO)  [e.g.GPS]

   ​	Low-Earth Orbit(LEO)  [e.g. starlink]

   c)     copper

   ​	fiber optic cable  {Multi-mode，Single-mode}

   ​	twisted pair  {Cat-3，Cat-5，Cat-5e，Cat-6，Cat-8}

   ​	coaxial cable

   d)     Space Division Multiplexing  SDM

   ​	Frequency Division Multiplexing  FDMA

   ​	Wavelength Division Multiplexing

   ​	Time Division Multiplexing  TDM,TDMA

   ​	TIme and Frequency Division Multiplexing

   ​	Code Division Multiplexing CDM,CDMA

3. The end-to-end delay in a packet switching system is not always smaller than in a circuit switching system. Here come the reasons.

   In a **circuit-switched network**, a dedicated communication path is established before the data transmission begins, and this path remains dedicated for the duration of the communication session. This results in reduced delay and latency, because the data packets arrive in the proper order with minimum packet loss. The communication is done with a steady bandwidth and consistent data rate. In a **packet-switched network**, there is no requirement to establish a dedicated channel. The data is broken down into smaller units called packets and transmitted over the network. These packets may take different paths to reach their destination, and they may be transmitted out of order. If there are many users using it at a certain time, congestion will increase its delay. This can result in higher latency than circuit switching because packets must be routed through multiple nodes, which can cause delay.

   So, while packet switching can be more efficient in terms of bandwidth usage, it does not necessarily guarantee smaller end-to-end delay compared to circuit switching. The actual delay would depend on factors like network congestion, the number of nodes the packets have to pass through, and the specific protocols used for packet transmission and error correction.

   ![image-20231029213346777](C:\Users\WWWsy\AppData\Roaming\Typora\typora-user-images\image-20231029213346777.png)

![image-20231029213401706](C:\Users\WWWsy\AppData\Roaming\Typora\typora-user-images\image-20231029213401706.png)

![image-20231029213416074](C:\Users\WWWsy\AppData\Roaming\Typora\typora-user-images\image-20231029213416074.png)

![7fb67ff2915521d2a0625fe49435f5f](D:\wechatfiles\WeChat Files\wxid_r777pg4uwfuq22\FileStorage\Temp\7fb67ff2915521d2a0625fe49435f5f.jpg)

![535256f3a4b48f80b442ee37c032dc5](D:\wechatfiles\WeChat Files\wxid_r777pg4uwfuq22\FileStorage\Temp\535256f3a4b48f80b442ee37c032dc5.jpg)

![d46af228377e5a10af3a5637361a7b6](D:\wechatfiles\WeChat Files\wxid_r777pg4uwfuq22\FileStorage\Temp\d46af228377e5a10af3a5637361a7b6.jpg)

![3b9e3d507a3d7b2a6b65074db5f1858](D:\wechatfiles\WeChat Files\wxid_r777pg4uwfuq22\FileStorage\Temp\3b9e3d507a3d7b2a6b65074db5f1858.jpg)

![9ed4b1c1f418479a59c02d6ca0f7aae](D:\wechatfiles\WeChat Files\wxid_r777pg4uwfuq22\FileStorage\Temp\9ed4b1c1f418479a59c02d6ca0f7aae.jpg)
