# Atividade 3

**Equipamento RSP**
```
en
    conf t
        hostname RSP
        interface g0/0/0
            ip address 192.168.10.126 255.255.255.128
            no shut
        interface s0/1/1
            ip address 10.0.0.26 255.255.255.252
            no shut
        interface s0/1/0
            ip address 10.0.0.1 255.255.255.252
            clock rate 2000000
            no shut
        exit
        router rip
            version 2
            network 192.168.10.0
            ne 10.0.0.24
            ne 10.0.0.0
            no auto-summary
        end
    wr
```
**Equipamento RINT A**
```
en
    conf t
        hostname RINT-A
        interface s0/1/0
            ip address 10.0.0.5 255.255.255.252
            clock rate 2000000
            no shutdown
        interface s0/1/1
            ip address 10.0.0.2 255.255.255.252
            no shutdown
        router rip
            version 2
            ne 10.0.0.4
            ne 10.0.0.0
            no a
        end
    wr
```
**Equipamento RINT B**
```
en
    conf t
        hostname RINT-B
        interface s0/1/0
            ip address 10.0.0.6 255.255.255.252
            no shutdown
        interface s0/1/1
            ip address 10.0.0.9 255.255.255.252
            clock rate 2000000
            no shutdown
        router rip
            version 2
            ne 10.0.0.4
            ne 10.0.0.8
            no a
        end
    wr
```
**Equipamento RINT C**
```
en
    conf t
        hostname RINT-C
        interface s0/1/0
            ip address 10.0.0.10 255.255.255.252
            no shutdown
        interface s0/1/1
            ip address 10.0.0.13 255.255.255.252
            clock rate 2000000
            no shutdown
        router rip
            version 2
            ne 10.0.0.12
            ne 10.0.0.8
            no a
        end
    wr
```
**Equipamento RINT D**
```
en
    conf t
        hostname RINT-C
        interface s0/1/0
            ip address 10.0.0.14 255.255.255.252
            no shutdown
        interface s0/1/1
            ip address 10.0.0.17 255.255.255.252
            clock rate 2000000
            no shutdown
        router rip
            version 2
            ne 10.0.0.12
            ne 10.0.0.16
            no a
        end
    wr
```
**Equipamento RSANTOS**
```
en
    conf t
        hostname RSANTOS
        interface g0/0/0
            ip address 192.168.50.254 255.255.255.192
            no shut
        interface s0/1/1
            ip address 10.0.0.22 255.255.255.252
            no shut
        interface s0/1/0
            ip address 10.0.0.25 255.255.255.252
            clock rate 9600
            no shut
        exit
        router rip
            version 2
            network 192.168.50.0
            ne 10.0.0.20
            ne 10.0.0.0
            no auto-summary
        end
    wr
```
**Equipamento RRJ**
```
en
    conf t
        hostname RRJ
        interface g0/0/0
            ip address 192.168.30.126 255.255.255.192
            no shut
        interface s0/1/1
            ip address 10.0.0.21 255.255.255.252
            clock rate 9600
            no shut
        interface s0/1/0
            ip address 10.0.0.18 255.255.255.252
            no shut
        exit
        router rip
            version 2
            network 192.168.50.0
            ne 10.0.0.16
            ne 10.0.0.20
            no auto-summary
        end
    wr
```
># Configuração dos computadores
>Lembrando que foi nescesário fazer uma mudança do gateway proposto para o PC0, já que tinha confilto com o ip.
>
>PC's | IP | Mask | Gateway
>:--------- | :------: | :------: | :------: 
>PC0 | 192.168.10.1 | 255.255.255.128 | 192.168.10.126
>PC1 | 192.168.30.65 | 255.255.255.192 | 192.168.30.126
>PC2 | 192.168.50.193 | 255.255.255.192 | 192.168.30.254
