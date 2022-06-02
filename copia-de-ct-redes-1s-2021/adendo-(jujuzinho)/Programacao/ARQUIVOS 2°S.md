# COMANDOS 2°S

## **RIP** 

**Configuração do RIP v1 no roteador R2:**
```
R2>en
R2#conf t
R2(config)#router rip
R2(config-router)#network 192.168.1.0
R2(config-router)#network 192.168.0.0
```
**Configuração do RIP v2 no roteador R2:**
```
R2>en
R2#conf t
R2(config)#router rip
R2(config-router)#version 2
R2(config-router)#no auto-summary
R2(config-router)#network 192.168.1.0
R2(config-router)#network 192.168.0.0
```
## **OSPF**

**Configurando OSPF MULTIAREA**

**Especificar Redes que o Router participa**
```
R1>en
R1#conf t
R1(config)#router ospf 10 
R1(config-router)#router-id 1.1.1.1
R1(config-router)#network 10.1.1.1 0.0.0.0 area 1
R1(config-router)#network 10.1.2.1 0.0.0.0 area 1
R1(config-router)#network 192.168.10.1 0.0.0.0 area 1
R1(config-router)#end
```
**Especificar interfaces que não tem roteadores em suas exteremidades**
```
R1(config)#router ospf 10 
R1(config)#passive-interfaces GigabiEthernet 0/0
R1(config)#end 
```
**Ver redes cadastradas na area participantes**
```
R1#show ip protocols
```
**Verificar area**
```
R1#show ip ospf interface brief
```
## **STP**
**Verificar Spanning Tree por VLAN
Aqui identificamos se o switch é root bridge da VLAN**
```
R1#show spanning-tree vlan 10
```
**Ver Interfaces**
```
R1#show interfaces 
```
**Ver somente as FastEthernet**
```
R1#show interfaces | in FastEthernet 
```
**Ver todas as interfaces conectadas do Spanning-tree**
```
R1#show spanning-tree detail
```
**Ver MAC somente das interfaces conectadas e ativas** 
```
R1#show mac-address-table
```
**Ver MAC somente das interfaces conectadas e não ativas**
```
R1#show interfaces | in line protocol | address
```
**Mudar o Switch (Root Bridge)**
```
R1(config)# spanning-tree vlan 1 priority 28672
```
**Verificar qual a prioridade do Root ID antes de mudar / Visualizar Canal Etherchannel por Porta**
```
R1#show etherchannel summary
```
**Visualizar Portas**
```
#show ip interface brief
```
**Visualizar Canal Etherchannel**
```
R1#show etherchannel
```
**Mostram o port channel como um link lógico**
```
R1#show interfaces trunk 
R1#show spanning-tree 
```
**Configurar Link Aggreggation LACP**
```
R1>enable
R1#configure terminal
R1(config)# interface range gigabitEthernet 1/1-2
R1(config-if)# channel-protocol lacp
R1(config-if)# channel-group 1 mode active
    ou
R1(config-if)# channel-group 1 mode passive
```
**Configurar Link Aggreggation PAgP**
```
R1>enable
R1#configure terminal
R1(config)# interface range gigabitEthernet 1/1-2
R1(config-if)# channel-protocol pagp
R1(config-if)# channel-group 1 mode auto
    ou
R1(config-if)# channel-group 1 mode desirable
```
***
!Status das Portas
#show port-channel summary
Sinalizadores: 
D - Down (desligado)
P - port-channel está Up (ligado) (membros estão funcionais)
I - Individual 
H - Hot-standby (Link em espera) (somente LACP)
s - recurso suspenso - módulo removido
S - Comutado 
R - Roteado
U – Up (ligado) (canal lógico)

show running-config
.....
***
>**config não estão certas**      
>**Observar que foi criada uma interfadce virtual chamada Port-channel 1
>Toda mudança é feita na porta "Port-channel 1"**
```
interface GigabitEthernet0/1
 channel-protocol lacp
 channel-group 1 mode active

interface GigabitEthernet0/0
 channel-protocol lacp
 channel-group 1 mode active

interface Port-channel 1
```
***
**Verificar IPs**
```
R1#show ip interface brief
```
**Verificar outside e inside em alguma interface**
```
R1#show run
```
**Verificar rotas**
```
R1#show ip route
```
**Verificar rotas**
```
R1#show ip nat statistics
```
**Ver Traduções**
```
R1#show ip nat translations

Pro  Inside global     Inside local       Outside local      Outside global
---  64.100.50.1       172.16.16.1        ---                ---

R1#show run

    (procure por interface GigabitEthernet)

interface GigabitEthernet0/0
 ip address 172.16.16.14 255.255.255.240
 ip nat inside
 duplex auto
 speed auto
!
interface Serial0/0/0
 ip address 209.165.128.130 255.255.255.248
 ip nat outside
!
```
**Ver tipos de NAT ativos**
```
R1#show ip nat statistics

Total translations: 1 (1 static, 0 dynamic, 0 extended)
Outside Interfaces: Serial0/0/0
Inside Interfaces: GigabitEthernet0/0
```

