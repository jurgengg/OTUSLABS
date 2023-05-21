# Lab___Switch_Security_Configuration-1801-49aa15
![](https://github.com/jurgengg/OTUSLABS/blob/main/LAB9/Screenshot_5.png)    
⦁	Настройка основного сетевого устройства  
⦁	Создайте сеть.  
⦁	Создайте сеть согласно топологии.  
⦁	Инициализация устройств  
![](https://github.com/jurgengg/OTUSLABS/blob/main/LAB9/Screenshot_6.png)   

###	Настройте маршрутизатор R1.  
```
Router>en
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#enable secte
Router(config)#enable sec
Router(config)#enable secret class
Router(config)#host r!
r!(config)#host R1
R1(config)#no ip d
R1(config)#no ip do
R1(config)#no ip doma
R1(config)#no ip domain loo
R1(config)#no ip domain lookup 
R1(config)#ip dhc
R1(config)#ip dhcp ex
R1(config)#ip dhcp excluded-address 192.168.10.1 192.168.10.9
R1(config)#ip dhcp excluded-address 192.168.10.201 192.168.10.202
R1(config)#ip hh
R1(config)#ip d
R1(config)#ip dhc
R1(config)#ip dhcp po
R1(config)#ip dhcp pool  Students
R1(dhcp-config)#ne
R1(dhcp-config)#network 192.168.10.0 255.255.255.0
R1(dhcp-config)#domain
R1(dhcp-config)#domain-name CCNA2.Lab-11.6.1
R1(dhcp-config)#exi
R1(config)#ip de
R1(config)#ip defa
R1(config)#ip defa
R1(config)#ip defau
R1(config)#ip defaul
R1(config)#ip default-g
R1(config)#
R1#
%SYS-5-CONFIG_I: Configured from console by console

R1#\
Translating "\"
% Unknown command or computer name, or unable to find computer address

R1#
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#ip d
R1(config)#ip dhcp po
R1(config)#ip dhcp pool S
R1(config)#ip dhcp pool Students
R1(dhcp-config)#de
R1(dhcp-config)#default-router 192.168.10.1
R1(dhcp-config)#
R1#
%SYS-5-CONFIG_I: Configured from console by console
\
Translating "\"
% Unknown command or computer name, or unable to find computer address

R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#int
R1(config)#interface loo
R1(config)#interface loopback0

R1(config-if)#
%LINK-5-CHANGED: Interface Loopback0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback0, changed state to up

R1(config-if)#ip ad
R1(config-if)#ip address 10.10.1.1 255.255.255.0
R1(config-if)#int g0/0/1
R1(config-if)#de
R1(config-if)#desc
R1(config-if)#description Link to S1
R1(config-if)#ip dh
R1(config-if)#ip dhc
R1(config-if)#ip dhcp
R1(config-if)#ip dhcp re
R1(config-if)#ip dhcp relay
R1(config-if)#ip dhcp relay i
R1(config-if)#ip dhcp relay info
R1(config-if)#ip dhcp relay information trusted
                 ^
% Invalid input detected at '^' marker.
	
R1(config-if)#ip add
R1(config-if)#ip address 192.168.10.1 255.255.255.0
R1(config-if)#no shu

R1(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up
exit
R1(config)#ip dhcp
R1(config)#ip dhcp  re
R1(config)#ip dhcp  relay in
R1(config)#ip dhcp  relay information tru
R1(config)#ip dhcp  relay information trust-all 
R1(config)#line con 0
R1(config-line)#logg
R1(config-line)#logging sy
R1(config-line)#logging synchronous 
R1(config-line)#exe
R1(config-line)#exec-timeout 0 0
```  
 
### Проверьте текущую конфигурацию на R1, используя следующую команду:  
R1# show ip interface brief  
```
R1#show ip interface br
Interface              IP-Address      OK? Method Status                Protocol 
GigabitEthernet0/0/0   unassigned      YES unset  administratively down down 
GigabitEthernet0/0/1   192.168.10.1    YES manual up                    up 
Loopback0              10.10.1.1       YES manual up                    up 
Vlan1                  unassigned      YES unset  administratively down down
R1#
```  

⦁	Настройка и проверка основных параметров коммутатора  
⦁	Настройте имя хоста для коммутаторов S1 и S2.  
Откройте окно конфигурации  
⦁	Запретите нежелательный поиск в DNS.  
⦁	Настройте описания интерфейса для портов, которые используются в S1 и S2.  
⦁	Установите для шлюза по умолчанию для VLAN управления значение 192.168.10.1 на обоих коммутаторах.  
```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#ena
Switch(config)#enable se
Switch(config)#enable secret class
Switch(config)#
Switch(config)#host S1
S1(config)#no ip
S1(config)#no ip d
S1(config)#no ip do
S1(config)#no ip dom
S1(config)#no ip domain lo
S1(config)#no ip domain lookup 
S1(config)#ip de
S1(config)#ip default-gateway 192.168.10.1
S1(config-if)#int fa0/1
S1(config-if)#desc
S1(config-if)#description Link to S2
S1(config)#int fa0/5
S1(config-if)#de
S1(config-if)#description link to R1
S1(config-if)#int fa0/6
S1(config-if)#desc
S1(config-if)#description link to pc
S1(config-if)#
```  
```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#eba
Switch(config)#ena
Switch(config)#enable sec
Switch(config)#enable secret class
Switch(config)#host S2
S2(config)#no ip domain lo
S2(config)#no ip domain lookup 
S2(config)#ip de
S2(config)#ip default-gateway 192.168.10.1
S2(config)#int fa0/18
S2(config-if)#desc
S2(config-if)#description Link to PC
S2(config-if)#int fa0/1
S2(config-if)#desc
S2(config-if)#description Link to S1
S2(config-if)#
```  


### Добавьте VLAN 10 на S1 и S2 и назовите VLAN - Management.  
```
S1(config-if)#vlan 10
S1(config-vlan)#name Management

S2(config-if)#vlan 10
S2(config-vlan)#name Management
```  

### Сконфигруриуйте SVI для VLAN 10.  
Настройте IP-адрес в соответствии с таблицей адресации для SVI для VLAN 10 на S1 и S2. Включите интерфейсы SVI и предоставьте описание для интерфейса  
```
S1(config)#int vlan 10
S1(config-if)#
%LINK-5-CHANGED: Interface Vlan10, changed state to up

S1(config-if)#ip adf
S1(config-if)#ip ad
S1(config-if)#ip address 192.168.10.201 255.255.255.0
S1(config-if)#no shu
S1(config-if)#des
S1(config-if)#description Management

S2(config-vlan)#int vlan 10
S2(config-if)#
%LINK-5-CHANGED: Interface Vlan10, changed state to up

S2(config-if)#
S2(config-if)#
S2(config-if)#ip ad
S2(config-if)#ip address 192.168.10.202 255.255.255.0
S2(config-if)#desc
S2(config-if)#description Management
```  
### Настройте VLAN 333 с именем Native на S1 и S2.  
### Настройте VLAN 999 с именем ParkingLot на S1 и S2.  
```
S1(config-vlan)#int fa0/1
S1(config-if)#swi
S1(config-if)#switchport mode tr
S1(config-if)#switchport mode trunk 

S1(config-if)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan10, changed state to up
swi
S1(config-if)#switchport tr
S1(config-if)#switchport trunk na
S1(config-if)#switchport trunk native vlan 333
```  


## Настройки безопасности коммутатора.  
### Релизация магистральных соединений 802.1Q.  
### Настройте все магистральные порты Fa0/1 на обоих коммутаторах для использования VLAN 333 в качестве native VLAN.  
```
S1(config-if)#vlan 333
S1(config-vlan)#name Native
S1(config-vlan)#vlan 999
S1(config-vlan)#name ParkingLot

S2(config-vlan)#int fa0/1
S2(config-if)#swi
S2(config-if)#switchport mo
S2(config-if)#switchport mode tr
S2(config-if)#switchport mode trunk 
S2(config-if)#swi
S2(config-if)#switchport tru
S2(config-if)#switchport trunk na
S2(config-if)#switchport trunk native vlan 333
S2(config-if)#no s%SPANTREE-2-UNBLOCK_CONSIST_PORT: Unblocking FastEthernet0/1 on VLAN0333. Port consistency restored.

%SPANTREE-2-UNBLOCK_CONSIST_PORT: Unblocking FastEthernet0/1 on VLAN0001. Port consistency restored.

% Incomplete command.
S2(config-if)#no shu
```  
### Убедитесь, что режим транкинга успешно настроен на всех коммутаторах.  
S1# show interface trunk  
```
S2#sh interfaces tr
S2#sh interfaces trunk 
Port        Mode         Encapsulation  Status        Native vlan
Fa0/1       on           802.1q         trunking      333

Port        Vlans allowed on trunk
Fa0/1       1-1005

Port        Vlans allowed and active in management domain
Fa0/1       1,10,333,999

Port        Vlans in spanning tree forwarding state and not pruned
Fa0/1       1,10,333,999


S1#sh int tr
Port        Mode         Encapsulation  Status        Native vlan
Fa0/1       on           802.1q         trunking      333

Port        Vlans allowed on trunk
Fa0/1       1-1005

Port        Vlans allowed and active in management domain
Fa0/1       1,10,333,999

Port        Vlans in spanning tree forwarding state and not pruned
Fa0/1       1,10,333,999
```  



### Отключить согласование DTP F0/1 на S1 и S2.   
```
S1(config)#int fa0/1
S1(config-if)#swi
S1(config-if)#switchport n
S1(config-if)#switchport nonegotiate

S2(config)#int fa0/1
S2(config-if)#swi
S2(config-if)#switchport non
S2(config-if)#switchport nonegotiate
```  
### Проверьте с помощью команды show interfaces.  
```
S1#sh interfaces fa0/1 sw
S1#sh interfaces fa0/1 switchport 
Name: Fa0/1
Switchport: Enabled
Administrative Mode: trunk
Operational Mode: trunk
Administrative Trunking Encapsulation: dot1q
Operational Trunking Encapsulation: dot1q
Negotiation of Trunking: Off

S2#sh int f0/1 sw
S2#sh int f0/1 switchport 
Name: Fa0/1
Switchport: Enabled
Administrative Mode: trunk
Operational Mode: trunk
Administrative Trunking Encapsulation: dot1q
Operational Trunking Encapsulation: dot1q
Negotiation of Trunking: Off
```  


### Настройка портов доступа  
### На S1 настройте F0/5 и F0/6 в качестве портов доступа и свяжите их с VLAN 10.  
```
S1(config)#int range fa0/5-6
S1(config-if-range)#swi
S1(config-if-range)#switchport mode
S1(config-if-range)#switchport mode ac
S1(config-if-range)#switchport mode access 
S1(config-if-range)#swi
S1(config-if-range)#switchport ac
S1(config-if-range)#switchport access v
S1(config-if-range)#switchport access vlan 10
S1(config-if-range)#
```  
### На S2 настройте порт доступа Fa0/18 и свяжите его с VLAN 10.  
```
S2(config)#int fa0/18
S2(config-if)#sw
S2(config-if)#switchport mo
S2(config-if)#switchport mode acc
S2(config-if)#switchport mode access 
S2(config-if)#sw
S2(config-if)#switchport ac
S2(config-if)#switchport access vlan 10
```  



### Безопасность неиспользуемых портов коммутатора  
### На S1 и S2 переместите неиспользуемые порты из VLAN 1 в VLAN 999 и отключите неиспользуемые порты.  
```
S1(config)#int range fa0/2-4, fa0/7-24
S1(config-if-range)#swi
S1(config-if-range)#switchport mod
S1(config-if-range)#switchport mode ac
S1(config-if-range)#switchport mode access 
S1(config-if-range)#swi
S1(config-if-range)#switchport ac
S1(config-if-range)#switchport access vlan 999
S1(config-if-range)#shu

%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/3, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/4, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/7, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/8, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/9, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/10, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/11, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/12, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/13, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/14, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/15, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/16, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/17, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/18, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/19, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/20, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/21, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/22, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/23, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/24, changed state to administratively down
S1(config)#int ran
S1(config)#int range gi0/1-2
S1(config-if-range)#swi
S1(config-if-range)#switchport mode
S1(config-if-range)#switchport mode acc
S1(config-if-range)#switchport mode access 
S1(config-if-range)#sw
S1(config-if-range)#switchport ac
S1(config-if-range)#switchport access vlan 999
S1(config-if-range)#shu

S2(config)#int range f0/2-17,fa0/19-24
S2(config-if-range)#swi
S2(config-if-range)#switchport mode
S2(config-if-range)#switchport mode acc
S2(config-if-range)#switchport mode access 
S2(config-if-range)#sw
S2(config-if-range)#switchport ac
S2(config-if-range)#switchport access vlan 999
S2(config-if-range)#shu

%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/3, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/4, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/5, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/6, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/7, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/8, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/9, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/10, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/11, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/12, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/13, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/14, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/15, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/16, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/17, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/19, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/20, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/21, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/22, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/23, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/24, changed state to administratively down

S2(config)#int range gi0/1-2
S2(config-if-range)#swi
S2(config-if-range)#switchport mode
S2(config-if-range)#switchport mode ac
S2(config-if-range)#switchport mode access 
S2(config-if-range)#sw
S2(config-if-range)#switchport ac
S2(config-if-range)#switchport access vlan999
                                          ^
% Invalid input detected at '^' marker.
	
S2(config-if-range)#switchport access vlan 999
S2(config-if-range)#shu

%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to administratively down

%LINK-5-CHANGED: Interface GigabitEthernet0/2, changed state to administratively down
```  
### Убедитесь, что неиспользуемые порты отключены и связаны с VLAN 999, введя команду  show.  
S1# show interfaces status  
```
S2#sh int status 
Port      Name               Status       Vlan       Duplex  Speed Type
Fa0/1     Link to S1         connected    trunk      auto    auto  10/100BaseTX
Fa0/2                        disabled 999        auto    auto  10/100BaseTX
Fa0/3                        disabled 999        auto    auto  10/100BaseTX
Fa0/4                        disabled 999        auto    auto  10/100BaseTX
Fa0/5                        disabled 999        auto    auto  10/100BaseTX
Fa0/6                        disabled 999        auto    auto  10/100BaseTX
Fa0/7                        disabled 999        auto    auto  10/100BaseTX
Fa0/8                        disabled 999        auto    auto  10/100BaseTX
Fa0/9                        disabled 999        auto    auto  10/100BaseTX
Fa0/10                       disabled 999        auto    auto  10/100BaseTX
Fa0/11                       disabled 999        auto    auto  10/100BaseTX
Fa0/12                       disabled 999        auto    auto  10/100BaseTX
Fa0/13                       disabled 999        auto    auto  10/100BaseTX
Fa0/14                       disabled 999        auto    auto  10/100BaseTX
Fa0/15                       disabled 999        auto    auto  10/100BaseTX
Fa0/16                       disabled 999        auto    auto  10/100BaseTX
Fa0/17                       disabled 999        auto    auto  10/100BaseTX
Fa0/18    Link to PC         connected    10         auto    auto  10/100BaseTX
Fa0/19                       disabled 999        auto    auto  10/100BaseTX
Fa0/20                       disabled 999        auto    auto  10/100BaseTX
Fa0/21                       disabled 999        auto    auto  10/100BaseTX

S1#sh int status 
Port      Name               Status       Vlan       Duplex  Speed Type
Fa0/1                        connected    trunk      auto    auto  10/100BaseTX
Fa0/2                        disabled 999        auto    auto  10/100BaseTX
Fa0/3                        disabled 999        auto    auto  10/100BaseTX
Fa0/4                        disabled 999        auto    auto  10/100BaseTX
Fa0/5     link to R1         connected    10         auto    auto  10/100BaseTX
Fa0/6     link to pc         connected    10         auto    auto  10/100BaseTX
Fa0/7                        disabled 999        auto    auto  10/100BaseTX
Fa0/8                        disabled 999        auto    auto  10/100BaseTX
Fa0/9                        disabled 999        auto    auto  10/100BaseTX
Fa0/10                       disabled 999        auto    auto  10/100BaseTX
Fa0/11                       disabled 999        auto    auto  10/100BaseTX
Fa0/12                       disabled 999        auto    auto  10/100BaseTX
Fa0/13                       disabled 999        auto    auto  10/100BaseTX
Fa0/14                       disabled 999        auto    auto  10/100BaseTX
Fa0/15                       disabled 999        auto    auto  10/100BaseTX
Fa0/16                       disabled 999        auto    auto  10/100BaseTX
Fa0/17                       disabled 999        auto    auto  10/100BaseTX
Fa0/18                       disabled 999        auto    auto  10/100BaseTX
Fa0/19                       disabled 999        auto    auto  10/100BaseTX
Fa0/20                       disabled 999        auto    auto  10/100BaseTX
Fa0/21                       disabled 999        auto    auto  10/100BaseTX
```  

### Документирование и реализация функций безопасности порта.  
Интерфейсы F0/6 на S1 и F0/18 на S2 настроены как порты доступа. На этом шаге вы также настроите безопасность портов на этих двух портах доступа.  
### На S1, введите команду show port-security interface f0/6  для отображения настроек по умолчанию безопасности порта для интерфейса F0/6. Запишите свои ответы ниже.  


![](https://github.com/jurgengg/OTUSLABS/blob/main/LAB9/lab9.png)  



⦁	На S1 включите защиту порта на F0 / 6 со следующими настройками:  
⦁	Максимальное количество записей MAC-адресов: 3  
⦁	Режим безопасности: restrict  
⦁	Aging time: 60 мин.  
⦁	Aging type: неактивный  
⦁	Verify port security on S1 F0/6.  
S1# show port-security interface f0/6  
```
S1(config)#int fa0/6
S1(config-if)#sw
S1(config-if)#switchport po
S1(config-if)#switchport port-security ma
S1(config-if)#switchport port-security max
S1(config-if)#switchport port-security maximum 3
S1(config-if)#sw
S1(config-if)#switchport po
S1(config-if)#switchport port-security vi
S1(config-if)#switchport port-security violation restrict
S1(config-if)#switchport port-security ag
S1(config-if)#switchport port-security aging time 60
S1(config-if)#switchport port-security aging ty
S1(config-if)#switchport port-security aging typ
S1(config-if)#switchport port-security aging type
S1(config-if)#switchport port-security ty
S1(config-if)#switchport port-security typ
S1(config-if)#switchport port-security ag
S1(config-if)#switchport port-security aging type
                                              ^
% Invalid input detected at '^' marker.
	
S1(config-if)#switchport port-security aging ?
  time  Port-security aging time
S1(config-if)#switchport port-security ?
  aging        Port-security aging commands
  mac-address  Secure mac address
  maximum      Max secure addresses
  violation    Security violation mode
  <cr>
S1(config-if)#switchport port-security ma
S1(config-if)#switchport port-security mac
S1(config-if)#switchport port-security mac-address ?
  H.H.H   48 bit mac address
  sticky  Configure dynamic secure addresses as sticky
S1(config-if)#switchport port-security aging ti
S1(config-if)#switchport port-security aging ti
S1(config-if)#switchport port-security aging t
S1(config-if)#switchport port-security aging ?
  time  Port-security aging time
S1(config-if)#switchport port-security aging type
                                              ^
% Invalid input detected at '^' marker.
	
S1(config-if)#switchport port-security aging ?
  time  Port-security aging time
S1(config-if)#switchport port-security aging a
S1(config-if)#switchport port-security aging ag
S1(config-if)#switchport port-security aging agi
S1(config-if)#switchport port-security aging po
S1(config-if)#switchport port-security aging por
S1(config-if)#switchport port-security in
S1(config-if)#switchport port-security ?
  aging        Port-security aging commands
  mac-address  Secure mac address
  maximum      Max secure addresses
  violation    Security violation mode
  <cr>
S1(config-if)#switchport port-security agi
S1(config-if)#switchport port-security aging in
S1(config-if)#switchport port-security aging inactivity
                                             ^
% Invalid input detected at '^' marker.
	
S1(config-if)#switchport port-security aging type inactivity
                                              ^
% Invalid input detected at '^' marker.

*Не удалось настроить type inactivity

S1(config)#int fa0/6
S1(config-if)#swi
S1(config-if)#switchport po
S1(config-if)#switchport port-security 
```
```
S1#show port-security int fa0/6
Port Security              : Enabled
Port Status                : Secure-up
Violation Mode             : Restrict
Aging Time                 : 60 mins
Aging Type                 : Absolute
SecureStatic Address Aging : Disabled
Maximum MAC Addresses      : 3
Total MAC Addresses        : 1
Configured MAC Addresses   : 0
Sticky MAC Addresses       : 0
Last Source Address:Vlan   : 00E0.B046.91B7:10
Security Violation Count   : 0
```  

### Включите безопасность порта для F0 / 18 на S2. Настройте каждый активный порт доступа таким образом, чтобы он автоматически добавлял адреса МАС, изученные на этом порту, в текущую конфигурацию.  

⦁	Настройте следующие параметры безопасности порта на S2 F / 18:  
⦁	Максимальное количество записей MAC-адресов: 2  
⦁	Тип безопасности: Protect  
⦁	Aging time: 60 мин.  
⦁	Проверка функции безопасности портов на S2 F0/18.  
```
S2(config)#int fa0/18
S2(config-if)#sw
S2(config-if)#switchport po
S2(config-if)#switchport port-security 
S2(config-if)#sw
S2(config-if)#switchport po
S2(config-if)#switchport port-security ma
S2(config-if)#switchport port-security mac
S2(config-if)#switchport port-security mac-address st
S2(config-if)#switchport port-security mac-address sticky 
S2(config-if)#switchport port-security ma
S2(config-if)#switchport port-security max
S2(config-if)#switchport port-security maximum 2
S2(config-if)#switchport port-security v
S2(config-if)#switchport port-security violation p
S2(config-if)#switchport port-security violation protect 
S2(config-if)#switchport port-security ag
S2(config-if)#switchport port-security aging time 60
```  
S2# show port-security interface f0/18  
```
S2#sh port-security int fa0/18
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
  10    00D0.FFDE.77D7    SecureSticky                  Fa0/18       -
-----------------------------------------------------------------------------
Total Addresses in System (excluding one mac per port)     : 0
Max Addresses limit in System (excluding one mac per port) : 1024
```  


### Реализовать безопасность DHCP snooping.  
### На S2 включите DHCP snooping и настройте DHCP snooping во VLAN 10.  
```
S2(config)#ip dh
S2(config)#ip dhcp sn
S2(config)#ip dhcp snooping 
S2(config)#ip dh
S2(config)#ip dhcp sn
S2(config)#ip dhcp snooping vlan 10
```  
### Настройте магистральные порты на S2 как доверенные порты.  
### Ограничьте ненадежный порт Fa0/18 на S2 пятью DHCP-пакетами в секунду.  
```
S2(config)#int fa0/1
S2(config-if)#ip d
S2(config-if)#ip dhcp s
S2(config-if)#ip dhcp snooping trust
S2(config-if)#int fa0/18
S2(config-if)#ip d
S2(config-if)#ip dhcp s
S2(config-if)#ip dhcp snooping l
S2(config-if)#ip dhcp snooping limit ra
S2(config-if)#ip dhcp snooping limit rate 5
```  
### Проверка DHCP Snooping на S2.  
S2# show ip dhcp snooping  
```
S2#sh ip dhcp snooping 
Switch DHCP snooping is enabled
DHCP snooping is configured on following VLANs:
10
Insertion of option 82 is enabled
Option 82 on untrusted port is not allowed
Verification of hwaddr field is enabled
Interface                  Trusted    Rate limit (pps)
-----------------------    -------    ----------------
FastEthernet0/1            yes        unlimited       
FastEthernet0/18           no         5         
```  


### В командной строке на PC-B освободите, а затем обновите IP-адрес.  
C:\Users\Student> ipconfig /release  
C:\Users\Student> ipconfig /renew  
```
C:\>ipconfig 

FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: CCNA2.Lab-11.6.1
   Link-local IPv6 Address.........: FE80::2D0:FFFF:FEDE:77D7
   IPv6 Address....................: ::
   IPv4 Address....................: 192.168.10.11
   Subnet Mask.....................: 255.255.255.0
   Default Gateway.................: ::
                                     192.168.10.1

Bluetooth Connection:

   Connection-specific DNS Suffix..: CCNA2.Lab-11.6.1
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0

C:\>ipconfig  /release

   IP Address......................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: 0.0.0.0
   DNS Server......................: 0.0.0.0

C:\>ipconfig  /renew

   IP Address......................: 192.168.10.11
   Subnet Mask.....................: 255.255.255.0
   Default Gateway.................: 192.168.10.1
   DNS Server......................: 0.0.0.0

C:\>
```  
### Проверьте привязку отслеживания DHCP с помощью команды show ip dhcp snooping binding.  
```
S2#sh ip dhcp snooping binding 
MacAddress          IpAddress        Lease(sec)  Type           VLAN  Interface
------------------  ---------------  ----------  -------------  ----  -----------------
00:D0:FF:DE:77:D7   192.168.10.11    0           dhcp-snooping  10    FastEthernet0/18
Total number of bindings: 1
```  



### Реализация PortFast и BPDU Guard  
### Настройте PortFast на всех портах доступа, которые используются на обоих коммутаторах.  
```
S2(config)#int fa0/18
S2(config-if)#spa
S2(config-if)#spanning-tree po
S2(config-if)#spanning-tree portfast 
%Warning: portfast should only be enabled on ports connected to a single
host. Connecting hubs, concentrators, switches, bridges, etc... to this
interface  when portfast is enabled, can cause temporary bridging loops.
Use with CAUTION

%Portfast has been configured on FastEthernet0/18 but will only
have effect when the interface is in a non-trunking mode.
S2(config-if)#

S1(config)#int ra
S1(config)#int range fa0/5-6
S1(config-if-range)#sap
S1(config-if-range)#spa
S1(config-if-range)#spanning-tree po
S1(config-if-range)#spanning-tree portfast 
%Warning: portfast should only be enabled on ports connected to a single
host. Connecting hubs, concentrators, switches, bridges, etc... to this
interface  when portfast is enabled, can cause temporary bridging loops.
Use with CAUTION

%Portfast has been configured on FastEthernet0/5 but will only
have effect when the interface is in a non-trunking mode.
%Warning: portfast should only be enabled on ports connected to a single
host. Connecting hubs, concentrators, switches, bridges, etc... to this
interface  when portfast is enabled, can cause temporary bridging loops.
Use with CAUTION

%Portfast has been configured on FastEthernet0/6 but will only
have effect when the interface is in a non-trunking mode.
```  
### Включите защиту BPDU на портах доступа VLAN 10 S1 и S2, подключенных к PC-A и PC-B.  
```
S1(config-if-range)#int fa0/6
S1(config-if)#spa
S1(config-if)#spanning-tree bp
S1(config-if)#spanning-tree bpduguard ena
S1(config-if)#spanning-tree bpduguard enable

S2(config-if)#int fa0/18
S2(config-if)#spa
S2(config-if)#spanning-tree bp
S2(config-if)#spanning-tree bpduguard enable
S2(config-if)#
S2#
%SYS-5-CONFIG_I: Configured from console by console
```  
### Убедитесь, что защита BPDU и PortFast включены на соответствующих портах.  
S1# show spanning-tree interface f0/6 detail  
```
S1#sh spanning-tree int fa0/6 detail 



Port 6 (FastEthernet0/6) of VLAN0010 is designated forwarding
  Port path cost 19, Port priority 128, Port Identifier 128.6
  Designated root has priority 32778, address 000A.F384.0717
  Designated bridge has priority 32778, address 000A.F384.0717
  Designated port id is 128.6, designated path cost 19
  Timers: message age 16, forward delay 0, hold 0
  Number of transitions to forwarding state: 1
  The port is in the portfast mode
  Link type is point-to-point by default
  ```  



### Проверьте наличие сквозного ⁪подключения.
Проверьте PING свзяь между всеми устройствами в таблице IP-адресации. В случае сбоя проверки связи может потребоваться отключить брандмауэр на хостах.  

```
S1#ping 192.168.10.202

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.10.202, timeout is 2 seconds:
..!!!
Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms


S1#ping 192.168.10.1

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.10.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/0 ms

S1#ping 192.168.10.10

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.10.10, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms

S1#ping 192.168.10.11

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.10.11, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms

S1#ping 10.10.1.1

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/0 ms
```  


⦁	Вопросы для повторения  
⦁	С точки зрения безопасности порта на S2, почему нет значения таймера для оставшегося возраста в минутах, когда было сконфигурировано динамическое обучение - sticky? Так как MAC адресс привязан.  
⦁	Что касается безопасности порта на S2, если вы загружаете скрипт текущей конфигурации на S2, почему порту 18 на PC-B никогда не получит IP-адрес через DHCP? Включен DHCP SNOOPING  
⦁	Что касается безопасности порта, в чем разница между типом абсолютного устаревания и типом устаревание по неактивности?в абсолютном отсчет начинается сразу после изучения, а по неактивности - начнет отсчитываться когда клиент неактивен  

