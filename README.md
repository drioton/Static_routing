# Static_routing #

```
3x Router
6x PC
3x Switch

1.0.0.0/30 Left-Middle
2.0.0.0/30 Middle-right
192.168.1.0/24  PC0-PC1
192.168.2.0/24  PC2-PC3
192.168.3.0/24  PC4-PC5
```
```
Wir können jetzt bereits alle Geräte einrichten, aber wir verbinden nur Router Left und Router Middle.
Router Right verbinden wir mit Router Middle erst,
wenn wir das statische Routing zwischen Router Left und Router Middle konfiguriert haben.

We can already set up all devices, but we will only connect Router Left and Router Middle.
We will connect Router Right to Router Middle only after we configure static routing between Router Left and Router Middle.
```
images/Preparation.png
https://github.com/drioton/Static_routing/blob/a3f49b26c34350fe5547e143fba63f38a3f48853/images/Preparation.png

![Preparation](https://github.com/drioton/Static_routing/blob/main/images/Preparation.png)

**Router 0 (Left)**

```
enable
configure terminal
hostname Left
interface GigabitEthernet0/1
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
interface GigabitEthernet0/0
no shutdown
exit
```

**Router 1 (Middle)**

```
enable
configure terminal
hostname Middle
interface GigabitEthernet0/2
ip address 192.168.2.1 255.255.255.0
no shutdown
exit
interface GigabitEthernet0/0
ip address 1.0.0.2 255.255.255.252
no shutdown
exit
exit
```

**Static routing**


**Router Left**

```
show ip route   
configure terminal
ip route 192.168.2.0 255.255.255.0 1.0.0.2 
```
Das Hinzufügen eines weiteren Netzwerks. Das erste ist das Netzwerk, das wir mit der Maske hinzufügen möchten, und das nächste Netzwerk ist der nächste Hop, an den unser Router Left senden wird.

Adding another network. The first one is the network we want to add with the subnet mask, and the next network is the next hop to which our router Left will send.

**Router Middle**

```
enable
configure terminal
ip route 192.168.1.0 255.255.255.0 1.0.0.1
```

**PC0**
```
C:\>ping 192.168.2.3

Pinging 192.168.2.3 with 32 bytes of data:

Reply from 192.168.2.3: bytes=32 time<1ms TTL=126
Reply from 192.168.2.3: bytes=32 time<1ms TTL=126
Reply from 192.168.2.3: bytes=32 time<1ms TTL=126
Reply from 192.168.2.3: bytes=32 time<1ms TTL=126

Ping statistics for 192.168.2.3:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

```


**Two new Network**

```
Connect together Router Middle and Router Right 
```












