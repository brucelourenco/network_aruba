
- SSH Configuration 
https://community.arubanetworks.com/browse/articles/blogviewer?blogkey=f4833466-4ac7-4b08-833f-63e37b19f508

- Create local users
ArubaSwitch(config)# aaa authentication local-user brucesilva group Level-15 password plaintext 

- Create manager user
password manager user-name admin plaintext H1a2p3

- Remove local users
switch(config)# no aaa authentication local-user localuser
switch(config)# no password operator
switch(config)# no password manager


Aruba2930F# show interfaces brief |

case-insensitive      Ignore the case of regular expression while filtering the output.
begin                 Begins unfiltered output of the show command with the first line that contains the regular expression.
exclude               Displays output lines that do not contain the regular expression.
include               Displays output lines that contain the regular expression.

Aruba2930F# show interfaces brief | i Up
  10           100/1000T  | No        Yes     Up     1000FDx    MDI  off  0
  11           100/1000T  | No        Yes     Up     1000FDx    MDIX off  0
  24           100/1000T  | No        Yes     Up     1000FDx    MDIX off  0


No Aruba OS tem uma “pegadinha” para poder ignorar maiúsculas e minúsculas nos comandos:

Tem que usar a opção case antes do tipo de filtro. Veja exemplo abaixo:

Aruba2930F# show interfaces brief | i UP
Aruba2930F# (Não retorna nada pois UP foi escrito diferente do que mostrado no comando)

Usando o case agora :

Aruba2930F# show interfaces brief | case i UP
  10           100/1000T  | No        Yes     Up     1000FDx    MDI  off  0
  11           100/1000T  | No        Yes     Up     1000FDx    MDIX off  0
  24           100/1000T  | No        Yes     Up     1000FDx    MDIX off  0



Aruba2930F# show interfaces status | i Up
  1        Uplinks    Down    Auto          1000FDx  100/1000T  No     1
  2        Uplinks    Down    Auto          1000FDx  100/1000T  No     1
  3        Uplinks    Down    Auto          1000FDx  100/1000T  No     1
  4        Uplinks    Down    Auto          1000FDx  100/1000T  No     1
  5        Uplinks    Down    Auto          1000FDx  100/1000T  No     1
  24                     Up            Auto         1000FDx  100/1000T  multi  1


Aruba2930F# show mac-address

Status and Counters - Port Address Table

  MAC Address       Port                            VLAN
  ----------------- ------------------------------- ----
  38184c-09444e     24                              1
  3c3786-6923ae     24                              1
  50579c-89373e     24                              1
  7085c2-d20014     24                              1
  94eaea-bb0f30     24                              1
  94eaea-bb0f3e     24                              1
  98ded0-ae1881     24                              1
  9cebe8-c35f98     24                              1
  e0d55e-2cc16b     24                              1

Comandos usando filtro  com o pipe (|) 

Aruba2930F# show mac-address |

case-insensitive      Ignore the case of regular expression while filtering the output.
begin                 Begins unfiltered output of the show command with the first line that contains the regular expression.
exclude               Displays output lines that do not contain the regular expression.
include               Displays output lines that contain the regular expression.

Comando show mac-address  que incluem 94ea
        
Aruba2930F# show mac-address | include  94ea
  94eaea-bb0f30     24                              1
  94eaea-bb0f3e     24                              1
                    
OU 

Aruba2930F# show mac-address | i 94ea
  94eaea-bb0f30     24                              1
  94eaea-bb0f3e     24                              1

Comando show mac-address  que começam 94ea


Aruba2930F# show mac-address | begin 98 ou  show mac-address | b 98
  98541b-64444d     24                              1
  98ded0-ae1881     24                              1
  9cebe8-c35f98     24                              1
  a8db03-3f5b65     24                              1
  dcbfe9-98b9a1     24                              1
  e0d55e-2cc16b     24                              1



Comandos principais nos switches Aruba OS

•	show version – mostra versão do sistema operacional

•	show flash – mostra conteúdo de ambas as áreas da flash

•	show running-config - mostra configuração da RAM - running config

•	write memory - grava info da RAM na flash

•	show configuration - mostra o contéudo startup config

