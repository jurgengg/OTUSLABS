# Configure_CDP__LLDP__and_NTP
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab13/677667.png)    
## Настройте базовые параметры для маршрутизатора
```
router(config)# hostname R1
R1(config)# no ip domain lookup
R1(config)# enable secret class
R1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# line vty 0 4
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# service password-encryption
R1(config)# banner motd $ Authorized Users Only! $
R1(config-if)# interface g0/0/1
R1(config-if)# ip address 10.22.0.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# end
R1# copy running-config startup-config
```
## Настройте базовые параметры каждого коммутатора
```
switch(config)# hostname S1
S1(config)# no ip domain-lookup
S1(config)# enable secret class
S1(config)# line console 0
S1(config-line)# password cisco
S1(config-line)# login
S1(config)# line vty 0 15
S1(config-line)# password cisco
S1(config-line)# login
S1(config)# service password-encryption
S1(config)# banner motd $ Authorized Users Only! $
S1(config)# interface range f0/2-4, f0/6-24, g0/1-2
S1(config-if-range)# shutdown
S1(config-if-range)# end
S1# copy running-config startup-config
```
```
switch(config)# hostname S2
S2(config)# no ip domain-lookup
S2(config)# enable secret class
S2(config)# line console 0
S2(config-line)# password cisco
S2(config-line)# login
S2(config)# line vty 0 15
S2(config-line)# password cisco
S2(config-line)# login
S2(config)# service password-encryption
S2(config)# banner motd $ Authorized Users Only! $
S2(config)# interface range f0/2-24, g0/1-2
S2(config-if-range)# shutdown
S2(config-if-range)# end
S2# copy running-config startup-config
```
## Обнаружение сетевых ресурсов с помощью протокола CDP
```
R1# show cdp interface | include interfaces
 cdp enabled interfaces : 5
 interfaces up          : 4
 interfaces down        : 1
```

Сколько интерфейсов участвует в объявлениях CDP? Какие из них активны? В исходящих данных выше пять интерфейсов участвуют в CDP. Четыре вверху, один внизу.
### ⦁	На R1 используйте соответствующую команду show cdp, чтобы определить версию IOS, используемую на S1.
```
R1# show cdp entry S1
-------------------------
Device ID: S1
Entry address(es):
Platform: cisco WS-C2960+24LC-L, Capabilities: Switch IGMP
Interface: GigabitEthernet0/0/1, Port ID (outgoing port): FastEthernet0/5
Holdtime : 125 sec

Version :
Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.2(4)E8, RELEASE SOFTWARE (fc3)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2019 by Cisco Systems, Inc.
Compiled Fri 15-Mar-19 17:28 by prod_rel_team

advertisement version: 2
VTP Management Domain: ''
Native VLAN: 1
Duplex: full
```
 ⦁	Какая версия IOS используется на  S1? IOS Version 15.2(4)E8
## ⦁	На S1 используйте соответствующую команду show cdp, чтобы определить, сколько пакетов CDP было выданных.
```
S1# show cdp traffic
CDP counters :
        Total packets output: 179, Input: 148
        Hdr syntax: 0, Chksum error: 0, Encaps failed: 0
        No memory: 0, Invalid packet: 0,
        CDP version 1 advertisements output: 0, Input: 0
        CDP version 2 advertisements output: 179, Input: 148
```
⦁	Сколько пакетов имеет выход CDP с момента последнего сброса счетчика? 179 packets
### ⦁	Настройте SVI для VLAN 1 на S1 и S2, используя IP-адреса, указанные в таблице адресации выше. Настройте шлюз по умолчанию для каждого коммутатора на основе таблицы адресов.
```
S1(config)# interface vlan 1
S1(config-if)# ip address 10.22.0.2 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# exit
S1(config)# ip default-gateway 10.22.0.1

S2(config)# interface vlan 1
S2(config-if)# ip address 10.22.0.3 255.255.255.0
S2(config-if)# no shutdown
S2(config-if)# exit
S2(config)# ip default-gateway 10.22.0.1
```
### ⦁	На R1 выполните команду show cdp entry S1 . 
```
R1# show cdp entry S1
-------------------------
Device ID: S1
Entry address(es):
  IP address: 10.22.0.2
Platform: cisco WS-C2960+24LC-L,  Capabilities: Switch IGMP
Interface: GigabitEthernet0/0/1,  Port ID (outgoing port): FastEthernet0/5
Holdtime : 133 sec

Version :
Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.2(4)E8, RELEASE SOFTWARE (fc3)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2019 by Cisco Systems, Inc.
Compiled Fri 15-Mar-19 17:28 by prod_rel_team

advertisement version: 2
VTP Management Domain: ''
Native VLAN: 1
Duplex: full
Management address(es):
  IP address: 10.22.0.2
```
Какие дополнительные сведения доступны теперь? Выходные данные включают IP-адрес управления для VLAN 1 SVI на S1, который был только что настроен.
### ⦁	Отключить CDP глобально на всех устройствах. 

