## NIC (Network Interface Card) Issues

### Checking for dropped Packects

Server performance can be affected due to dropped packects on a NIC. Dropped packets causes them to re-sent which affects network performance.

Using the ```ip``` command we can check statistics for a NIC and other network objects

```
ip - show / manipulate routing, network devices, interfaces and tunnels
```

List all network interfaces
<details>
<summary>solution</summary>

```bash
ip link

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 00:0d:3a:2e:62:0f brd ff:ff:ff:ff:ff:ff
3: enP8170s1: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master eth0 state UP mode DEFAULT group default qlen 1000
    link/ether 00:0d:3a:2e:62:0f brd ff:ff:ff:ff:ff:ff
    altname enP8170p0s2

```
</details>

</br>

Check statistics for a network interface
<details>
<summary>solution</summary>

```bash
ip -s link show eth0

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 00:0d:3a:2e:62:0f brd ff:ff:ff:ff:ff:ff
    RX: bytes  packets  errors  dropped overrun mcast   
    222035952  147608   0       0       0       0       
    TX: bytes  packets  errors  dropped carrier collsns 
    3030525    11839    0       0       0       0

```

Here we are passing the -s option to show statistics for the eth0 interface. 

RX and TX show the packets received and transmitted from this interface respectively. 

There are no dropped packets
</details>


### Analyze Network Bandwidth

