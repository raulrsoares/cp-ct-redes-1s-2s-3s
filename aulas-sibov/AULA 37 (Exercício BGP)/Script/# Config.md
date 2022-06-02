## TIM
```
en
    conf t
        hostname R_TIM
    int g0/0/0
        ip add 200.1.0.254 255.255.255.0
        no shut
    int s0/1/0
        ip add 189.190.190.1 255.255.255.252
        no shut
    int s0/1/1
        ip add 189.190.194.1 255.255.255.252
        no shut
        exit
    router bgp 13200
        neighbor 189.190.194.2 remote-as 13203
        neighbor 189.190.190.2 remote-as 13201
        network 200.1.0.0 mask 255.255.255.0
        network 189.190.190.0 mask 255.255.255.252
        network 189.190.194.0 mask 255.255.255.252
        exit
```
## PTT
```
en
    conf t
        hostname R_PTT
    int s0/1/0
        ip add 189.190.194.2 255.255.255.252
        clock rate 4000000
        no shut
    int s0/1/1
        ip add 189.190.195.1 255.255.255.252
        clock rate 4000000
        no shut
        exit
    router bgp 13203
        neighbor 189.190.195.2 remote-as 20000
        neighbor 189.190.194.1 remote-as 13200
        network 189.190.195.0 mask 255.255.255.252
        network 189.190.194.0 mask 255.255.255.252
        exit
```
## VIVO1
```
en
    conf t
        hostname R_VIVO1
    int s0/1/0
        ip add 189.190.190.2 255.255.255.252
        clock rate 4000000
        no shut
    int s0/1/1
        ip add 189.190.191.1 255.255.255.252
        clock rate 4000000
        no shut
        exit
    router bgp 13201
        neighbor 189.190.190.1 remote-as 13200
        neighbor 189.190.191.2 remote-as 13202
        network 189.190.191.0 mask 255.255.255.252
        network 189.190.190.0 mask 255.255.255.252
        exit
```
## VIVO2
```
en
    conf t
        hostname R_VIVO2
    inter s0/1/0
        clock rate 4000000
        ip add 189.190.192.1 255.255.255.252
        no shut
    inter s0/1/1
        ip add 189.190.191.2 255.255.255.252
        no shut
        exit
    router bgp 13202
        network 189.190.192.0 mask 255.255.255.252
        network 189.190.191.0 mask 255.255.255.252
        neighbor 189.190.192.2 remote-as 20000
        neighbor 189.190.191.1 remote-as 13201
        exit
```
## VIVOCLI1
```
en
    conf t
        hostname VIVOCLI1
    inter g0/0/0
        ip add 200.0.0.3 255.255.255.0
        no shut
        standby version 2
        standby 1 ip 200.0.0.4
        standby 1 priority 150
        standby 1 preempt
    inter s0/1/0
        ip add 189.190.192.2 255.255.255.252
        no shut
        exit
    router bgp 20000
        network 189.190.192.0 mask 255.255.255.252
        network 200.0.0.0 mask 255.255.255.0
        neighbor 189.190.192.1 remote-as 13202
        exit
```
## VIVOCLI2
```
en
    conf t
        hostname R_VIVOCLI2
    inter g0/0/0
        ip add 200.0.0.2 255.255.255.0
        standby version 2
        standby 1 ip 200.0.0.4
        standby 1 priority 100
        standby 1 preempt
        no shut
    inter s0/1/0
        ip add 189.190.195.2 255.255.255.252
        no shut
        exit
    router bgp 20000
        network 189.190.195.0 mask 255.255.255.252
        network 200.0.0.0 mask 255.255.255.0
        neighbor 189.190.195.1 remote-as 13203
        exit
```