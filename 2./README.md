 ### Configuring a VM as a router and a second VM as a node/client and NATing from a VM



# Commands used:

1. Installed ```net-tools``` in both VMs: 
``` sudo yum install net-tools```

2. Brought up the netwrok interfaces ```enp0s3``` and ```enp0s8``` using ```ifup``` command;
```
ifup enp0s3
ifup enp0s8
```

2. Added ip address and net mask of a network interface using ```ifconfig``` command:

``` ifconfig enp0s3 192.168.1.139 netmask 255.255.255.0
```
3. listing the route table with ```route``` command:
``` route  ```


4. testing the connectin from VM2 to VM1 

```
ping 192.168.1.139

```



5. adding the default gateway in VM2: 

```
route add default gw 192.168.1.139

```

6. Adding the iptables rules for forwarding the incming requets from VM2 to the internet

```
# modprobe iptable_nat
# echo 1> /proc/sys/net/ipv4/ip_forward
# iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE 
# iptables -A FORWARD  -i enp0s8 -j ACCEPT 

```
7. Pinging on Cloudflare 
```
    ping 1.1.1.1

```