**Criar NAT Dinâmico**
```
Passo 1 - ACL
R1(config)#ip access-list standard LAN
R1(config-std-nacl)#permit 192.168.0.0 0.0.0.255

Passo 2 - Criar NAT Pool 
R1(config)#ip nat pool Intervalo-IPs-WAN 200.0.0.101 200.0.0.110

Passo 3 - Criação NAT Dinamico
R1(config)#ip nat inside source list LAN pool Intervalo-IPs-WAN
```
**Criar PAT**
```
Passo 1 - Criar Pool com Unico Endereço
R1(config)#ip nat pool IP-WAN-PAT 200.0.0.103

Passo 2 - Criar ACL
R1(config)#ip access-list standard PAT
R1(config-std-nacl)#permit 192.168.1.0 0.0.0.255

Passo 3 - Criar regra PAT aplicando na Interface 
R1(config)#ip nat inside source list PAT interface Serial 0/0/0 orverload
```
**Criar NAT Estatico (static) usando todas as porta** 
```
R1(config)#ip nat inside source static 192.168.2.100 200.0.0.100
```
**Criar NAT Estatico (static) usando portas especificas, mais segurança**
```
R1(config)#ip nat inside source static 192.168.2.100 80 200.0.0.3 8080
```
**Limpar tabela de NAT  inteira**
```
#clear ip nat translation *

Vejamos que o STATIC sempre esta lá fixo
```
# **ACL**
**Verificar em qual porta esta aplicada a ACL**
```
R1(config)#show running-config
```
**Atrelar ACL a interface**
```
(config)# interface serial 0/0/0
(config-if)# ip access-group 11 out
```
**Remover ACL da interface**
```
R1(config)# interface serial 0/0/0
R1(config-if)# no ip access-group 11 out
```
**Criar ACL Padrão Numerica (Consigo filtrar Protocolos de Transporte (TCP e UDP)**
```
R1(config)# access-list 99 permit tcp 192.168.0.0 0.0.0.255 range 1024 65535 host 172.16.30.2 eq www
```
**Criar ACL Extendida Numerica (Consigo filtrar Protocolos de Transporte (TCP e UDP)**
```
R1(config)# access-list 101 permit tcp 192.168.0.0 0.0.0.255 range 1024 65535 host 172.16.30.2 eq www
```
**Criar ACL Padrão Nomeada (Consigo filtrar protocolos de Transporte (TCP e UDP)**
```
R1(config)# ip access-list standard LiberaRede192
R1(config-std-nacl)# 10 permit tcp 192.168.0.0 0.0.0.255 host 10.0.0.1 eq 80
R1(config-std-nacl)# 20 deny tcp any any
```
**Criar ACL Extendida Nomeada (Consigo filtrar protocolos de Transporte (TCP e UDP)**
```
R1(config)# ip access-list extended Lib_Visitante_APP
R1(config-std-nacl)# 10 permit ip 192.168.0.1 0.0.0.0 host 172.16.0.2
R1(config-std-nacl)# 20 permit icmp 192.168.0.1 0.0.0.0 host 172.16.0.2
R1(config-std-nacl)# 30 deny ip any any
```
**Verificar as ACLs**
```
R1# show access-lists

    Exemplo:
R1# show access-lists
Standard IP access list 11
    10 deny 192.168.10.0 0.0.0.255 (8 match(es))
    20 permit any (7 match(es))
```
**Criar ACL numerada e criar um Comentario**
```
R1(config)#access-list 1 remark Rede_LAN_S1
R1(config)#access-list 1 permit 192.168.10.0 0.0.0.255
R1(config)#access-list 1 deny any
R1(config)#do show access-list
```
**Criar ACL Padrão nomeada - Simples**
```
R1(config)#ip access-list standard NO_ACCESS
R1(config-std-nacl)#20 permit any
R1(config-std-nacl)#10 deny host 192.168.11.10
```
**Proteção Login com ACL**
```
line vty 0 4
login local
transport input ssh
access-class 21 in
exit
access-list 21 permit 192.168.10.0 0.0.0.255
access-list 21 deny any
```
# **HRSP**
```
R1
Configuração
(config)# interface gigabitEthernet 0/0
(config-if)# ip add 192.168.0.2 255.255.255.0
(config-if)# no shut

(config-if)# standby version 2
(config-if)# standby 1 ip 192.168.0.1
(config-if)# standby 1 priority 150

R2
    
Configuração
(config)# interface gigabitEthernet 0/0
(config-if)# ip add 192.168.0.3 255.255.255.0
(config-if)# no shut
(config-if)# standby version 2
(config-if)# standby 1 ip 192.168.0.1
(config-if)# standby 1 priority 100


Por padrão é 100
```

**Ver configuração do HRSP**
```
R1#show standby brief
```

**Ver rotas pelo Tracert**
```
CMD
tracert <ip>
```
## **BGP**

**Configurando BGP em R1**
```
R1#
R1# configurar terminal
R1(config) # ip route 20.0.0.0 255.0.0.0 192.168.1.2
R1(config) #router bgp 1000
R1(config-router) # Neighbor 20.0.0.1 remote-as 2000
R1(config-router) # vizinho 20.0.0.1 update-source loopback 1
R1(config-roteador) # vizinho 20.0.0.1 ebgp-multihop 2
R1(config-router) #network 21.0.0.0 mask 255.0.0.0
R1(config-router) #exit
R1(config) #exit
R1#
```
**Configurando BGP em R2**
```
R2#
R2#configurar terminal
R2(config) #ip route 10.0.0.0 255.0.0.0 192.168.1.1
R2(config) #router bgp 2000
R2(config-roteador) # vizinho 10.0.0.1 remoto-as 1000
R2(config-router) # Neighbor 10.0.0.1 update-source loopback 1
R2(config-roteador) # vizinho 10.0.0.1 ebgp-multihop 2
R2(config-roteador) #exit
R2(config) #exit
```
## **TUNNEL**

**Configurando TUNNEL em RA**
```
RA>en
RA#conf t 
RA(config) #interface tunnel 0 
RA(config-if) #ip add 10.10.10.1 255.255.255.252 
RA(config-if) #tunnel source s0/0/0
RA(config-if) #tunnel destination 209.165.122.2 
RA(config-if) #tunnel mode gre ip 
RA(config-if) #no shut 
RA(config-if) #exit 

RA(config) #ip route 192.168.2.0 255.255.255.0 10.10.10.2
```

**Configurando TUNNEL em RB**
```
RB>en
RB#conf t 
RB(config) #interface tunnel 0 
RB(config-if) #ip add 10.10.10.2 255.255.255.252 
RB(config-if) #tunnel source s0/0/0
RB(config-if) #tunnel destination 64.103.211.2 
RB(config-if) #tunnel mode gre ip 
RB(config-if) #no shut 
RB(config-if) #exit 
RB(config) #
```
## **PPP**
**Configurando PPP em R1**
```
R1

R1>en
R1#conf t

	!1a - Passo - Trocar o encapsulamaneto da Interface para PPP  
R1(config) #interface s0/0/0
R1(config-if) #encapsulation ppp
R1(config-if) #exit

	!2b - Passo - Criar usuario de Conexao R3 com senha class
R1(config) #username R3 secret class

	!3a - Passo - Informar o usuario de Conexao R1 com senha cisco
R1(config) #interface s0/0/0
R1(config-if) #ppp authentication pap
R1(config-if) #ppp pap sent-username R1 password cisco
R1(config-if) #exit

```
**Configurando PPP em R3**
```
R3>en
R3#conf t
	!1b - Passo - Entrar na interface e ativar encapsulamento PPP
R3(config) #interface s0/0/0
R3(config-if) #encapsulation ppp

	!2a - Passo - Criar usuario de Conexao R1 com senha cisco
R3(config-if) #username R1 secret cisco

	!3b - Passo - Logar com o usuário R3 e ativar metodo de autenticacao PAP
R3(config) #interface s0/0/0
R3(config-if) #ppp authentication pap
R3(config-if) #ppp pap sent-username R3 password class
R3(config-if) #exit


	!1d Mudar encapsulamento
R3(config) #interface s0/0/1
R3(config-if) #encapsulation ppp

R3(config-if) #interface s0/1/0
R3(config-if) #encapsulation ppp
R3(config-if) #exit

	!3c Passa - Criar usuário e Senha para o R2
R3(config) #username R2 secret cisco

	!3d Logar com usuário e mudar o metodo de autenticação PAP
R3(config-if) #interface s0/0/1
R3(config-if) #ppp authentication pap
R3(config-if) #ppp pap sent-username R3 password class
R3(config-if) #exit

R3(config) #username ISP secret cisco
R3(config-if) #interface serial0/1/0
R3(config-if) #ppp authentication chap
R3(config-if) #exit

```
**Configurando PPP em R2**
```
R2>en
R2#conf t
 1c Mudar encapsulamento da interface S0/0/1
R2(config) #interface s0/0/1
R2(config-if) #encapsulation ppp
R2(config-if) #exit
 2d Criar usuário de conexão para o R3
R2(config) #username R3 secret class
 3c Conectar com usuario R2 no metodo PAP
R2(config) #interface s0/0/1
R2(config-if) #ppp authentication pap
R2(config-if) #ppp pap sent-username R2 password cisco
R2(config-if) #exit
```
**Configurando PPP em ISP**
```
ISP>en
ISP#conf t
ISP(config) #interface s0/0/0
ISP(config-if) #encapsulation ppp
ISP(config-if) #exit
ISP(config) #hostname ISP
ISP(config) #username R3 secret cisco
ISP(config) #interface s0/0/0
ISP(config-if) #ppp authentication chap
ISP(config-if) #exit
```
