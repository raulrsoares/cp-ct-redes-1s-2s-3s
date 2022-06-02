# Desafio Aula 5

## Equipamento RSP
```
en
    conf t
        hostname RSP
        banner motd "Somente pessoal do TI do Senai sao paulo Autorizado !!"
        service password-encryption
        interface g0/0/0
            ip address 192.168.50.190 255.255.255.224
            no shut
        interface s0/1/1
            ip address 10.0.0.17 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.5 255.255.255.252
            clock rate 4000000
            no shut
        line console 0
            password senai@132
            login
        line vty 0 15
            password senai@132
            login
        exit
        int loopback 0
            description RT RSP
            ip add 10.0.1.1 255.255.255.0
            no shut
        router rip
            version 2
            network 192.168.50.0
            ne 10.0.0.16
            ne 10.0.0.4
            no auto-summary
            passive-interface g0/0/0
        end
    wr
```

## Equipamento RITA
```
en
    conf t
        hostname RITA
        banner motd " Somente pessoal do TI do Senai itapira Autorizado !! "
        service password-encryption
        enable secret senai@132
        interface g0/0/0
            ip address 192.168.60.198 255.255.255.248
            no shut
        interface s0/1/1
            ip address 10.0.0.18 255.255.255.252
            no shut
        interface s0/1/0
            ip address 10.0.0.22 255.255.255.252
            no shut
        line console 0
            password senai@132
            login
        line vty 0 15
            password senai@132
            login
        exit
        int loopback 0
            description RT RITA
            ip add 10.0.1.6 255.255.255.0
            no shut
        router rip
            version 2
            network 192.168.60.0
            ne 10.0.0.16
            ne 10.0.0.20
            no auto-summary
            passive-interface g0/0/0
        end
    wr
```

## Equipamento RITU
```
en
    conf t
        hostname RITU
        banner motd "& Somente pessoal do TI do Senai itu Autorizado !! &"
        service password-encryption
        enable secret senai@132
        interface g0/0/0
            ip address 192.168.30.190 255.255.255.224
            no shut
        interface s0/1/1
            ip address 10.0.0.21 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.10 255.255.255.252
            no shut
        line console 0
            password senai@132
            login
        line vty 0 15
            password senai@132
            login
        exit
        int loopback 0
            description RT RITU
            ip add 10.0.1.5 255.255.255.0
            no shut
        router rip
            version 2
            network 192.168.30.0
            ne 10.0.0.20
            ne 10.0.0.8
            no auto-summary
            passive-interface g0/0/0
        end
    wr
```

## Equipamento RJUN
```
en
    conf t
        hostname RJUN
        banner motd " Somente pessoal do TI do Senai JUNDIAI Autorizado !! "
        service password-encryption
        enable secret senai@132
        interface g0/0/0
            ip address 192.168.20.126 255.255.255.192
            no shut
        interface s0/1/1
            ip address 10.0.0.9 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.2 255.255.255.252
            no shut
        line console 0
            password senai@132
            login
        line vty 0 15
            password senai@132
            login
        exit
        int loopback 0
            description RT RJUN
            ip add 10.0.1.4 255.255.255.0
            no shut
        router rip
            version 2
            network 192.168.30.0
            ne 10.0.0.8
            ne 10.0.0.0
            no auto-summary
            passive-interface g0/0/0
        end
    wr
```

## Equipamento RSAN
```
en
    conf t
        hostname RSAN
        banner motd " Somente pessoal do TI do Senai SANTOS Autorizado !! "
        service password-encryption
        enable secret senai@132
        interface g0/0/0
            ip address 192.168.10.254 255.255.255.128
            no shut
        interface s0/1/1
            ip address 10.0.0.1 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.14 255.255.255.252
            no shut
        line console 0
            password senai@132
            login
        line vty 0 15
            password senai@132
            login
        exit
        int loopback 0
            description RT RSAN
            ip add 10.0.1.3 255.255.255.0
            no shut
        router rip
            version 2
            network 192.168.10.0
            ne 10.0.0.12
            ne 10.0.0.0
            no auto-summary
            passive-interface g0/0/0
        end
    wr
```

## Equipamento RJUQ
```
en
    conf t
        hostname RJUQ
        banner motd & Somente pessoal do TI do Senai rt-juq Autorizado !! &
        service password-encryption
        enable secret senai@132
        interface g0/0/0
            ip address 192.168.40.254 255.255.255.0
            no shut
        interface s0/1/1
            ip address 10.0.0.13 255.255.255.252
            clock rate 4000000
            no shut
        interface s0/1/0
            ip address 10.0.0.6 255.255.255.252
            no shut
        line console 0
            password senai@132
            login
        line vty 0 15
            password senai@132
            login
        exit
        int loopback 0
            description RT RSAN
            ip add 10.0.1.2 255.255.255.0
            no shut
        router rip
            version 2
            network 192.168.40.0
            ne 10.0.0.12
            ne 10.0.0.4
            no auto-summary
            passive-interface g0/0/0
        end
    wr
```

#
