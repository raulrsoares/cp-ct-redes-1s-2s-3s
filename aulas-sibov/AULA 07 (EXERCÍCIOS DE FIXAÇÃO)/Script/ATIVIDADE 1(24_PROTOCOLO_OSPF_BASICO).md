##  Equipamento R_Matriz
```
en
    conf t
        hostname Matriz
        int g0/0/0
            ip add 192.168.0.254 255.255.255.0
            no shut
        int se0/1/0
            ip add 10.0.0.13 255.255.255.252
            clock rate 4000000
            no shut
            exit
        router ospf 20
            router-id 1.1.1.1
            network 192.168.0.0 0.0.0.255 area 0
            network 10.0.0.12 0.0.0.3 area 0 
            passive-interface g 0/0/0
            end
        wr
```
##  Equipamento R_Filial
```
en
    conf t
        hostname Filial
        int g0/0/0
            ip add 172.16.255.254 255.255.0.0
            no shut
        int se0/1/0
            ip add 10.0.0.14 255.255.255.252
            no shut
            exit
        router ospf 20
            router-id 2.2.2.2
            network 172.16.0.0 0.0.255.255 area 0
            network 10.0.0.12 0.0.0.3 area 0
            passive-interface g 0/0/0
            end
        wr
```
># Configuração dos computadores
>
>PC's | ID Rede | IP | Mask | Gateway | Wildcard
>:--------- | :------: | :------: | :------: | :------: | :------:
>PC0 | 192.168.0.0 | 192.168.0.1 | 255.255.255.0 | 192.168.0.254 | 0.0.0.127
>PC1 | 172.16.0.0 | 172.16.0.1 | 255.255.0.0 | 172.16.255.254 | 0.0.255.255