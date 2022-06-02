## R1
```
en
    conf t
        int s0/0/0
        no ip access-group 11 out
        exit
    no access-list 11
```