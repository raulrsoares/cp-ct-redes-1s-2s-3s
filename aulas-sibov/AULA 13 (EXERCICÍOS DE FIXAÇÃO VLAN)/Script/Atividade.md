## Equipamento S1p
```
enable
    configure terminal
    hostname S1
        vlan 10
            name Faculty/Staff
        vlan 20
            name Students
        vlan 30
            name Guest(Default)
        vlan 99
            name Management&Native
        vlan 150
            name VOICE
        exit
        int g0/1
            sw mo trunk
            sw trunk native vl 99
            sw trunk all vl 10,20,30,150,99
        int g0/2
            sw mo trunk
            sw trunk native vl 99
            sw trunk all vl 10,20,30,150,99
        end
    wr
```
## Equipamento S2
```
enable
    configure terminal
    hostname S2
        vlan 10
            name Faculty/Staff
        vlan 20
            name Students
        vlan 30
            name Guest(Default)
        vlan 99
            name Management&Native
        vlan 150
            name VOICE
        exit
        int f0/11
            sw mo ac
            sw ac vl 10
        int f0/18
            sw mo ac
            sw ac vl 20
        int f0/6
            sw mo ac
            sw ac vl 30
        int g0/1
            sw mo trunk
            sw trunk native vl 99
            sw trunk all vl 10,20,30,150,99
        end
    wr
```
## Equipamento S3
```
enable
    configure terminal
    hostname S3
        vlan 10
            name Faculty/Staff
        vlan 20
            name Students
        vlan 30
            name Guest(Default)
        vlan 99
            name Management&Native
        vlan 150
            name VOICE
        int f0/11
            sw mo ac
            sw ac vl 10
            sw voice vl 150
        int f0/18
            sw mo ac
            sw ac vl 20
        int f0/6
            sw mo ac
            sw ac vl 30
        int g0/2
            sw mo trunk
            sw trunk native vl 99
            sw trunk all vl 10,20,30,150,99
        end
    wr
```