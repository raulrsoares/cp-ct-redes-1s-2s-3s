# Atividade 8 **INCOMPLETO**

## Equipamento R1
```
en
    conf t
        hostname R1
        ipv6 unicast-routing
        int s0/1/1
            ipv6 add 2001:DB8:DA:2::1/64
            clock rate 4000000
            no shut
        int g0/0/0
            ipv6 add 2001:DB8:5EA1:B2B2::128/64
            no shut
        router rip
        version 2
        pa g0/0/0
        exit
        ipv6 router ospf 1
        area 0 range 2001:DB8:5EA1:B2B2::/64
        area 0 range 2001:DB8:DA:2::/64
        end
    wr
```
## Equipamento R2
```
en
    conf t
        hostname R2
        ipv6 unicast-routing
        int s0/1/0
            ipv6 add 2001:DB8:DA:2::2/64
            no shut
        int g0/0/0
            ipv6 add 2001:DB8:5EA1:B3B3::128/64
            no shut
        router rip
        version 2
        pa g0/0/0
        exit
        ipv6 router ospf 1
        area 0 range 2001:DB8:5EA1:B3B3::/64
        area 0 range 2001:DB8:DA:2::/64
        end
    wr
```

># Configuração dos computadores
>
>PC's | ID Rede | IP | Mask | Gateway | 
>:--------- | :------: | :------: | :------: | :------: 
>PC20 | 2001:DB8:5EA1:B2B2::/64 | 2001:DB8:5EA1:B2B2::1 | /64 | 2001:DB8:5EA1:B2B2::128
>PC30 | 2001:DB8:5EA1:B3B3::/64 | 2001:DB8:5EA1:B3B3::1 | /64 | 2001:DB8:5EA1:B3B3::128
>s0/1/1 | 2001:DB8:DA:2::/64 | 2001:DB8:DA:2::1/64 | /64 | -
