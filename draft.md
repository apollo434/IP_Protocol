# 1. IP Protocol Overview with key function:
![Alt text](/pic/ip_overview.png)

#### IP Protocol task
1. Body Checking
>Checking the sum and other incorrect things
2. Fire Wall
>Netfilter FireWall Subsystem(customer terminal use iptable to operate it)
3. Tackle Operations
>IP Protocol include some operations, which need to complete
4. Fragmentation/Defragmentation
>Base on MTU
5. Rx/Tx/Forwarding
>Basic Receive/Transmit/Forwarding Task.
>>Raw IP and IP over IP

#### IP Head
![Alt text](/pic/IP_Head.png)

1. Version
2. Header Length: HL
3. Type Of Service: TOS
4. Total Length
5. Identification
6. Don't Fragment: DF
7. More Fragment: MF
8. Fragment Offset
>6.7.8 will complete Fragmentation/Recombine Function
9. Time To Live: TTL
>When TTL = 0, discard, and send ICMP to sender
>Default TTL = 64
10. Protocol
11. Header Checksum
12. Source Address
13. Destination Address
14. Options

# 2. IP Options
![Alt text](/pic/IP_Options.png)

![Alt text](/pic/IP_Options_Type.png)

#### End of Option List and No Operations
1. End of Option
> IPOPT_END Option will fill with the left space of IP Header, in order to align based on 4 words
2. No Operations
>IPOPT_NOOP Option will fill with the left space of IP Options, in order to alignment.

#### Source Option
>Source Option, in order to let sender to direct all of the Router on the way
1. Strict
> Based on R_1 R_2 R_3, it is Strict Type
2. Loose
> Based on R_1 R_3, then R_2 or R_2b both OK, it is Loose Type

![Alt text](/pic/IP_Router.png)

#### Record Option
> Record Option, in order to record first 9 IP Address which as tx port on the way

![Alt text](/pic/IP_Record_Instance.png)

**NOTE:**
>Even PC4 and PC5 can't be involved in Record Option, still no ICMP to sender


#### Timestamp Option
> Record Time stamp, meanwhile, operate overflow problem

![Alt text](/pic/IP_Timestamp.png)

##### SubType
1. RECORD TIMESTAMPS
> Every Router will record the time when it receive the packet
2. RECORD ADDRESS AND TIMESTAMPS
> Seems like 1, but more function is that record the receive port IP Address
3. RECORD TIMESTAMPS ONLY AT THE PRESPECIFIED SYSTEMS
> Seems like 1, but more function is that record the specified IP Address

![Alt text](/pic/IP_TimeStamp_Instance.png)

##### overflow
> Overflow, in order to record when the IP Address has been recorded for 9 times in **Record Option**, the more than 9 IP Address times, will increase in **Overflow**, when **Overflow** more than 15, will create a **ICMP** to sender


#### Router Alert Option

#3. Fragmentation and Defragmentation
