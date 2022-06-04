## Embratel
```
en
    conf t
        hostnam Embratel
    int g0/0
        ip add 200.1.1.2 255.255.255.252
        no shut
    int g0/1
        ip add 200.1.2.2 255.255.255.252
        no shut
!Informa o ID do AS
    router bgp 65000
!Cadastrar as redes que ele Participa
    network 200.1.1.0 mask 255.255.255.252
    network 200.1.2.0 mask 255.255.255.252
!Declarar o AS e o IP dos Amiguinhos
    neighbor 200.1.1.1 remote-as 65001
    neighbor 200.1.2.1 remote-as 65002
    end
```
## R1
```
en
    conf t
        hostname R1
        ip nat pool 1UNICOIP 200.1.1.1 200.1.1.1 netmask 255.255.255.252
        ip access-list standard LiberaRedeLocal
            permit 192.168.1.0 0.0.0.255
            exit
        ip nat inside source list LiberaRedeLocal pool 1UNICOIP overload
    int g0/1
        ip nat inside
        ip add 192.168.1.1 255.255.255.0
        no shut
    int g0/0
        ip nat outside
        ip add 200.1.1.1 255.255.255.252
        no shut
    router bgp 65001
        network 200.1.1.0 mask 255.255.255.252
        neighbor 200.1.1.2 remote-as 65000
        end
```
## R2
```
en
    conf t
        hostname R2
        ip nat pool 1UNICOIP 200.1.2.1 200.1.2.1 netmask 255.255.255.252
        ip access-list standard LiberaRedeLocal
            permit 192.168.2.0 0.0.0.255
            exit
        ip nat inside source list LiberaRedeLocal pool 1UNICOIP overload
    int g0/0
        ip nat inside
        ip add 192.168.2.1 255.255.255.0
        no shut
    int g0/1
        ip nat outside
        ip add 200.1.2.1 255.255.255.252
        no shut
    router bgp 65002
        network 200.1.2.0 mask 255.255.255.252
        neighbor 200.1.2.2 remote-as 65000
        end
```