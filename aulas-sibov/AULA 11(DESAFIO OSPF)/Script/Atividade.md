## EQUIPAMENTO R_JUQ
```
en
    conf t
        hostname R_JUQ
        service pass
        enable secret senai@132
        int g0/0/0
            ip add 10.3.247.254 255.255.248.0
            no shut
        int s0/1/0
            ip add 10.3.204.65 255.255.255.252
            clock rate 4000000
            no shut
        line console 0
            pass senai@132
            login
        line vty 0 4
            pass senai@132
            login local
        exit
        router ospf 80
        router-id 80.80.80.80
        net 10.3.204.64 0.0.0.3 area 0
        net 10.3.240.0 0.0.7.255 area 4
        pass g0/0/0
        end
    wr
```
## EQUIPAMENTO R_ITA
```
en
    conf t
        hostname R_ITA
        service pass
        enable secret senai@132
        int g0/0/0
            ip add 10.3.127.254 255.255.128.0
            no shut
        int s0/1/0
            ip add 10.3.204.78 255.255.255.252
            no shut
        int s0/1/1
            ip add 10.3.204.86 255.255.255.252
            no shut
        line console 0
            pass senai@132
            login
        line vty 0 4
            pass senai@132
            login local
        exit
        router ospf 30
        router-id 30.30.30.30
        net 10.3.204.84 0.0.0.3 area 8
        net 10.3.204.76 0.0.0.3 area 0
        net 10.3.0.0 0.0.127.255 area 9
        pass g0/0/0
        end
    wr
```
## EQUIPAMENTO R_SANTOS
```
en
    conf t
        hostname R_SANTOS
        service pass
        enable secret senai@132
        int g0/0/0
            ip add 10.3.251.254 255.255.252.0
            no shut
        int s0/1/1
            ip add 10.3.204.85 255.255.255.252
            clock rate 4000000
            no shut
        line console 0
            pass senai@132
            login
        line vty 0 4
            pass senai@132
            login local
        exit
        router ospf 20
        router-id 20.20.20.20
        net 10.3.204.84 0.0.0.3 area 8
        net 10.3.248.0 0.0.3.255 area 8
        pass g0/0/0
        end
    wr
```
## EQUIPAMENTO R_PAR
```
en
    conf t
        hostname R_PAR
        service pass
        enable secret senai@132
        int g0/0/0
            ip add 10.3.254.62 255.255.255.192
            no shut
        int s0/1/1
            ip add 10.3.204.89 255.255.255.252
            no shut
        int s0/1/0
            ip add 10.3.204.74 255.255.255.252
            no shut
        line console 0
            pass senai@132
            login
        line vty 0 4
            pass senai@132
            login local
        exit
        router ospf 40
        router-id 40.40.40.40
        net 10.3.204.88 0.0.0.3 area 10
        net 10.3.204.72 0.0.0.3 area 0
        net 10.3.254.0 0.0.0.63 area 11
        pass g0/0/0
        end
    wr
```
## EQUIPAMENTO R_SC
```
en
    conf t
        hostname R_SC
        service pass
        enable secret senai@132
        int g0/0/0
            ip add 10.2.255.254 255.255.0.0
            no shut
        int s0/1/1
            ip add 10.3.204.90 255.255.255.252
            clock rate 4000000
            no shut
        line console 0
            pass senai@132
            login
        line vty 0 4
            pass senai@132
            login local
        exit
        router ospf 50
        router-id 50.50.50.50
        net 10.3.204.88 0.0.0.3 area 10
        net 10.2.0.0 0.0.255.255 area 10
        pass g0/0/0
        end
    wr
```
## EQUIPAMENTO R_CENTRAL
```
en
    conf t
        hostname R_CENTRAL
        service pass
        enable secret senai@132
        int s0/2/1
            ip add 10.3.204.77 255.255.255.252
            clock rate 4000000
            no shut
        int s0/2/0
            ip add 10.3.204.73 255.255.255.252
            clock rate 4000000
            no shut
        int s0/1/0
            ip add 10.3.204.66 255.255.255.252
            clock rate 4000000
            no shut
        line console 0
            pass senai@132
            login
        line vty 0 4
            pass senai@132
            login local
        exit
        router ospf 90
        router-id 90.90.90.90
        net 10.3.204.76 0.0.0.3 area 0
        net 10.3.204.72 0.0.0.3 area 0
        net 10.3.204.64 0.0.0.3 area 0
        net 10.3.204.68 0.0.0.3 area 0
        end
    wr
```