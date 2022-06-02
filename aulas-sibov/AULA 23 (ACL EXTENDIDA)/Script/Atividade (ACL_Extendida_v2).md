## R-SP
```
en
    conf t
        ip access-list extended BloqueiaPing192
            10 deny icmp 192.168.0.0 0.0.0.255 172.16.0.0 0.0.255.255
            20 deny tcp 192.168.0.0 0.0.0.255 range 1024 65535 host 172.16.0.254 eq www
            30 permit tcp 172.16.0.0 0.0.255.255 range 1024 65535 host 192.168.0.254 eq www
            40 permit tcp any any
            exit
        int g0/0/0
            ip access-group BloqueiaPing192 in
            exit
```
