## SEDE
```
en
    conf t
        hostname HQ
    int s0/0/0
        encapsulation ppp
        ip add 209.165.201.18 255.255.255.252
        no shut
        username ISP-2 passowrd cisco
        ppp authentication chap
    int tunnel 10
        ip address 10.1.1.2 255.255.255.252
        tunnel source s0/0/0
        tunnel destination 209.165.201.2
        tunnel mode gre ip
    int g0/0
        ip add 192.168.30.1 255.255.255.0
        no shut
        exit
     ! DHCP SERVER
    ip dhcp excluded-address 192.168.30.1 192.168.30.10
    ip dhcp pool LAN
        network 192.168.30.0 255.255.255.0
        default-router 192.168.30.1
        dns-server 192.168.30.250
        exit
    router bgp 65020
        neighbor 209.165.201.17 remote-as 65535
        network 209.165.201.16 mask 255.255.255.252
        network 192.168.30.0 mask 255.255.255.0
        exit
    ip domain-name CISCO.com
    username admin password secureaccess
    crypto key generate rsa general-keys modulus 2048
    ip ssh version 2
    ip ssh authentication-retries 2
    ip ssh time-out 60
    line vty 0 15
        transport input ssh
        login local
    exit
    router ospf 100
        router-id 1.1.1.1
        network 192.168.30.0 0.0.0.255 area 0
        network 209.165.201.16 0.0.0.3 area 0
        network 10.1.1.2 0.0.0.3 area 0
        passive-interface g0/0
        exit
```
## BRANCH
```
en
    conf t
        hostname BRANCH
    int s0/0/0
        encapsulation ppp
        ip add 209.165.201.22 255.255.255.252
        no shut
        username ISP-3 password cisco
        ppp authentication chap
    int g0/0
        ip add 192.168.10.1 255.255.255.0
        no shut
        exit
        ! DHCP SERVER
    ip dhcp excluded-address 192.168.10.1 192.168.10.5
    ip dhcp pool LAN
        network 192.168.10.0 255.255.255.0
        default-router 192.168.10.1
        dns-server 192.168.30.250
        exit
    router bgp 65010
        neighbor 209.165.201.21 remote-as 65535
        network 209.165.201.20 mask 255.255.255.252
        network 192.168.10.0 mask 255.255.255.0
        exit
    ip domain-name CISCO.com
    username admin password secureaccess
        crypto key generate rsa general-keys modulus 2048
    ip ssh version 2
    ip ssh authentication-retries 2
    ip ssh time-out 60
    line vty 0 15
        transport input ssh
        login local
    exit
```
## REMOTO
```
en
    conf t
        hostname REMOTE
        ip route 0.0.0.0 0.0.0.0 209.165.201.1
    int g0/0
        ip add 192.168.20.1 255.255.255.0
        no shut
    int s0/0/0
        ip add 209.165.201.2 255.255.255.252
        no shut
    int tunnel 10
        ip add 10.1.1.1 255.255.255.252
        tunnel source s0/0/0
        tunnel destination 209.165.201.18
        tunnel mode gre ip
        no shut
        exit
    router ospf 100
        router-id 2.2.2.2
        network 192.168.20.0 0.0.0.255 area 0
        network 209.165.201.0 0.0.0.3 area 0
        network 10.1.1.1 0.0.0.3 area 0
        passive-interface g0/0
        exit
```
