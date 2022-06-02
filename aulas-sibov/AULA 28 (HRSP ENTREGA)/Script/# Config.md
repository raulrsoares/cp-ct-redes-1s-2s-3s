## Equipamento ISP Google
```
en
    conf t
        hostname R-GOOGLE
        ip route 200.201.202.0 255.255.255.252 80.10.201.2
        ip route 200.201.203.0 255.255.255.252 80.10.201.2
        ip route 200.10.202.0 255.255.255.252 80.10.202.2
        ip route 200.11.203.0 255.255.255.252 80.10.202.2
    int g0/0
        ip add 80.10.201.1 255.255.255.252
        no shut
    int g0/1
        ip add 80.10.202.1 255.255.255.252
        no shut
    int g0/2
        ip add 8.8.8.1 255.255.255.0
        no shut
```
## Equipamento ISP VIVO
```
en
    conf t
    hostname R-VIVO
        ip route 0.0.0.0 0.0.0.0 80.10.201.1
    int g0/0
        ip add 200.201.202.1 255.255.255.252
        no shut
    int g0/1
        ip add 80.10.201.2 255.255.255.252
        no shut
    int g0/2
        ip add 200.201.203.1 255.255.255.252
        no shut
```
## Equipamento ISP CLARO
```
en
    conf t
        hostname R-CLARO
        ip route 0.0.0.0 0.0.0.0 80.10.202.1
    int g0/0
        ip add 200.10.202.1 255.255.255.252
        no shut
    int g0/1
        ip add 80.10.202.2 255.255.255.252
        no shut
    int g0/2
        ip add 200.11.203.1 255.255.255.252
        no shut
```
## Equipamento R1
```
en
    conf t
        hostname R1
        ip route 0.0.0.0 0.0.0.0 200.201.202.1
        ip nat pool 1IPWan 200.201.202.2 200.201.202.2 netmask 255.255.255.252
        ip nat inside source list Liberar192 pool 1IPWan overload
    int g0/0
        ip add 200.201.202.2 255.255.255.252
        no shut
        ip nat outside
    int g0/1
        ip add 192.168.0.2 255.255.255.0
        no shut
        ip nat inside
        standby version 2
        standby 1 ip 192.168.0.1
        standby 1 priority 150
        standby 1 preempt
    ip access-list standard Liberar192
        permit 192.168.0.0 0.0.0.255
        deny any
        exit
```
## Equipamento R2
```
en
    conf t
        hostname R2
        ip access-list standard Liberar192
        permit 192.168.0.0 0.0.0.255
        deny any
        exit
        ip nat pool 1IPWan 200.201.203.2 200.201.203.2 netmask 255.255.255.252
        ip nat inside source list Liberar192 pool 1IPWan overload
        ip route 0.0.0.0 0.0.0.0 200.201.203.1
    int g0/0
        ip add 200.201.203.2 255.255.255.252
        no shut
        ip nat outside
    int g0/1
        ip add 192.168.0.3 255.255.255.0
        no shut
        ip nat inside
        standby version 2
        standby 1 ip 192.168.0.1
        standby 1 priority 100
        standby 1 preempt
```
## Equipamento R3
```
en
    conf t
    hostname R3
    ip access-list standard Liberar192
        permit 192.168.1.0 0.0.0.255
        deny any
        exit
    ip nat pool 1IPWan 200.10.202.2 200.10.202.2 netmask 255.255.255.252
    ip nat inside source list Liberar192 pool 1IPWan overload
    ip route 0.0.0.0 0.0.0.0 200.10.202.1
    int g0/0
        ip add 200.10.202.2 255.255.255.252
        no shut
        ip nat outside
    int g0/1
        ip add 192.168.1.2 255.255.255.0
        no shut
        ip nat inside
        standby version 2
        standby 1 ip 192.168.1.1
        standby 1 priority 150
        standby 1 preempt
```
## Equipamento R4
```
en
    conf t
        hostname R4
        ip access-list standard Liberar192
        permit 192.168.1.0 0.0.0.255
        deny any
        exit
        ip nat pool 1IPWan 200.11.203.2 200.11.203.2 netmask 255.255.255.252
        ip nat inside source list Liberar192 pool 1IPWan overload
        ip route 0.0.0.0 0.0.0.0 200.11.203.1
    int g0/0
        ip add 200.11.203.2 255.255.255.252
        no shut
        ip nat outside
    int g0/1
        ip add 192.168.1.3 255.255.255.0
        no shut
        ip nat inside
        standby version 2
        standby 1 ip 192.168.1.1
        standby 1 priority 100
        standby 1 preempt
```