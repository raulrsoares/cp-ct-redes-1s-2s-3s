## Equipamento R-SP
```
en
    conf t
    hostname R-SP
    ip access-list extended Liberar-ping-192
            10 permit icmp 192.168.0.0 0.0.0.255 172.16.0.0 0.0.25.255
            20 permit tcp host 192.168.0.1 host 172.16.0.254 eq www
            50 deny tcp any any
    int g0/0/0
        ip access-group Liberar-ping-192 in
        ip add 192.168.0.30 255.255.255.0
        no shut
    int s0/1/0
        ip add 10.0.0.1 255.255.255.252
        clock rate 4000000
        no shut
    end
```
## Equipamento R-SP
```
en
    conf t
    hostname R-RJ
    int g0/0/0
        ip add 172.16.0.30 255.255.255.0
        no shut
    int s0/1/0
        ip add 10.0.0.2 255.255.255.252
        no shut
    end
```