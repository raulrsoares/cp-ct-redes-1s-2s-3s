## R1
```
en
    conf t
        ip nat inside source static 172.16.16.1 64.100.50.1
        int g0/0
            ip nat inside
        int s0/0/0
            ip nat outside
```