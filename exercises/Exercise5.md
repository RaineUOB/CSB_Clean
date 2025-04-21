## Week 5 Exercices: Security Protocols and Private Network

1. Sana is wondering what a VPN is and how she can benefit from it, explain to her what a VPN is, its applications and the possible ways of implementing it.

2. What is IP tunnelling? 

3. A client and server want to communicate, explain the steps of establishing a TLS exchange.

4. What are the TLS subprotocols?

5. Why SSL was discarded?

> [!NOTE]
> For the following two questions, you need to revise slides from previous lectures about network attacks and also some research on your own.

6. What network attacks do you think we can stop using TLS?

7. What network attacks do you think we can stop using IPSec?

## Answers

1. A VPN facilitates communications between companies and their partners, internal communications of a geographically distributed company, or remote communications between a mobile and its company. It is mainly based on establishing an IP tunnel to exchange data. A VPN can be imlemented using TLS or IPSec. IPSEC VPN is useful for 
Remote access scenario and Interconnecting LANs. TLS VPN is useful for Remote access to private network scenario.

2. IP tunnelling is creating a private channel where two distant devices can communicate as if they were local. It is based on encapsulating an IP packet inside another IP packet.

3. Check slide 18 in the [lecture slides](slides/L5_Security_Protocols_Private_Networks.pdf).

4. TLS Subprotocols: 
    - handshake
    - change cipher spec protocol
    -  alert protocol
    -  data protocol
    -  reccord protocol

6. SSL was not secure enough so it was discarded and TLS has taken its place.

7. Because the communication is encrypted, TLS can stop eavesdropping, tampering, and message forgery between two communicating network endpoints.

8. Network-based attacks from untrusted computers, attacks that can result in the denial-of-service of applications, services, or the network, Data corruption
Using IPSec  keeps the data encrypted and makes sure they all reached their destination without any alterations on their way.