```
R1(config)# no cdp run
S1(config)# no cdp run
S2(config)# no cdp run
```

## Обнаружение сетевых ресурсов с помощью протокола LLDP
### ⦁	Введите соответствующую команду lldp, чтобы включить LLDP на всех устройствах в топологии.
```
R1(config)# lldp run
S1(config)# lldp run
S2(config)# lldp run
```
### ⦁	На S1 выполните соответствующую команду lldp, чтобы предоставить подробную информацию о S2. 
```
S1# show lldp entry S2

Capability codes:
    (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
    (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
------------------------------------------------
Local Intf: Fa0/1
Chassis id: c025.5cd7.ef00
Port id: Fa0/1
Port Description: FastEthernet0/1
System Name: S2

System Description:
Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.2(4)E8, RELEASE SOFTWARE (fc3)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2019 by Cisco Systems, Inc.
Compiled Fri 15-Mar-19 17:28 by prod_rel_team

Time remaining: 109 seconds
System Capabilities: B
Enabled Capabilities: B
Management Addresses:
    IP: 10.22.0.3
Auto Negotiation - supported, enabled
Physical media capabilities:
    100base-TX(FD)
    100base-TX(HD)
    10base-T(FD)
    10base-T(HD)
Media Attachment Unit type: 16
Vlan ID: 1

Total entries displayed: 1
```

Что такое chassis ID  для коммутатора S2? — c025.5cd7.ef00.
⦁	Соединитесь через консоль на всех устройствах и используйте команды LLDP, необходимые для отображения топологии физической сети только из выходных данных команды show - show lldp Neighbor.

## Настройка NTP
### Установите время.
```
R1# clock set 18:30:00 20 August 2023
```
### 	Настройте главный сервер NTP.
```
R1(config)# ntp master 4
```
### ⦁	Настройте S1 и S2 в качестве клиентов NTP. Используйте соответствующие команды NTP для получения времени от интерфейса G0/0/1 R1, а также для периодического обновления календаря или аппаратных часов коммутатора.
```
S1(config)# ntp server 10.22.0.1
S1(config)# ntp update-calendar

S2(config)# ntp server 10.22.0.1
S2(config)# ntp update-calendar
```
## Проверьте настройку NTP
```
S1# show ntp status | include Clock

Clock is synchronized, stratum 5, reference is 10.22.0.1

S2# show ntp associations

  address         ref clock       st   when   poll reach  delay  offset   disp
*~10.22.0.1       127.127.1.1      4      4     64     3  3.194   4.629 63.914
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

Для каких интерфейсов в пределах сети не следует использовать протоколы обнаружения сетевых ресурсов? Протоколы обнаружения не следует использовать на интерфейсах, обращенных к внешним сетям, поскольку эти протоколы предоставляют информацию о внутренней сети. Эта информация позволяет злоумышленникам получить ценную информацию о внутренней сети и может быть использована для взлома сети.

