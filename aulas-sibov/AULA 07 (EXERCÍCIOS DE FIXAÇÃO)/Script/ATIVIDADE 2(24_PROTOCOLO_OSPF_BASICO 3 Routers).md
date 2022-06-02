##  Equipamento R_Matriz
```
en
    conf t
        hostname Matriz
        int g0/0/0
            ip add 192.168.0.126 255.255.255.128
            no shut
        int se0/1/0
            ip add 10.0.0.13 255.255.255.252
            clock rate 4000000
            no shut
        int s0/1/1
            ip add 10.0.0.9 255.255.255.252
            clock rate 8000000
            no shut
            exit
        router ospf 20
            router-id 1.1.1.1
            network 192.168.0.0 0.0.0.127 area 0
            network 10.0.0.12 0.0.0.3 area 0
            network 10.0.0.8 0.0.0.3 area 0 
            passive-interface g 0/0/0
            end
        wr
```
##  Equipamento R_Filial1
```
en
    conf t
        hostname Filial1
        int g0/0/0
            ip add 192.168.0.158 255.255.255.224
            no shut
        int se0/1/0
            ip add 10.0.0.14 255.255.255.252
            no shut
        int se0/1/1
            ip add 10.0.0.6 255.255.255.252
            no shut
            exit
        router ospf 20
            router-id 2.2.2.2
            network 192.168.0.128 0.0.0.31 area 0
            network 10.0.0.12 0.0.0.3 area 0
            network 10.0.0.4 0.0.0.3 area 0
            passive-interface g 0/0/0
            end
        wr
```
##  Equipamento R_Filial2
```
en
    conf t
        hostname Filial2
        int g0/0/0
            ip add 192.168.0.174 255.255.255.240
            no shut
        int se0/1/0
            ip add 10.0.0.10 255.255.255.252
            no shut
        int se0/1/1
            ip add 10.0.0.6 255.255.255.252
            clock rate 8000000
            no shut
            exit
        router ospf 20
            router-id 3.3.3.3
            network 192.168.0.160 0.0.0.15 area 0
            network 10.0.0.8 0.0.0.3 area 0
            network 10.0.0.4 0.0.0.3 area 0
            passive-interface g 0/0/0
            end
        wr
```
># Configuração dos computadores
>
>PC's | ID Rede | IP | Mask | Gateway | Wildcard 
>:--------- | :------: | :------: | :------: | :------: | :------:
>PC0 | 192.168.0.0 | 192.168.0.1 | 255.255.255.128 | 192.168.0.126 | 0.0.0.127
>PC1 | 192.168.0.128 | 192.168.0.129 | 255.255.255.224 | 192.168.0.158 | 0.0.0.31
>PC2 | 192.168.0.160 | 192.168.0.161 | 255.255.255.240 | 192.168.0.174 | 0.0.0.15