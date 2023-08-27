### Курс Network engineer. Basic
### Тема проекта: Проектирование сети организации с использованием технологий динамической маршрутизации, резервированием и безопасности 
### Автор: Башаев Юрий

Цели проекта:  
В качестве цели проекта была выбрано создать с нуля сеть небольшой организации "Карта мира", которая имеет несколько удаленных друг от друга филиалов.  
Задачами к проектированию сети ставилось обеспечить: Создание VLAN`ов для каждого отдела организации, Обеспечение защиты от сетевых атак, Настройка динамической маршрутизации, Настройка динамической выдачи IP адресов  
Для реализации были выбраны следующие технологии:  OSPF, Spanning Tree Protocol, NAT, VLAN, Port Security,DHCP  
## Разработанная схема локальной сети организации:  

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

### Выводы и планы по развитию: В дальнейшем планируется организовать сеть провайдера с помощью технологии MPLS, В каждой офисе компании реализовать 3-х уровневую сетевую архитектуру, Развернуть VOIP SIP сервер в офисах компании.






