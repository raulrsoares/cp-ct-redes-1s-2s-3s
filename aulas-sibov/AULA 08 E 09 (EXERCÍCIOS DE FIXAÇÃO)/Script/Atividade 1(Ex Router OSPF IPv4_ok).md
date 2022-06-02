## Router A
```
en
    conf t
        hostname R-A
        int g0/0
            ip add 172.31.0.1 255.255.254.0
            no shut
        int s0/3/0
            ip add 172.31.4.1 255.255.255.252
            clock rate 4000000
            no shut
        exit
        router ospf 10
            router-id 1.1.1.1
            net 172.31.0.0 0.0.1.255 area 0
            net 172.31.4.0 0.0.0.3 area 0
            pa g0/0
            default
        end
    wr
```
## Router B
```
en
    conf t
        hostname R-B
        int g0/1
            ip add 172.31.2.1 255.255.254.0
            no shut
        int s0/3/1
            ip add 172.31.4.2 255.255.255.252
            no shut
        int s0/3/0
            ip add 172.31.4.5 255.255.255.252
            no shut
        exit
        router ospf 20
            router-id 2.2.2.2
            net 172.31.2.0 0.0.1.255 area 0
            net 172.31.4.0 0.0.0.3 area 0
            net 172.31.4.4 0.0.0.3 area 0
            pa g0/0
            default
        end
    wr
```
## Router C
```
en
    conf t
        hostname R-C
        int g0/0
            ip add 172.31.6.1 255.255.254.0
            no shut
        int s0/0/0
            ip add 172.31.4.6 255.255.255.252
            clock rate 4000000
            no shut
        exit
        router ospf 30
            router-id 3.3.3.3
            net 172.31.6.0 0.0.1.255 area 0
            net 172.31.4.4 0.0.0.3 area 0
            pa g0/0
            default
        end
    wr
```

