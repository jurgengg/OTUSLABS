### Курс Network engineer. Basic
### Тема проекта: Проектирование сети организации с использованием технологий динамической маршрутизации, резервированием и безопасности 
### Автор: Башаев Юрий

### Цели проекта:  
В качестве цели проекта была выбрано создать с нуля сеть небольшой организации "Карта мира", которая имеет несколько удаленных друг от друга филиалов.  
Задачами к проектированию сети ставилось обеспечить: Создание VLAN`ов для каждого отдела организации, Обеспечение защиты от сетевых атак, Настройка динамической маршрутизации, Настройка динамической выдачи IP адресов  
Для реализации были выбраны следующие технологии:  OSPF, Spanning Tree Protocol, NAT, VLAN, Port Security,DHCP  
## Разработанная схема локальной сети организации:  
![](https://github.com/jurgengg/OTUSLABS/blob/main/proekt/7.png)  
Начинаем с базовой настройки каждого коммутатора
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
## VLAN
Создадим необходимые VLAN и распеделим порты на коммутаторе S1
```
S1(config-vlan)#vlan 10
S1(config-vlan)#name Sales
S1(config-vlan)#vlan 20
S1(config-vlan)#name Operations
S1(config-vlan)#vlan 999
S1(config-vlan)#name Parking_lot
S1(config-if-range)#int fa0/5
S1(config-if)#switchport mode access 
S1(config-if)#switchport access vlan 10
S1(config-if-range)#int range fa0/6-7
S1(config-if)#switchport mode access 
S1(config-if)#switchport access vlan 20
S1(config)#int range f0/1-4
S1(config)# switchport mode trunk
S1(config)#switchport trunk allowed vlan 10,20
S1(config)#int range f0/8-24, gi0/1-2
S1(config-if-range)#switchport mode access 
S1(config-if-range)#switchport access vlan 999
S1(config-if-range)#shutdown 
```
Создадим необходимые VLAN и распеделим порты на коммутаторе S2
```
S2(config-vlan)#vlan 10
S2(config-vlan)#name Sales
S2(config-vlan)#vlan 20
S2(config-vlan)#name Operations
S2(config-vlan)#vlan 999
S2(config-vlan)#name Parking_lot
S2(config-if-range)#int fa0/6
S2(config-if)#switchport mode access 
S2(config-if)#switchport access vlan 20
S2(config)#int range f0/1-4
S2(config)# switchport mode trunk
S2(config)#switchport trunk allowed vlan 10,20
S2(config-if-range)#int range fa0/5, fa0/7
S2(config-if)#switchport mode access 
S2(config-if)#switchport access vlan 10
S2(config)#int range f0/8-24, gi0/1-2
S2(config-if-range)#switchport mode access 
S2(config-if-range)#switchport access vlan 999
S2(config-if-range)#shutdown 
```
Создадим необходимые VLAN и распеделим порты на коммутаторе S3
```
S3(config-vlan)#vlan 10
S3(config-vlan)#name Sales
S3(config-vlan)#vlan 20
S3(config-vlan)#name Operations
S3(config-vlan)#vlan 999
S3(config-vlan)#name Parking_lot
S3(config)#int range f0/1-5
S3(config)# switchport mode trunk
S3(config)#switchport trunk allowed vlan 10,20
S3(config)#int range f0/6-24, gi0/1-2
S3(config-if-range)#switchport mode access 
S3(config-if-range)#switchport access vlan 999
S3(config-if-range)#shutdown
```
Создадим необходимые VLAN и распеделим порты на коммутаторе S4
```
S4(config-vlan)#vlan 30
S4(config-vlan)#name Admin
S4(config-vlan)#vlan 40
S4(config-vlan)#name Buhgalteriya
S4(config-vlan)#vlan 999
S4(config-vlan)#name Parking_lot
S4(config)#int range f0/6-24, gi0/1-2
S4(config-if-range)#switchport mode access 
S4(config-if-range)#switchport access vlan 999
S4(config-if-range)#shutdown
S4(config-if-range)#int range fa0/1, fa0/4
S4(config-if)#switchport mode access 
S4(config-if)#switchport access vlan 30
S4(config-if-range)#int range fa0/2-3
S4(config-if)#switchport mode access 
S4(config-if)#switchport access vlan 40
S4(config)#int range f0/1-5
S4(config)# switchport mode trunk
S4(config)#switchport trunk allowed vlan 30,40
```

### Проверка созданных Vlan на S1
```
Switch#sh vlan br

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/8, Fa0/9, Fa0/10, Fa0/11
                                                Fa0/12, Fa0/13, Fa0/14, Fa0/15
                                                Fa0/16, Fa0/17, Fa0/18, Fa0/19
                                                Fa0/20, Fa0/21, Fa0/22, Fa0/23
                                                Fa0/24, Gig0/1, Gig0/2
