## EQUIPAMENTO R0
```
en
    conf t
        hostname R0
        int s0/1/0
            ip add 10.0.0.2 255.255.255.252
            clock rate 4000000
            no shut
        int s0/1/1
            ip add 10.0.0.13 255.255.255.252
            no shut
        int s0/2/0
            ip add 10.0.0.5 255.255.255.252
            clock rate 4000000
            no shut
        int s0/2/1
            ip add 10.0.0.9 255.255.255.252
            clock rate 4000000
            no shut
        exit
        router ospf 10
            router-id 10.10.10.10
            net 10.0.0.0 0.0.0.3 area 0
            net 10.0.0.4 0.0.0.3 area 0
            net 10.0.0.8 0.0.0.3 area 0
            net 10.0.0.12 0.0.0.3 area 0
            end
        wr
```
## EQUIPAMENTO R1
```
en
    conf t
        hostname R1
        int g0/0/0
            ip add 192.168.0.126 255.255.255.128
            no shut
        int s0/1/0
            ip add 10.0.0.1 255.255.255.252
            no shut
        exit
        router ospf 1
            router-id 1.1.1.1
            net 10.0.0.0 0.0.0.3 area 0
            net 192.168.0.0 0.0.0.127 area 4
            pass g0/0/0
            end
        wr
```
## EQUIPAMENTO R2
```
en
    conf t
        hostname R2
        int g0/0/0
            ip add 192.168.0.206 255.255.255.240
            no shut
        int s0/1/0
            ip add 10.0.0.14 255.255.255.252
            no shut
        exit
        router ospf 2
            router-id 2.2.2.2
            net 10.0.0.12 0.0.0.3 area 0
            net 192.168.0.192 0.0.0.15 area 1
            pass g0/0/0
            end
        wr
```
## EQUIPAMENTO R3
```
en
    conf t
        hostname R3
        int g0/0/0
            ip add 192.168.0.210 255.255.255.252
            no shut
        int s0/1/0
            ip add 10.0.0.6 255.255.255.252
            no shut
        exit
        router ospf 3
            router-id 3.3.3.3
            net 10.0.0.4 0.0.0.3 area 0
            net 192.168.0.208 0.0.0.15 area 2
            pass g0/0/0
            end
        wr
```
## EQUIPAMENTO R4
```
en
    conf t
        hostname R4
        int g0/0/0
            ip add 192.168.0.190 255.255.255.192
            no shut
        int s0/1/0
            ip add 10.0.0.10 255.255.255.252
            clock rate 4000000
            no shut
        exit
        router ospf 4
            router-id 4.4.4.4
            net 10.0.0.8 0.0.0.3 area 0
            net 192.168.0.128 0.0.0.63 area 3
            pass g0/0/0
            end
        wr
```