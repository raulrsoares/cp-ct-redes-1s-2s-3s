## ISP
```
en
    conf t 
        int g0/0
            ip add 200.201.202.1 255.255.255.252
            no shut
        int g0/2
            ip add 200.201.203.1 255.255.255.252
            no shut
        int g0/1
            ip add 8.8.8.1 255.255.255.0
            no shut
```
## R1
```
en
    conf t
        ip nat pool 1IPWan 200.201.202.2 200.201.202.2 netmask 255.255.255.252
        ip access-list standard Liberar192
            permit 192.168.0.0 0.0.0.255
            deny any
            exit
        ip nat inside source list Liberar192 pool 1IPWan overload
        ip route 8.8.8.8 0.0.0.0 200.201.202.2
        int g0/0
            ip add 200.201.202.2 255.255.255.252
            no shut
            ip nat out
        int g0/1
            ip add 192.168.0.2 255.255.255.252
            no shut
            ip nat in
            standby version 2
            standby 1 ip 192.168.0.1
            standby 1 priorit 150
```
## R2
```
en
    conf t
        ip nat pool 1IPWan 200.201.203.2 200.201.202.2 netmask 255.255.255.252
        ip access-list standard Liberar192
            permit 192.168.0.0 0.0.0.255
            deny any
            exit
        ip nat inside source list Liberar192 pool 1IPWan overload
        ip route 8.8.8.8 0.0.0.0 200.201.203.2
        int g0/0
            ip add 200.201.203.2 255.255.255.252
            no shut
            ip nat out
        int g0/1
            ip add 192.168.0.3 255.255.255.0
            no shut
            ip nat in
            standby version 2
            standby 1 ip 192.168.0.1
            standby 1 priorit 100
        exit
```