10   VLAN0010                         active    Fa0/5
20   VLAN0020                         active    Fa0/6, Fa0/7
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active
```
### Проверка созданных Vlan на S2
```
Switch#sh vlan br

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/8, Fa0/9, Fa0/10, Fa0/11
                                                Fa0/12, Fa0/13, Fa0/14, Fa0/15
                                                Fa0/16, Fa0/17, Fa0/18, Fa0/19
                                                Fa0/20, Fa0/21, Fa0/22, Fa0/23
                                                Fa0/24, Gig0/1, Gig0/2
10   VLAN0010                         active    Fa0/5, Fa0/7
20   VLAN0020                         active    Fa0/6
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active
```
### Проверка созданных Vlan на S4
```
Switch#sh vlan br

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/6, Fa0/7, Fa0/8, Fa0/9
                                                Fa0/10, Fa0/11, Fa0/12, Fa0/13
                                                Fa0/14, Fa0/15, Fa0/16, Fa0/17
                                                Fa0/18, Fa0/19, Fa0/20, Fa0/21
                                                Fa0/22, Fa0/23, Fa0/24, Gig0/1
                                                Gig0/2
30   VLAN0030                         active    Fa0/1, Fa0/4
40   VLAN0040                         active    Fa0/2, Fa0/3
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active
```
Далее базовая настройка каждого маршрутизатора:
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
```
Настройка ip адресов на R1
```

R1(config)#int g0/0/1
R1(config)#ip address 215.36.25.1 255.255.255.0
R1(config-if)#no sh
R1(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up
R1(config-if)#int gi0/0/1.10
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.10, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.10, changed state to up
R1(config-subif)#encapsulation dot1Q 10
R1(config-subif)#ip address 192.168.10.1 255.255.255.0
R1(config-subif)#int gi0/0/1.20
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.20, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.20, changed state to up
R1(config-subif)#encapsulation dot1Q 20
R1(config-subif)#ip address 192.168.20.1 255.255.255.0
```
Настройка ip адресов на R2
```
R2(config)#int g0/0/0
R2(config)#ip address 215.36.25.2 255.255.255.0
R2(config)#int g0/0/1
R2(config)#ip address 138.36.78.1 255.255.255.0
```
Настройка ip адресов на R3
```
R3(config)#int g0/0/0
R3(config)#ip address 138.36.78.2 255.255.255.0
R3(config)#int g0/0/1
R3(config)#ip address 25.48.75.1 255.255.255.0
```
Настройка ip адресов на R4
```
R4(config)#int g0/0/0
R4(config)#ip address 25.48.75.2 255.255.255.0
R4(config)#int g0/0/1
R4(config)#ip address 149.65.32.1 255.255.255.0
```
Настройка ip адресов на R5
```
R5(config)#int g0/0/1
R5(config)#ip address 149.65.32.2 255.255.255.0
R5(config)#int g0/0/0
R5(config)#no sh
R5(config)#int gi0/0.30
R5(config)#encapsulation dot1Q 30
R5(config)#ip address 192.168.30.1 255.255.255.0
R5(config)#int gi0/0.40
R5(config)#encapsulation dot1Q 40
R5(config)#ip address 192.168.40.1 255.255.255.0
```
## DHCP
Настройка DHCP R5
```
R5(config)# ip dhcp excluded-address 192.168.30.1
R5(config)# ip dhcp pool V30
R5(dhcp-config)# network 192.168.30.0 255.255.255.0
R5(dhcp-config)# default-router 192.168.30.1
R5(config)# ip dhcp excluded-address 192.168.40.1
R5(config)# ip dhcp pool V40
R5(config)# network 192.168.40.0 255.255.255.0
R5(dhcp-config)# default-router 192.168.40.1
```
Настройка DHCP R1
```
R1(config)# ip dhcp excluded-address 192.168.10.1
R1(config)# ip dhcp pool V10
R1(dhcp-config)# network 192.168.10.0 255.255.255.0
R1(dhcp-config)# default-router 192.168.10.1
R1(config)# ip dhcp excluded-address 192.168.20.1
R1(config)# ip dhcp pool V20
R1(config)# network 192.168.20.0 255.255.255.0
R1(dhcp-config)# default-router 192.168.20.1
```
### Проверка созданных пулов
```
Router#sh ip dhcp pool

Pool V10 :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 3
 Excluded addresses             : 2
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 192.168.10.1         192.168.10.1     - 192.168.10.254    3    / 2     / 254

Pool V20 :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 3
 Excluded addresses             : 2
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 192.168.20.1         192.168.20.1     - 192.168.20.254    3    / 2     / 254

Router#sh ip dhcp pool

Pool V30 :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 2
 Excluded addresses             : 2
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 192.168.30.1         192.168.30.1     - 192.168.30.254    2    / 2     / 254

Pool V40 :
 Utilization mark (high/low)    : 100 / 0
 Subnet size (first/next)       : 0 / 0 
 Total addresses                : 254
 Leased addresses               : 2
 Excluded addresses             : 2
 Pending event                  : none

 1 subnet is currently in the pool
 Current index        IP address range                    Leased/Excluded/Total
 192.168.40.1         192.168.40.1     - 192.168.40.254    2    / 2     / 254
Router#
```
### Попытка получить IP-адрес от DHCP на PC 10
```
C:\>ipconfig /all

FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: 
   Physical Address................: 00D0.BABB.3E59
   Link-local IPv6 Address.........: FE80::2D0:BAFF:FEBB:3E59
   IPv6 Address....................: ::
   IPv4 Address....................: 192.168.30.2
   Subnet Mask.....................: 255.255.255.0
   Default Gateway.................: ::
                                     192.168.30.1
   DHCP Servers....................: 192.168.30.1
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-DA-51-07-41-00-D0-BA-BB-3E-59
   DNS Servers.....................: ::
                                     0.0.0.0

Bluetooth Connection:

   Connection-specific DNS Suffix..: 
   Physical Address................: 0000.0C22.5A10
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0
   DHCP Servers....................: 0.0.0.0
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-DA-51-07-41-00-D0-BA-BB-3E-59
   DNS Servers.....................: ::
                                     0.0.0.0
```
### Попытка получить IP-адрес от DHCP на PC 1
```
C:\>ipconfig /all

FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: 
   Physical Address................: 00E0.A324.8EE0
   Link-local IPv6 Address.........: FE80::2E0:A3FF:FE24:8EE0
   IPv6 Address....................: ::
   IPv4 Address....................: 192.168.20.2
   Subnet Mask.....................: 255.255.255.0
   Default Gateway.................: ::
                                     192.168.20.1
   DHCP Servers....................: 192.168.20.1
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-5D-93-AE-47-00-E0-A3-24-8E-E0
   DNS Servers.....................: ::
                                     0.0.0.0

Bluetooth Connection:

   Connection-specific DNS Suffix..: 
   Physical Address................: 0060.3E5E.7D22
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0
   DHCP Servers....................: 0.0.0.0
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-5D-93-AE-47-00-E0-A3-24-8E-E0
   DNS Servers.....................: ::
                                     0.0.0.0
```
![](https://github.com/jurgengg/OTUSLABS/blob/main/proekt/88.png)  
### Ping с PC 1 на PC 10
```
C:\>ping 192.168.30.2

Pinging 192.168.30.2 with 32 bytes of data:

Request timed out.
Reply from 192.168.30.2: bytes=32 time=17ms TTL=123
Reply from 192.168.30.2: bytes=32 time=11ms TTL=123
Reply from 192.168.30.2: bytes=32 time<1ms TTL=123

Ping statistics for 192.168.30.2:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 17ms, Average = 9ms
```
## Настройка OSPF
ip адреса на интрефейсах уже настроены ранее  
На всех маршрутизаторах настраиваем OSPF таким образом:
```
R1(config)#router ospf 1
R1(config-router)#router-id 215.36.25.1
R1(config-router)#int g0/0/1
R1(config-if)#ip ospf 1 area 0
```
Убедимся, что OSPFv2 работает между маршрутизаторами. Выполните команду, чтобы убедиться, что R1 и R2 сформировали смежность.
```
Router#sh ip ospf ne


Neighbor ID     Pri   State           Dead Time   Address         Interface
215.36.25.2       1   FULL/DR         00:00:36    215.36.25.2     GigabitEthernet0/1
```
## OSPF
### Конфигурация OSPF с каждого маррутизатора:
```
R1:
router ospf 1
 log-adjacency-changes
 network 215.36.25.0 0.0.0.255 area 0
 network 192.168.20.0 0.0.0.255 area 0
 network 192.168.10.0 0.0.0.255 area 0

R2:
router ospf 1
 log-adjacency-changes
 network 215.36.25.0 0.0.0.255 area 0
 network 138.36.78.0 0.0.0.255 area 0

R3:
router ospf 1
 log-adjacency-changes
 network 138.36.78.0 0.0.0.255 area 0
 network 25.48.75.0 0.0.0.255 area 0

R4:
router ospf 1
 log-adjacency-changes
 network 25.48.75.0 0.0.0.255 area 0
 network 149.65.32.0 0.0.0.255 area 0

R5:
router ospf 1
 log-adjacency-changes
 network 149.65.32.0 0.0.0.255 area 0
 network 192.168.30.0 0.0.0.255 area 0
 network 192.168.40.0 0.0.0.255 area 0

```
На R1 выполним команду show ip route ospf, чтобы убедиться, что сети присутствует в таблице маршрутизации
```
Router#sh ip rou ospf
     25.0.0.0/24 is subnetted, 1 subnets
O       25.48.75.0 [110/3] via 215.36.25.2, 00:53:03, GigabitEthernet0/1
     138.36.0.0/24 is subnetted, 1 subnets
O       138.36.78.0 [110/2] via 215.36.25.2, 00:53:03, GigabitEthernet0/1
     149.65.0.0/24 is subnetted, 1 subnets
O       149.65.32.0 [110/4] via 215.36.25.2, 00:53:03, GigabitEthernet0/1
O    192.168.30.0 [110/5] via 215.36.25.2, 00:53:03, GigabitEthernet0/1
O    192.168.40.0 [110/5] via 215.36.25.2, 00:53:03, GigabitEthernet0/1
```

⦁	Запустим Ping до адреса интерфейса R5  из R1. 
```
Router#ping 149.65.32.2

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 149.65.32.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/0 ms
```
## NAT
## Настройка NAT

```
R1(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R1(config)# ip nat pool Ner 215.36.25.3 215.36.25.15 netmask 255.255.255.0
R1(config)# ip nat inside source list 1 pool Ner
R1(config)# interface g0/0/0
R1(config-if)# ip nat inside
R1(config)# interface g0/0/1
R1(config-if)# ip nat outside
```
```
R1(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R1(config)# ip nat pool NatPool2 149.65.32.3 149.65.32.10 netmask 255.255.255.0
R1(config)# ip nat inside source list 1 pool NatPool2
R1(config)# interface g0/0/0
R1(config-if)# ip nat inside
R1(config)# interface g0/0/1
R1(config-if)# ip nat outside
```
## Конфигурация безопасности коммутатора
Защитим порты коммутатора в сторону конечных устройств от сетевых атак
Настройки проведем для S4 на все порты в стороны ПК  
```
S4(config)#int fa0/4
S4(config-if)#switchport port-security 
S4(config-if)#switchport port-security mac-address sticky 
S4(config-if)#switchport port-security maximum 2
S4(config-if)#switchport port-security violation protect 
S4(config-if)#switchport port-security aging time 60
```
проверяем:  
```
S2#sh port-security int fa0/4
Port Security              : Enabled
Port Status                : Secure-up
Violation Mode             : Protect
Aging Time                 : 60 mins
Aging Type                 : Absolute
SecureStatic Address Aging : Disabled
Maximum MAC Addresses      : 2
Total MAC Addresses        : 1
Configured MAC Addresses   : 0
Sticky MAC Addresses       : 1
Last Source Address:Vlan   : 00D0.FFDE.77D7:10
Security Violation Count   : 0

S2#sh port-security address 
               Secure Mac Address Table
-----------------------------------------------------------------------------
Vlan    Mac Address       Type                          Ports   Remaining Age
                                                                   (mins)
----    -----------       ----                          -----   -------------
  10    00D0.FFDE.77D7    SecureSticky                  Fa0/4       -
-----------------------------------------------------------------------------
Total Addresses in System (excluding one mac per port)     : 0
Max Addresses limit in System (excluding one mac per port) : 1024
```


### Выводы и планы по развитию: Поставленные цели и задачи выполнены, технологии реализованы, локальная сеть работает в полнном объеме.  
В дальнейшем планируется организовать сеть провайдера с помощью технологии MPLS, В каждой офисе компании реализовать 3-х уровневую сетевую архитектуру, Развернуть VOIP SIP сервер в офисах компании.

## P.S.
Конфигурации всех устройств  
S1:
```
Current configuration : 1407 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
spanning-tree mode rapid-pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/2
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/3
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/4
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/5
 switchport access vlan 10
!
interface FastEthernet0/6
 switchport access vlan 20
!
interface FastEthernet0/7
 switchport access vlan 20
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
!
!
!
line con 0
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end
```
S2:  
```
Switch#sh run
Building configuration...

Current configuration : 1523 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
spanning-tree mode rapid-pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/2
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/3
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/4
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/5
 switchport access vlan 10
!
interface FastEthernet0/6
 switchport access vlan 20
!
interface FastEthernet0/7
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
!
!
!
line con 0
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end
```
S3:  
```
Switch#sh run
Building configuration...

Current configuration : 1349 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
spanning-tree mode rapid-pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/2
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/3
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/4
 switchport trunk allowed vlan 10,20
 switchport mode trunk
!
interface FastEthernet0/5
 switchport mode trunk
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
!
!
!
line con 0
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end
```
S4:  
```
Switch#sh run
Building configuration...

Current configuration : 1579 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
 switchport access vlan 30
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface FastEthernet0/2
 switchport access vlan 40
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface FastEthernet0/3
 switchport access vlan 40
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface FastEthernet0/4
 switchport access vlan 30
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface FastEthernet0/5
 switchport mode trunk
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
!
!
!
line con 0
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end
```
R1:
```
Router#sh run
Building configuration...

Current configuration : 1456 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
ip dhcp excluded-address 192.168.10.1
ip dhcp excluded-address 192.168.20.1
!
ip dhcp pool V10
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
ip dhcp pool V20
 network 192.168.20.0 255.255.255.0
 default-router 192.168.20.1
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX1524K6NR-
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 no ip address
 duplex auto
 speed auto
!
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1
 ip address 215.36.25.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 log-adjacency-changes
 network 215.36.25.0 0.0.0.255 area 0
 network 192.168.20.0 0.0.0.255 area 0
 network 192.168.10.0 0.0.0.255 area 0
!
ip nat pool Ner 215.36.25.3 215.36.25.15 netmask 255.255.255.0
ip nat inside source list 1 pool Ner
ip classless
!
ip flow-export version 9
!
!
access-list 1 permit 192.168.0.0 0.0.255.255
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end
```
R2:  
```
Router#sh run
Building configuration...

Current configuration : 830 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX1524C222-
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 ip address 215.36.25.2 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 138.36.78.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 log-adjacency-changes
 network 215.36.25.0 0.0.0.255 area 0
 network 138.36.78.0 0.0.0.255 area 0
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end
```
R3:  
```
Router#sh run
Building configuration...

Current configuration : 828 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX1524F02E-
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 ip address 138.36.78.2 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 25.48.75.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 log-adjacency-changes
 network 138.36.78.0 0.0.0.255 area 0
 network 25.48.75.0 0.0.0.255 area 0
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end
```
R4:  
```
Router#sh run
Building configuration...

Current configuration : 828 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX152418N5-
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 ip address 25.48.75.2 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 149.65.32.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 log-adjacency-changes
 network 25.48.75.0 0.0.0.255 area 0
 network 149.65.32.0 0.0.0.255 area 0
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end
```
R5:  
```
Router#sh run
Building configuration...

Current configuration : 1467 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
ip dhcp excluded-address 192.168.30.1
ip dhcp excluded-address 192.168.40.1
!
ip dhcp pool V30
 network 192.168.30.0 255.255.255.0
 default-router 192.168.30.1
ip dhcp pool V40
 network 192.168.40.0 255.255.255.0
 default-router 192.168.40.1
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX1524HXQF-
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 no ip address
 duplex auto
 speed auto
!
interface GigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/0.40
 encapsulation dot1Q 40
 ip address 192.168.40.1 255.255.255.0
 ip nat outside
!
interface GigabitEthernet0/1
 ip address 149.65.32.2 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 log-adjacency-changes
 network 149.65.32.0 0.0.0.255 area 0
 network 192.168.30.0 0.0.0.255 area 0
 network 192.168.40.0 0.0.0.255 area 0
!
ip nat pool NatPool2 149.65.32.3 149.65.32.10 netmask 255.255.255.0
ip nat inside source list 1 pool NatPool2
ip classless
!
ip flow-export version 9
!
!
access-list 1 permit 192.168.0.0 0.0.255.255
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end
```

