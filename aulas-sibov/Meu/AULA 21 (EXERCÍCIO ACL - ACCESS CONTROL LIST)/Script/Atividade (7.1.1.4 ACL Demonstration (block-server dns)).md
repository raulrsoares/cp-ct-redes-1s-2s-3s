## R3
```
en
    conf t
        access-list 11 deny 192.168.31.0 0.0.0.255
        access-list 11 permit any
        int g0/1
            ip access-group 11 out
        end
```