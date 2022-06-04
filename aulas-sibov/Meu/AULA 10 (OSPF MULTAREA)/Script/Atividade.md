## EQUIPAMENTO R1
```
en
    conf t
        hostname R1
        int g0/0/0
            ip add 192.168.1.1 255.255.255.0
            no shut
        int s0/1/0
            ip add 10.0.0.1 255.255.255.252
            no shut
        router ospf 1
            router-id 1.1.1.1
            network 10.0.0.0 0.0.0.3 area 0
            network 192.168.1.0 0.0.0.255 area 1
            pass g0/0/0
            end
        wr
```
## EQUIPAMENTO R2
```
en
    conf t
        hostname R2
        int s0/1/1
            ip add 10.0.0.5 255.255.255.252
            clock rate 4000000
            no shut
        int s0/1/0
            ip add 10.0.0.2 255.255.255.252
            clock rate 4000000
            no shut
        router ospf 2
            router-id 2.2.2.2
            network 10.0.0.0 0.0.0.3 area 0
            network 10.0.0.4 0.0.0.3 area 0
            end
        wr
```
## EQUIPAMENTO R3
```
en
    conf t
        hostname R3
        int g0/0/0
            ip add 192.168.3.1 255.255.255.0
            no shut
        int s0/1/1
            ip add 10.0.0.6 255.255.255.252
            no shut
        router ospf 3
            router-id 3.3.3.3
            network 10.0.0.4 0.0.0.3 area 0
            network 192.168.3.0 0.0.0.255 area 3
            pass g0/0/0
            end
        wr
```