## R2
```
en
    conf t
        access-list 1 deny 192.168.11.0 0.0.0.255
        access-list 1 permit any
        interface GigabitEthernet0/0
            ip access-group 1 out
```
## R3
```
en
    conf t
        access-list 1 deny 192.168.10.0 0.0.0.255
        access-list 1 permit any
        interface GigabitEthernet0/0
            ip access-group 1 out
```