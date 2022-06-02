# Atividade 1

**Equipamento RSP**
```
en
    conf t
        hostname RSP
        int g0/0/0
            ip add 192.168.10.254 255.255.255.0
            no shut
        int s0/1/0
            ip add 10.0.0.1 255.255.255.252
            clock rate 4000000
            no shut
        exit
        router rip
            version 2
            ne 192.168.10.0
            ne 10.0.0.0
            no a
        end
    wr
```
**Equipamento RINT**
```
en
    conf t
        hostname RINT
        int s0/1/1
            ip add 10.0.0.2 255.255.255.252
            no shut
        int s0/1/0
            ip add 10.0.0.5 255.255.255.252
            no shut
        exit
        router rip
            version 2
            ne 10.0.0.4
            ne 10.0.0.0
            no a
        end
    wr
```
**Equipamento RRJ**
```
en
    conf t
        hostname RRJ
        int g0/0/0
            ip add 172.16.255.254 255.255.0.0
            no shut
        int s0/1/0
            ip add 10.0.0.6 255.255.255.252
            clock rate 4000000
            no shut
        exit
        router rip
            version 2
            ne 10.0.0.4
            ne 172.16.0.0
            no a
        end
    wr
```
># Configuração dos computadores
>Lembrando que foi nescesário mudar o gateway proposto para o PC0, já que tinha confilto entre o ip e o gateway.
> PC's | IP | Mask | Gateway
>:--------- | :------: | :------: | :------: 
>PC0 | 192.168.10.1 | 255.255.255.128 | 192.168.10.126
>PC1 | 192.168.30.65 | 255.255.255.192 | 192.168.30.126
