## Лабораторная работа - Реализация DHCPv4 
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab10/23.png)    
⦁	Создание сети и настройка основных параметров устройства
В первой части лабораторной работы вам предстоит создать топологию сети и настроить базовые параметры для узлов ПК и коммутаторов.
⦁	Создание схемы адресации
Подсеть сети 192.168.1.0/24 в соответствии со следующими требованиями:
⦁	Одна подсеть «Подсеть A», поддерживающая 58 хостов (клиентская VLAN на R1).
Подсеть A - 192.168.1.0/26 (.1 -.63)
Запишите первый IP-адрес в таблице адресации для R1 G0/0/1.100 . 
⦁	Одна подсеть «Подсеть B», поддерживающая 28 хостов (управляющая VLAN на R1). 
Подсеть B: 192.168.1.64/27 (.65-.95)
Запишите первый IP-адрес в таблице адресации для R1 G0/0/1.200. Запишите второй IP-адрес в таблице адресов для S1 VLAN 200 и введите соответствующий шлюз по умолчанию.
⦁	Одна подсеть «Подсеть C», поддерживающая 12 узлов (клиентская сеть на R2).
Подсеть C: 192.168.1.96/28 (.97-.111)
Запишите первый IP-адрес в таблице адресации для R2 G0/0/1.

### Произведите базовую настройку маршрутизаторов
```
router(config)# hostname R1
router(config)# hostname R1
R1(config)# enable secret class
R1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# line vty 0 4
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# service password-encryption
R1(config)# banner motd $ Authorized Users Only! $
R1# copy running-config startup-config
R1(config)# interface g0/0/1
R1(config-if)# no shutdown
R1(config-if)# exit
```
### Настройка маршрутизации между сетями VLAN на маршрутизаторе R1

```
R1(config)# interface g0/0/1.100
R1(config-subif)# description Client Network
R1(config-subif)# encapsulation dot1q 100
R1(config-subif)# ip address 192.168.1.1 255.255.255.192
R1(config-subif)# interface g0/0/1.200
R1(config-subif)# encapsulation dot1q 200
R1(config-subif)# description Management Network
R1(config-subif)# ip address 192.168.1.65 255.255.255.224
R1(config-subif)# interface g0/0/1.1000
R1(config-subif)# encapsulation dot1q 1000 native
R1(config-subif)# description Native VLAN
```
```
R1# show ip interface brief
Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0/0   unassigned      YES unset  administratively down down
GigabitEthernet0/0/1   unassigned      YES unset  up                    up
Gi0/0/1.100            192.168.1.1     YES manual up                    up
Gi0/0/1.200            192.168.1.65    YES manual up                    up
Gi0/0/1.1000           unassigned      YES unset  up
```
### Настройте G0/1 на R2, затем G0/0/0 и статическую маршрутизацию для обоих маршрутизаторов
```
R2(config)# interface g0/0/1
R2(config-if)# ip address 192.168.1.97 255.255.255.240
R2(config-if)# no shutdown
R2(config-if)# exit
```
```
R1(config)# interface g0/0/0
R1(config-if)# ip address 10.0.0.1 255.255.255.252
R1(config-if)# no shutdown

R2(config)# interface g0/0/0
R2(config-if)# ip address 10.0.0.2 255.255.255.252
R2(config-if)# no shutdown
```
```
R1(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.2
R2(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.1
```

