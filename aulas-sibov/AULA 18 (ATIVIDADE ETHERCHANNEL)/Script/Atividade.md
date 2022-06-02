## EQUIPAMENTO S1 - F0/1-4
```
en
    conf t
        hostname SW1
        vlan 10
            name Alunos
        vlan 20
            name cla-fofoxis(pofs)
        vlan 110
            name comnedor-de-chetos(TI)
        int vlan 110
            ip add 192.168.110.1 255.255.255.0
            no shut
        int vlan 10
            ip add 192.168.10.11 255.255.255.0
            no shut
        int vlan 20
            ip add 192.168.20.11 255.255.255.0
            no shut
        int range f0/1-2
            sw mo trunk
            sw trunk native vl 110
            sw trunk all vlan 10,20,110
            channel-protocol pagp
            channel-group 2 mode desirable
            no shut
        int range f0/3-4
            sw mo trunk
            sw trunk native vl 110
            sw trunk all vlan 10,20,110
            channel-protocol pagp
            channel-group 1 mode desirable
            no shut
        int f0/5
            switchport mode access
            switchport access vlan 20
            no shut
        int f0/6
            switchport mode access
            switchport access vlan 10
            no shut
```
## EQUIPAMENTO S2 - F0/1-4
```
en
    conf t
        hostname SW2
        vlan 10
            name Alunos
        vlan 20
            name cla-fofoxis(pofs)
        vlan 110
            name comnedor-de-chetos(TI)
        int vlan 110
            ip add 192.168.110.2 255.255.255.0
            no shut
        int vlan 10
            ip add 192.168.10.12 255.255.255.0
            no shut
        int vlan 20
            ip add 192.168.20.12 255.255.255.0
            no shut
        int range f0/1-2
            sw mo trunk
            sw trunk native vl 110
            sw trunk all vlan 10,20,110
            channel-protocol pagp
            channel-group 2 mode auto
            no shut
        int range f0/3-4
            sw mo trunk
            sw trunk native vl 110
            sw trunk all vlan 10,20,110
            channel-protocol pagp
            channel-group 3 mode desirable
            no shut
        int f0/5
            switchport mode access
            switchport access vlan 20
            no shut
        int f0/18
            switchport mode access
            switchport access vlan 10
            no shut
```
## EQUIPAMENTO S3 - F0/1-4
```
en
    conf t
        hostname SW3
        vlan 10
            name Alunos
        vlan 20
            name cla-fofoxis(pofs)
        vlan 110
            name comnedor-de-chetos(TI)
        int vlan 110
            ip add 192.168.110.3 255.255.255.0
            no shut
        int vlan 10
            ip add 192.168.10.13 255.255.255.0
            no shut
        int vlan 20
            ip add 192.168.20.13 255.255.255.0
            no shut
        int range f0/1-2
            sw mo trunk
            sw trunk native vl 110
            sw trunk all vlan 10,20,110
            channel-protocol pagp
            channel-group 3 mode auto
            no shut
        int range f0/3-4
            sw mo trunk
            sw trunk native vl 110
            sw trunk all vlan 10,20,110
            channel-protocol pagp
            channel-group 1 mode auto
            no shut
        int f0/5
            switchport mode access
            switchport access vlan 20
            no shut
        int f0/18
            switchport mode access
            switchport access vlan 10
            no shut
        int f0/6
            switchport mode access
            switchport access vlan 110
            no shut
```