## R-SP
```
en
    conf t
        ip access-list extended Liberar-ping-192
            10 permit icmp 192.168.0.0 0.0.0.255 172.16.0.0 0.0.25.255
            20 permit tcp host 192.168.0.1 host 172.16.0.254 eq www
            50 deny tcp any any
        int g0/0/0
            ip access-group Liberar-ping-192 in
```