### Настройте базовые параметры каждого коммутатора
```
switch(config)# hostname S1
S1(config)# no ip domain-lookup
S1(config)# enable secret class
S1(config)# line console 0
S1(config-line)# password cisco
S1(config-line)# login
S1(config)# line vty 0 4
S1(config-line)# password cisco
S1(config-line)# login
S1(config)# service password-encryption
S1(config)# banner motd $ Authorized Users Only! $
S1(config)# exit
S1# copy running-config startup-config
```
### Создайте сети VLAN на коммутаторе S1
```
S1(config)# vlan 100
S1(config-vlan)# name Clients
S1(config-vlan)# vlan 200
S1(config-vlan)# name Management
S1(config-vlan)# vlan 999
S1(config-vlan)# name Parking_Lot
S1(config-vlan)# vlan 1000
S1(config-vlan)# name Native
S1(config-vlan)# exit
S1(config)# interface vlan 200
S1(config-if)# ip address 192.168.1.66 255.255.255.224
S1(config-if)# no shutdown
S1(config-if)# exit
S1(config)# ip default-gateway 192.168.1.65
S2(config)# interface vlan 1
S2(config-if)# ip address 192.168.1.98 255.255.255.240
S2(config-if)# no shutdown
S2(config-if)# exit
S2(config)# ip default-gateway 192.168.1.97
S1(config)# interface range f0/1 - 4, f0/7 - 24, g0/1 - 2
S1(config-if-range)# switchport mode access
S1(config-if-range)# switchport access vlan 999
S1(config-if-range)# shutdown
S1(config-if-range)# exit

S2(config)# interface range f0/1 - 4, f0/6 - 17, f0/19 - 24, g0/1 - 2
S2(config-if-range)# switchport mode access
S2(config-if-range)# shutdown
S2(config-if-range)# exit
```
###  Назначьте сети VLAN соответствующим интерфейсам коммутатор
```
S1(config)# interface f0/6
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 100
```
S1# show vlan brief

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/5
100  Clients                          active    Fa0/6
200  Management                       active    
999  Parking_Lot                      active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/7, Fa0/8, Fa0/9, Fa0/10
                                                Fa0/11, Fa0/12, Fa0/13, Fa0/14
                                                Fa0/15, Fa0/16, Fa0/17, Fa0/18
                                                Fa0/19, Fa0/20, Fa0/21, Fa0/22
                                                Fa0/23, Fa0/24, Gi0/1, Gi0/2
