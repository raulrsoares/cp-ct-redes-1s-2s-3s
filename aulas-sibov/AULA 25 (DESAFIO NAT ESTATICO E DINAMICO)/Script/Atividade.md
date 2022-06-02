## Equipamento Roteador Empresa - ACME
```
en
    conf t
        int g0/0
            ip nat inside
        int g0/1
            ip nat inside
        int g0/2
            ip nat inside
        int s 0/0/0
            ip nat outside
        exit
        ip access-list standard RNATD-LAN
            permit 192.168.0.0 0.0.0.255
        ip access-list standard RPAT-WLAN
            permit 192.168.1.0 0.0.0.255
        ip access-list standard RNATS-SERVIDORES
            permit 192.168.2.0 0.0.0.255
        exit
        ip nat pool RNATD-POOL 200.0.0.3 200.0.0.13 netmask 255.255.255.0
        ip nat inside source list RNATD-LAN pool RNATD-POOL
        
        ip nat pool RPAT-POOL 200.0.0.14 200.0.0.14 netmask 255.255.255.0
        ip nat inside source list RPAT-WLAN pool RPAT-POOL overload


        ip nat inside source static 192.168.2.100 200.0.0.15
```
