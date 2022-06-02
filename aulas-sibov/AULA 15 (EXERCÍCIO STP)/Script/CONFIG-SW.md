## EQUIPAMENTO SW1
```
en
    conf t
        hostname SW1
        vlan 120
            name Gerenciamento
        int vlan 120
            ip add 192.168.10.1 255.255.255.0
            no shut
        int range f0/1-3
        sw mo trunk
        sw trunk native vl 120
        spanning-tree mode pvst
        spanning-tree vlan 1,120 root secondary
        int range g0/1-2
        sw mo trunk
        sw trunk native vl 120
        spanning-tree mode pvst
        spanning-tree vlan 1,120 root secondary
        end
```
## EQUIPAMENTO SW2
```
en
    conf t
        hostname SW2
        vlan 120
         name Gerenciamento
        int vlan 120
            ip add 192.168.10.2 255.255.255.0
            no shut
        int f0/24
            switchport mode access
            switchport access vlan 120
            spanning-tree portfast
            spanning-tree bpduguard enable
            no shut
        int range f0/1-3
        sw mo trunk
        sw trunk native vl 120
        spanning-tree mode pvst
        spanning-tree vlan 1,120 root secondary
        int range g0/1-2
        sw mo trunk
        sw trunk native vl 120
        spanning-tree mode pvst
        spanning-tree vlan 1,120 root secondary
        end
```
## EQUIPAMENTO SW3
```
en
    conf t
        hostname SW3
        vlan 120
         name Gerenciamento
        int vlan 120
            ip add 192.168.10.3 255.255.255.0
            no shut
        int range f0/2-4
        sw mo trunk
        sw trunk native vl 120
        spanning-tree mode pvst
        spanning-tree vlan 1,120 root secondary
        int range g0/1-2
        sw mo trunk
        sw trunk native vl 120
        spanning-tree mode pvst
        spanning-tree vlan 1,120 root secondary
        end
```
## EQUIPAMENTO SW4
```
en
    conf t
        hostname SW4
        vlan 120
         name Gerenciamento
        int vlan 120
            ip add 192.168.10.4 255.255.255.0
            no shut
        int range f0/1-3
        sw mo trunk
        sw trunk native vl 120
        spanning-tree mode pvst
        spanning-tree vlan 1,120 root primary
        int range g0/1-2
        sw mo trunk
        sw trunk native vl 120
        spanning-tree mode pvst
        spanning-tree vlan 1,120 root primary
        end
```