1000 Native                           active
1002 fddi-default                     act/unsup
1003 token-ring-default               act/unsup
1004 fddinet-default                  act/unsup
1005 trnet-default                    act/unsup
```
Почему интерфейс F0/5 указан в VLAN 1? так как находится в  VLAN по умолчанию и не настроен как магистраль 802.1Q.  
### Вручную настройте интерфейс S1 F0/5 в качестве транка 802.1Q
```
S1(config)# interface f0/5
S1(config-if)# switchport mode trunk
S1(config-if-range)# switchport trunk native vlan 1000
S1(config-if-range)# switchport trunk allowed vlan 100,200,1000
S1(config)# exit
S1# copy running-config startup-config
```
Какой IP-адрес был бы у ПК, если бы он был подключен к сети с помощью DHCP? в диапазоне 169.254.xx  

## Настройте R1 с пулами DHCPv4 для двух поддерживаемых подсетей. Ниже приведен только пул DHCP для подсети A
```
R1(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.5
R1(config)# ip dhcp pool R1_Client_LAN
R1(dhcp-config)# network 192.168.1.0 255.255.255.192
R1(dhcp-config)# domain-name ccna-lab.com
R1(dhcp-config)# default-router 192.168.1.1
R1(dhcp-config)# lease 2 12 30
R1(config)# ip dhcp excluded-address 192.168.1.97 192.168.1.101
R1(config)# ip dhcp pool R2_Client_LAN
R1(dhcp-config)# network 192.168.1.96 255.255.255.240
R1(dhcp-config)# default-router 192.168.1.97
R1(dhcp-config)# domain-name ccna-lab.com
R1(dhcp-config)# lease 2 12 30
R1# copy running-config startup-config
```
## Проверка конфигурации сервера DHCPv4
```
Router#show ip dhcp pool

Pool R1_Client_LAN :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 62
 Leased addresses               : 0
 Excluded addresses             : 2
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 192.168.1.1          192.168.1.1      - 192.168.1.62      0    / 2     / 62

Pool R2_Client_LAN :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 14
 Leased addresses               : 0
 Excluded addresses             : 2
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 192.168.1.97         192.168.1.97     - 192.168.1.110     0    / 2     / 14
Router#show ip dhcp bindings 
                           ^
% Invalid input detected at '^' marker.
	
Router#show ip dhcp binding
IP address       Client-ID/              Lease expiration        Type
                 Hardware address
Router#show ip dhcp server statistics 
                    ^
% Invalid input detected at '^' marker.
	
Router#show ip dhcp binding
IP address       Client-ID/              Lease expiration        Type
                 Hardware address
192.168.1.6      000B.BEC8.E581           --                     Automatic
192.168.1.102    000B.BED7.35A9           --                     Automatic
Router#
```
```
```
C:\>ipconfig /all

FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: ccna-lab.com
   Physical Address................: 000B.BEC8.E581
   Link-local IPv6 Address.........: FE80::20B:BEFF:FEC8:E581
   IPv6 Address....................: ::
   IPv4 Address....................: 192.168.1.6
   Subnet Mask.....................: 255.255.255.192
   Default Gateway.................: ::
                                     192.168.1.1
   DHCP Servers....................: 192.168.1.1
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-1C-70-C6-5B-00-0B-BE-C8-E5-81
   DNS Servers.....................: ::
                                     0.0.0.0

Bluetooth Connection:

   Connection-specific DNS Suffix..: ccna-lab.com
   Physical Address................: 0002.1619.A45B
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0
   DHCP Servers....................: 0.0.0.0
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-1C-70-C6-5B-00-0B-BE-C8-E5-81
   DNS Servers.....................: ::
                                     0.0.0.0


C:\>ping 10.0.0.1

Pinging 10.0.0.1 with 32 bytes of data:

Reply from 10.0.0.1: bytes=32 time<1ms TTL=255
Reply from 10.0.0.1: bytes=32 time<1ms TTL=255
Reply from 10.0.0.1: bytes=32 time=3ms TTL=255
Reply from 10.0.0.1: bytes=32 time<1ms TTL=255

Ping statistics for 10.0.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 3ms, Average = 0ms
```
## Настройка и проверка DHCP-ретрансляции на R2
```
R2(config)# interface g0/0/1
R2(config-if)# ip helper-address 10.0.0.1
R2(config-if)# exit
R2# copy running-configuration startup-configuration
```
## Попытка получить IP-адрес от DHCP на PC-B
```
C:\>ipconfig /all

FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: ccna-lab.com
   Physical Address................: 000B.BED7.35A9
   Link-local IPv6 Address.........: FE80::20B:BEFF:FED7:35A9
   IPv6 Address....................: ::
   IPv4 Address....................: 192.168.1.102
   Subnet Mask.....................: 255.255.255.240
   Default Gateway.................: ::
                                     192.168.1.97
   DHCP Servers....................: 10.0.0.1
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-D8-94-39-40-00-0B-BE-D7-35-A9
   DNS Servers.....................: ::
                                     0.0.0.0

Bluetooth Connection:

   Connection-specific DNS Suffix..: ccna-lab.com
   Physical Address................: 00D0.5808.A650
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0
   DHCP Servers....................: 0.0.0.0
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-D8-94-39-40-00-0B-BE-D7-35-A9
   DNS Servers.....................: ::
                                     0.0.0.0


C:\>ping 10.0.0.2

Pinging 10.0.0.2 with 32 bytes of data:

Reply from 10.0.0.2: bytes=32 time<1ms TTL=255
Reply from 10.0.0.2: bytes=32 time<1ms TTL=255
Reply from 10.0.0.2: bytes=32 time<1ms TTL=255
Reply from 10.0.0.2: bytes=32 time=1ms TTL=255

IP address       Client-ID/              Lease expiration        Type
                 Hardware address
192.168.1.6      000B.BEC8.E581           --                     Automatic
192.168.1.102    000B.BED7.35A9           --                     Automatic
```
