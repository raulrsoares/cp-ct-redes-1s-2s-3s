## EQUIPAMENTO S1
```
en
    conf t
        vlan 10
        vlan 20
        vlan 30
        vlan 40
        vlan 50
        vlan 60
        vlan 70
        vlan 80
        vlan 99
        int vlan 99
            ip address 172.31.99.1 255.255.255.0
            no shut
            exit
        int f0/6
            switchport mode access
            switchport access vlan 30
            spanning-tree portfast
            spanning-tree bpduguard enable
            no shut
        int range f0/1-4
        sw mo trunk
        sw trunk native vl 99
        spanning-tree mode pvst
        spanning-tree vlan 1,10,30,50,70 root primary
        end
    wr
```
## EQUIPAMENTO S2
```
en
    conf t
        vlan 10
        vlan 20
        vlan 30
        vlan 40
        vlan 50
        vlan 60
        vlan 70
        vlan 80
        vlan 99
        int vlan 99
            ip address 172.31.99.2 255.255.255.0
            no shut
            exit
        int f0/18
            switchport mode access
            switchport access vlan 20
            spanning-tree portfast
            spanning-tree bpduguard enable
            no shut
        int range f0/1-4
        sw mo trunk
        sw trunk native vl 99
        spanning-tree mode pvst
        spanning-tree vlan 1,10,20,30,40,50,60,70,80,99 root secondary
        end
    wr
```
## EQUIPAMENTO S3
```
en
    conf t
        vlan 10
        vlan 20
        vlan 30
        vlan 40
        vlan 50
        vlan 60
        vlan 70
        vlan 80
        vlan 99
        int vlan 99
            ip address 172.31.99.3 255.255.255.0
            no shut
            exit
        int f0/11
            switchport mode access
            switchport access vlan 10
            spanning-tree portfast
            spanning-tree bpduguard enable
            no shut
        int range f0/1-4
        sw mo trunk
        sw trunk native vl 99
        spanning-tree mode pvst
        spanning-tree vlan 20,40,60,80,99 root primary        
        end
    wr
```