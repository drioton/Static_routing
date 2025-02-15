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

** Stattic routing**

```
**Router Left**

```
show ip route   #checking routing Table
configure terminal
ip route 192.168.2.0 255.255.255.0 1.0.0.2 
#Das Hinzufügen eines weiteren Netzwerks. Das erste ist das Netzwerk, das wir mit der Maske hinzufügen möchten, und das nächste Netzwerk ist der nächste Hop, an den unser Router Left senden wird.
Adding another network. The first one is the network we want to add with the subnet mask, and the next network is the next hop to which our router Left will send.#

















