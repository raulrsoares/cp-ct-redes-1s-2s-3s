# *Aula 02*

Hoje termianr a aparte lógica da hierarquia.

* 1º Ligar a vm;
* 2º Configurar interfaces de Rede
*     # cat /etc/network/interfaces
* 3º Copia de segurança do arquivo de rede
*     # cp /etc/network/interfaces /root
* 4º Editar o arquivo - primeiro instalar o vim se não tiver instalado
*     # apt get update 
*     # apt get install vim

### *Copia de segurança do arquivo de rede*
~~~
# cp /etc/network/interfaces /root
~~~
### *Identificar interfaces de Rede*
~~~
# ip a
~~~
marque o nome das interfaces/mac para documentação.

* enp0s3 - 08:00:27:48:11:f2
* enp0s8 - 08:00:27:52:f9:57
* enp0s9 - 08:00:27:8c:aa:20

~~~
Interfaces de Redes
  IF0 - enp0s3 - 08:00:27:48:11:f2 - Servidores (Adaptador 1) - 172.31.1.254/24
  IF1 - enp0s8 - 08:00:27:52:f9:57 - Externa (Adaptador 2) - DHCP
  IF2 - enp0s9 - 08:00:27:8c:aa:20 - Cliente (Adaptador 3) - 10.10.1.6 /20
~~~

### *Para fazer a edição do arquivo*

    # vim.tiny /etc/network/interfaces

### *No terceiro # apagar a ultima linha*
    
    # iface ens33 inet dhcp

### *De enter uma vez e escreva:*
~~~
#enp0s3 - IF0 (Adaptador 1 do VirtualBox)
#SERVIDORES - 172.31.1.254/24
auto enp0s3
iface enp0s3 inet static
address 172.31.1.254
netmask 255.255.255.0
~~~
### *outro enter:*
~~~
#enp0s8 - IF1 (Adaptador 2 do VirtualBox)
#EXTERNA - DHCP
auto enp0s8
iface enp0s8 inet dhcp
~~~
### *mais um enter:*
~~~
#enp0s9 - IF2 (Adaptador 3 do VirtualBox)
#CLIENTE - 10.10.1.6/29
auto enp0s9
iface enp0s9 inet static
address 10.10.10.1.6
netmask 255.255.255.248
~~~
## *Use ":wq" para salvar e sair*
### *Reiniciar serviços linux*
~~~
systemctl restart/status/reload NOMEDOSERVICO
/etc/init.d/NOMEDOSREVICO restart/status/reload
services NOMEDOSERVICO restart/status/reload
~~~

### *Va para o terminal 6*
~~~
ctrl + fn + alt + f6
ctrl + alt + f6
alt +f6
alt + seta direira/esquerda até o terminal 6 
~~~
### *Log de Sistema*
~~~
tail -f (tempo real/recorrente) -n 100 (linhas) /var/log/syslog
~~~
## *Verificar o resolf.conf(DNS RESOLVER)*
~~~
# cat /etc/resolv.conf
~~~
*Abra o VirtualBox rode a tela até a parte de rede e selecione a "externa" e mude para nat, REINICIE as placas de rede
## *Repositórios*
~~~
# cat /etc/apt/sources.list
~~~
Atualize os repositórios usando o *apt update*, após isso de um *apt upgrade* para instalar os novos arquivos.

### *Baixar Repositórios/Pacotes*
~~~
# apt update -y
~~~

### *Instalar os arquivos baixados*
~~~
# apt upgrade -y
~~~

Pode ir para outra vty e continuar utilizando o Linux enquanto ocorre a atualização .
Após a instalação concluida instale o vim 
~~~
# apt install vim 
~~~

# *Subir Cliente*
~~~
Abrir (C:) \VMS\OVAS
		Windows 7 Ultimate Base - click x2
			Nome: CLIW7-TOQUIO
			Tipo de Sistema Operacional Convidado - Double click em Windows vista > Microsoft Windows > Windows 7 (64-Bit)
			Desmarcar Placa de Rede 
			Mudar o Nome do HD para - SRVFW-BERLIM.vmdk
			Publitica de Endereço Mac :Gerar Novos Endereços...
			Opções Adcionais :Desmarcar 
			Importar
Deixar Importando

