## Roteador
```
enable
    conf t
    access-list 99 permit host 10.0.0.1
    access-list 99 deny any
    line vty 0 15
        access-class 99 in
```