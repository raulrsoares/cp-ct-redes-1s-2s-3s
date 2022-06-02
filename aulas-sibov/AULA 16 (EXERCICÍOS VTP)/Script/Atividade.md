## EQUIPAMENTO RT
```
    en
        conf t 
        hostname RT_RAULZIN
        int g0/0
            no shut
        int g0/0.10
            encapsulation dot1q 10
            ip add 192.168.10.254 255.255.255.0
            exit
        int g0/0.20
            encapsulation dot1q 20
            ip add 192.168.20.254 255.255.255.0
            exit
        int g0/0.30
            encapsulation dot1q 30
            ip add 192.168.30.254 255.255.255.0
            exit
        int g0/0.40
            encapsulation dot1q 40
            ip add 192.168.40.254 255.255.255.0
```
## EQUIPAMENTO SW-CENTRAL
```
en
    conf t
    hostname SW_CENTRAL
    vlan 10
        name RH
    vlan 20
        name MKT
    vlan 30
        name TI
    vlan 40
        name GERENCIAMENTO
    vtp mode server
    vtp domain SENAI
    vtp p senai132
    int range f0/1-3,g0/1
        sw mo trunk
        sw trunk native vlan 30
        sw trunk all vl 10,20,30,40
        no shut
    int f0/20
        sw mo ac
        sw ac vl 40
        no shut
```
## EQUIPAMENTO SW-RH
```
en
    conf t
    hostname SW_RH
    vtp mode client
    vtp domain SENAI
    vtp p senai132
    int f0/1
        sw mo trunk
        sw trunk native vlan 30
        sw trunk all vl 10,20,30,40
        no shut
    int f0/5
        sw mo ac
        sw ac vl 10
        no shut
```
## EQUIPAMENTO SW-MKT
```
en
    conf t
    hostname SW_MKT
    vtp mode client
    vtp domain SENAI
    vtp p senai132
    int f0/2
        sw mo trunk
        sw trunk native vlan 30
        sw trunk all vl 10,20,30,40
        no shut
    int f0/10
        sw mo ac
        sw ac vl 20
        no shut
```
## EQUIPAMENTO SW-TI
```
en
    conf t
    hostname SW_TI
    vtp mode client
    vtp domain SENAI
    vtp p senai132
    int f0/3
        sw mo trunk
        sw trunk native vlan 30
        sw trunk all vl 10,20,30,40
        no shut
    int f0/15
        sw mo ac
        sw ac vl 30
        no shut
```