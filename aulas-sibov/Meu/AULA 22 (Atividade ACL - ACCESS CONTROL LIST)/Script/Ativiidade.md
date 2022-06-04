## R1
```
en
    conf t
    ip access-list standard FROM_192
        no 10 deny 192.168.0.0 0.0.0.255
        10 deny 10.0.0.0 0.255.255.255
    ip access-list standard FROM_10
        no 10 deny host 10.0.0.22
        5 deny host 10.0.0.2
    ip access-list standard FROM_172
        no 10 deny host 172.16.0.2
    interface GigabitEthernet0/0
        ip access-group FROM_192 out
```
