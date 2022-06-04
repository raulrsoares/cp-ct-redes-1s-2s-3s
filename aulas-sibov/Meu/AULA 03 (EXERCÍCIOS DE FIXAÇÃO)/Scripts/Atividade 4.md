# Atividade 4
## Esta dando erro no RJUN, o o router não deixa entra o ping.

**Equipamento RSP**
```
en
    conf t
        hostname RSP
        interface g0/0/0
            ip address 192.168.50.190 255.255.255.224
            no shut
        interface s0/1/1
            ip address 10.0.0.17 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.5 255.255.255.252
            clock rate 4000000
            no shut
        exit
        router rip
            version 2
            network 192.168.50.0
            ne 10.0.0.16
            ne 10.0.0.4
            no auto-summary
        end
    wr
```
**Equipamento RITA**
```
en
    conf t
        hostname RITA
        interface g0/0/0
            ip address 192.168.60.198 255.255.255.248
            no shut
        interface s0/1/1
            ip address 10.0.0.18 255.255.255.252
            no shut
        interface s0/1/0
            ip address 10.0.0.22 255.255.255.252
            no shut
        exit
        router rip
            version 2
            network 192.168.60.0
            ne 10.0.0.16
            ne 10.0.0.20
            no auto-summary
        end
    wr
```
**Equipamento RITU**
```
en
    conf t
        hostname RITU
        interface g0/0/0
            ip address 192.168.30.190 255.255.255.224
            no shut
        interface s0/1/1
            ip address 10.0.0.21 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.10 255.255.255.252
            no shut
        exit
        router rip
            version 2
            network 192.168.30.0
            ne 10.0.0.20
            ne 10.0.0.8
            no auto-summary
        end
    wr
```
**Equipamento RJUN**
```
en
    conf t
        hostname RJUN
        interface g0/0/0
            ip address 192.168.20.126 255.255.255.192
            no shut
        interface s0/1/1
            ip address 10.0.0.9 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.2 255.255.255.252
            no shut
        exit
        router rip
            version 2
            network 192.168.30.0
            ne 10.0.0.8
            ne 10.0.0.0
            no auto-summary
        end
    wr
```
**Equipamento RSAN**
```
en
    conf t
        hostname RSAN
        interface g0/0/0
            ip address 192.168.10.254 255.255.255.128
            no shut
        interface s0/1/1
            ip address 10.0.0.1 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.14 255.255.255.252
            no shut
        exit
        router rip
            version 2
            network 192.168.10.0
            ne 10.0.0.12
            ne 10.0.0.0
            no auto-summary
        end
    wr
```
**Equipamento RJUQ**
```
en
    conf t
        hostname RJUQ
        interface g0/0/0
            ip address 192.168.40.254 255.255.255.0
            no shut
        interface s0/1/1
            ip address 10.0.0.13 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.6 255.255.255.252
            no shut
        exit
        router rip
            version 2
            network 192.168.40.0
            ne 10.0.0.12
            ne 10.0.0.4
            no auto-summary
        end
    wr
```
># Configuração dos computadores
>Lembrando que foi nescesário mudaro gateway proposto para o PC0, já que tinha confilto entre o ip e o gateway.
> Foi nescessário a mudança do ip da serial 0/1/0 para .17 já que .19 é um broadcast
>
>PC's | IP | Mask | Gateway
>:--------- | :------: | :------: | :------: 
>PC0 | 192.168.50.161 | 255.255.255.224 | 192.168.50.190
>PC1 | 192.168.40.1 | 255.255.255.0 | 192.168.40.254
>PC2 | 192.168.10.129 | 255.255.255.128 | 192.168.10.254
>PC3 | 192.168.20.65 | 255.255.255.192 | 192.168.20.126
>PC4 | 192.168.30.177 | 255.255.255.240 | 192.168.30.190
>PC5 | 192.168.60.193 | 255.255.255.248 | 192.168.60.198
