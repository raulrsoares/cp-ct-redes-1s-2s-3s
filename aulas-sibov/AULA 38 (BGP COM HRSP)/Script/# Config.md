## R3
```
en
    conf t
        hostname R3
    int g0/0/0
        ip add 192.168.0.254 255.255.255.0
        no shut
    int s0/1/0
        ip add 172.16.0.1 255.255.255.252
        no shut
        exit
    router ospf 10
        router-id 1.1.1.1
        network 172.16.0.0 0.0.0.3 area 0
        network 192.168.0.0 0.0.0.255 area 10
        pass g0/0/0
        end
    wr
```
## R0
```
en
    conf t
        hostname R0
    int s0/1/0
        clock rate 4000000
        ip add 172.16.0.2 255.255.255.252
        no shut
    int s0/1/1
        clock rate 4000000
        ip add 10.0.0.5 255.255.255.252
        no shut
        exit
    router ospf 30
        router-id 2.2.2.2
        network 172.16.0.0 0.0.0.3 area 0
        redistribute bgp 13201 metric 200 subnets
        exit
    router bgp 13201
        neighbor 10.0.0.6 remote-as 13202
        network 10.0.0.4 mask 255.255.255.252
        redistribute ospf 30
        end
    wr
```
## R-CENTRAL
```
en
    conf t
        hostname R-Central
    int s0/1/0
        clock rate 4000000
        ip add 10.0.0.13 255.255.255.252
        no shut
    int s0/1/1
        ip add 10.0.0.6 255.255.255.252
        no shut
    router bgp 13202
        neighbor 10.0.0.5 remote-as 13201
        network 10.0.0.4 mask 255.255.255.252
        neighbor 10.0.0.14 remote-as 13203
        network 10.0.0.12 mask 255.255.255.252
        end
    wr
```
## R1
```
en
    conf t
        hostname R1
    int s0/1/0
        clock rate 4000000
        ip add 172.16.0.5 255.255.255.252
        no shut
    int s0/1/1
        ip add 10.0.0.14 255.255.255.252
        no shut
    router ospf 40
        router-id 3.3.3.3
        network 172.16.0.4 0.0.0.3 area 0
        redistribute bgp 13203 metric 200 subnets
    router bgp 13203
        neighbor 10.0.0.13 remote-as 13202
        network 10.0.0.12 mask 255.255.255.252
        redistribute ospf 40
        end
    wr
```
## R2
```
en
    conf t
        hostname R2
    int g0/0/0
        ip add 192.168.10.254 255.255.255.0
        no shut
    int s0/1/0
        ip add 172.16.0.6 255.255.255.252
        no shut
        exit
    router ospf 20
        router-id 4.4.4.4
        network 172.16.0.4 0.0.0.3 area 0
        network 192.168.10.0 0.0.0.255 area 20
        pass g0/0/0
        end
    wr
```