# Aula 4

## Equipamento R1
```
en
    conf t
        ip route 0.0.0.0 0.0.0.0 s0/0/1
        router rip
            version 2
            no a
            net 192.168.1.0
            net 192.168.2.0
            passive-interface g0/0
            default-information originate
            end
        wr
```
## Equipamento R2
```
en
    conf t
        router rip
            version 2
            no a
            net 192.168.4.0
            net 192.168.3.0
            net 192.168.2.0
            passive-interface g0/0
            default-information originate
            end
        wr
```
## Equipamento R3
```
en
    conf t
        router rip
            version 2
            no a
            net 192.168.4.0
            net 192.168.5.0
            passive-interface g0/0
            default-information originate
            end
        wr
```
