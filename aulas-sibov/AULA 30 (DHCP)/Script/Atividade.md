## R1
```
en
    conf t
        hostname R1
    int g0/0
        ip add 192.168.10.1 255.255.255.0
        ip nat inside
        no shut
        exit
    ! DHCP SERVER
    ip dhcp excluded-address 192.168.10.1 192.168.10.5
    ip dhcp pool R1-LAN
    network 192.168.10.0 255.255.255.0
    default-router 192.168.10.1
    dns-server 192.168.10.2
    exit
    int g0/1
        no shut
        ip nat outside
        ip add dhcp
        exit
    ip nat pool 1IPWAN 200.1.10.4 200.1.10.4 netmask 255.255.255.248
    ip access-list standard LiberarRedeLAN
        permit 192.168.10.0 0.0.0.255
        deny any
        exit
    ip nat inside source list LiberarRedeLAN pool 1IPWAN overload
```
## VIVO
```
en
    conf t
        hostname VIVO
    int g0/0
        ip add 200.1.10.1 255.255.255.248
        no shut
        exit
    int g0/1
        ip add 200.200.10.1 255.255.255.248
        no shut
        exit
    ! DHCP Server
    ip dhcp excluded-address 200.1.10.1 200.1.10.2
    ip dhcp pool VIVO-LAN
    network 200.1.10.0 255.255.255.248
    default-router 200.1.10.1
    dns-server 8.8.8.8
```