•	enable – entra no modo de configuração do switch

•	erase startup-config – apaga o startup config

•	erase config <filename> - Apaga arquivo de configuração especificado do sistema

•	show config <filename>  - Mostra conteúdo do arquivo de configuração especificado

•	show logging – mostra eventos do switch desde o último reboot

•	show logging –a - mostra todos os eventos 

•	show logging –r - mostra todos os eventos no sentido reverse da ordem cronológica.

•	show logging <string> - mostra todos os eventos que contém a string especificada.

•	vlan <id> - cria uma vlan com id definido pelo parâmetro <id>

•	tag <port> - configure a vlan com tag na porta especificada

•	untag <port> - configure a vlan como untagged para a porta especificada

•	no vlan <id> – remove a vlan com id especificado

•	show vlans – mostra todas as Vlans do Switch

•	show vlans <vlan-id> - mostra as portas que fazem parte da vlan identificada pelo vlan ID

•	show vlans port <port-id> detail – mostra informação de Vlan de uma porta específica

•	show ip – mostra Configuração IP

•	ip routing – habilita roteamento IP do switch L3

•	ip default-gateway <ip> - configure default-gateway do switch

•	write memory – salva as configurações na flash

•	copy startup-config tftp 10.x.2.100 <filename> - copia arquivo de configuração do servidor TFTP Externo

•	copy tftp flash 10.x.2.100 <filename> <flash_area> copia arquivo de configuração para o servidor TFTP

•	ping <IP address | hostname> - faz um ping para o IP especificado

•	traceroute <IP address> | hostname – faz um traceroute para o IP especificado 

•	show arp – mostra tabela arp do switch

•	show mac – mostra tabela MAC do switch

•	show mac – com pipe (|)

•	show mac | case – ignora letras maiúsculas e minúsculas no filtro

•	show mac | include – usa o filtro include 

show mac | include  aeaa

•	show mac | begin – usa o filtro pipe begin

•	show mac | exclude – usa o filtro pipe exclude

•	show interfaces status – mostra status de todas as portas

•	show interfaces brief – mostra resumo de todas as portas 

•	show interfaces config – 

Aruba2930F# show interfaces config

Port Settings

  Port    Type       | Enabled Mode         Flow Ctrl MDI
  ------- ---------- + ------- ------------ --------- ----
  1       100/1000T  | Yes     Auto         Disable   Auto
  2       100/1000T  | Yes     Auto         Disable   Auto
  3       100/1000T  | Yes     Auto         Disable   Auto


•	show config interface – mostra configuração de todas as portas

Aruba2930F# show config interface

Startup configuration: 89

interface 1
   name "Uplinks"
   untagged vlan 1
   exit
interface 2
   name "Uplinks"
   untagged vlan 1
   aaa port-access authenticator
   aaa port-access authenticator quiet-period 30
   exit
interface 3
   name "Uplinks"
   untagged vlan 1

•	show config interface < número da interface> - mostra configuração de uma porta em particular

Ex. show config interface 24

- Configuring Stack

### 48P ###
conf t
vsf member 1 link 1 49
vsf member 1 link 2 50
vsf enable domain 1

conf t
vsf member 2 link 1 49
vsf member 2 link 2 50
vsf enable domain 1

### 24P ###
conf t
vsf member 1 link 1 25
vsf member 1 link 2 26
vsf enable domain 1

conf t
vsf member 2 link 1 25
vsf member 2 link 2 26
vsf enable domain 1

ou

vsf member 1 link 1 27
vsf member 1 link 2 28
vsf enable domain 1

vsf member 2 link 1 27
vsf member 2 link 2 28
vsf enable domain 1

- Desconfigurar Stack
conf t
vsf member 1 remove
vsf disable
vsf member 2 remove
vsf disable


=====================================

- Unsupported transceiver option

allow-unsupported-transceiver

fonte: https://community.arubanetworks.com/blogs/esupport1/2019/03/19/unsupported-transceiver-option 

=====================================
Ativar NTP

timesync ntp
ntp unicast
ntp server 10.1.17.19 iburst
ntp enable

=====================================
console baud rate change

switch(config)# console baud-rate 9600
=====================================


