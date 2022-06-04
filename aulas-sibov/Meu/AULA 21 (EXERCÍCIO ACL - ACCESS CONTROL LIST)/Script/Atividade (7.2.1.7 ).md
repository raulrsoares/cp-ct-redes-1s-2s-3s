## R1
```
en
    conf t
    ip access-list standard File_Server_Restrictions
        permit 192.168.20.4
        deny any 
    int f0/1
        ip access-group File_Server_Restrictions out
```