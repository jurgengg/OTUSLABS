## Создайте сеть согласно топологии.  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab11/net.png)  
## Произведите базовую настройку маршрутизаторов  
```
Router>en
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#host R1
R1(config)#no do
R1(config)#no dot
R1(config)#do
R1(config)#doma
R1(config)#no ip
R1(config)#no ip 
R1(config)#no ip d
R1(config)#no ip doa
R1(config)#no ip do
R1(config)#no ip doma
R1(config)#no ip domain
R1(config)#no ip domain
% Incomplete command.
R1(config)#no ip domain-lookup
R1(config)#ena
R1(config)#enable se
R1(config)#enable secret class
R1(config)#line
R1(config)#line  
R1(config)#line c
R1(config)#line console 0
R1(config-line)#pas
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#line vty 0 4
R1(config-line)#pa
R1(config-line)#pas
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#ser
R1(config-line)#servi
R1(config-line)#ex
% Ambiguous command: "ex"
R1(config-line)#
R1(config-line)#ex
% Ambiguous command: "ex"
R1(config-line)#
R1(config-line)#
R1(config-line)#
R1#
%SYS-5-CONFIG_I: Configured from console by console

R1#
R1#
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#ser
R1(config)#service pa
R1(config)#service password-encryption 
R1(config)#ba
R1(config)#banner m
R1(config)#banner motd "
Enter TEXT message.  End with the character '"'.
NO ENTRY"

R1(config)#co
R1(config)#cop
R1(config)#cope
R1(config)#copy 
R1(config)#copy r
R1(config)#copy ru
R1(config)#
R1#
%SYS-5-CONFIG_I: Configured from console by console

R1#
R1#co
R1#copy
R1#copy r
R1#copy running-config s
R1#copy running-config sta
R1#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```
```
Router>en
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#host ?
  WORD  This system's network name
Router(config)#host R2
R2(config)#no ip
R2(config)#no ip d
R2(config)#no ip domain-l
R2(config)#no ip domain-lookup 
R2(config)#en
R2(config)#ena
R2(config)#enable se
R2(config)#enable secret class
R2(config)#le
R2(config)#line c
R2(config)#line console 0
R2(config-line)#pas
R2(config-line)#password cisco
R2(config-line)#login
R2(config-line)#line vty 0 4
R2(config-line)#pas
R2(config-line)#password cisco
R2(config-line)#login
R2(config-line)#exit
R2(config)#ser
R2(config)#service pa
R2(config)#service password-encryption 
R2(config)#ban
R2(config)#banner m
R2(config)#banner motd "
Enter TEXT message.  End with the character '"'.
NO ENTRY"

R2(config)#
R2#
%SYS-5-CONFIG_I: Configured from console by console

R2#
R2#
R2#cop
R2#copy r
R2#copy running-config s
R2#copy running-config st
R2#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```

## Настройте базовые параметры каждого коммутатора  
```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#host S1
S1(config)#no ip
S1(config)#no ip do
S1(config)#no ip doma
S1(config)#no ip domai
S1(config)#no ip domain
S1(config)#no ip domain-
S1(config)#no ip domain-l
S1(config)#no ip domain-lookup 
S1(config)#ena
S1(config)#enable se
S1(config)#enable secret class
S1(config)#line
S1(config)#line co
S1(config)#line console 0
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#line vty 0 4
S1(config-line)#pas
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#exit
S1(config)#se
S1(config)#service pa
S1(config)#service password-encryption 
S1(config)#ba
S1(config)#banner m
S1(config)#banner motd  "
Enter TEXT message.  End with the character '"'.
NO ENRTY"

S1(config)#
S1#
%SYS-5-CONFIG_I: Configured from console by console

S1#
S1#
S1#co
S1#cop
S1#copy r
S1#copy running-config s
S1#copy running-config st
S1#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```

```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#host S2
S2(config)#no ip domaun-
S2(config)#no ip domain-
S2(config)#no ip domain-
% Ambiguous command: "no ip domain-"
S2(config)#no ip domain-l
S2(config)#no ip domain-lookup 
S2(config)#en
S2(config)#ena
S2(config)#enable se
S2(config)#enable secret class
S2(config)#line vty 0 4
S2(config-line)#passw
S2(config-line)#password cisco
S2(config-line)#login
S2(config-line)#line co
S2(config-line)#line con
S2(config-line)#line cons
S2(config-line)#line cons
S2(config-line)#line cons
S2(config-line)#line cons
S2(config-line)#line cons
S2(config-line)#line cons
S2(config-line)#line conso
S2(config-line)#
S2#
%SYS-5-CONFIG_I: Configured from console by console

S2#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S2(config)#line
S2(config)#line  
S2(config)#line  c
S2(config)#line  console 0
S2(config-line)#pas
S2(config-line)#password cisco
S2(config-line)#login
S2(config-line)#exit
S2(config)#ser
S2(config)#service pa
S2(config)#service password-encryption 
S2(config)#ban
S2(config)#banner mo
S2(config)#banner motd "
Enter TEXT message.  End with the character '"'.
NO ENTRY"

S2(config)#
S2#
%SYS-5-CONFIG_I: Configured from console by console

S2#copy r
S2#copy running-config st
S2#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```
# Настройка сетей VLAN на коммутаторах  
## Создайте сети VLAN на коммутаторах  
```
S1(config)#vlan 20
S1(config-vlan)#na
S1(config-vlan)#name Management
S1(config-vlan)#vlan 30
S1(config-vlan)#name Oper
S1(config-vlan)#name Operations
S1(config-vlan)#vlan 40
S1(config-vlan)#name Salex
S1(config-vlan)#vlan 999
S1(config-vlan)#name ParkingLOT
S1(config-vlan)#vlan 1000
S1(config-vlan)#name Sobstv
S1(config-if)#do sh vlan

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/7, Fa0/8, Fa0/9
                                                Fa0/10, Fa0/11, Fa0/12, Fa0/13
                                                Fa0/14, Fa0/15, Fa0/16, Fa0/17
                                                Fa0/18, Fa0/19, Fa0/20, Fa0/21
                                                Fa0/22, Fa0/23, Fa0/24, Gig0/1
                                                Gig0/2
20   Management                       active    
30   Operations                       active    Fa0/6
40   Salex                            active    
999  ParkingLOT                       active    
1000 Sobstv                           active    
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1    enet  100001     1500  -      -      -        -    -        0      0
20   enet  100020     1500  -      -      -        -    -        0      0
30   enet  100030     1500  -      -      -        -    -        0      0
40   enet  100040     1500  -      -      -        -    -        0      0
999  enet  100999     1500  -      -      -        -    -        0      0
1000 enet  101000     1500  -      -      -        -    -        0      0
1002 fddi  101002     1500  -      -      -        -    -        0      0   
1003 tr    101003     1500  -      -      -        -    -        0      0   
1004 fdnet 101004     1500  -      -      -        ieee -        0      0   
1005 trnet 101005     1500  -      -      -        ibm  -        0      0   

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------

Remote SPAN VLANs
------------------------------------------------------------------------------

Primary Secondary Type              Ports
------- --------- ----------------- ------------------------------------------
S1(config-if)#int ra
S1(config-if)#exit
S1(config)#int ra
S1(config)#int range fa0/2-4, fa0/7-24, gi0/1-2
S1(config-if-range)#swi
S1(config-if-range)#switchport mo
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

%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to administratively down

%LINK-5-CHANGED: Interface GigabitEthernet0/2, changed state to administratively down
S1(config-if-range)#do sh vlan

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/5
20   Management                       active    
30   Operations                       active    Fa0/6
40   Salex                            active    
999  ParkingLOT                       active    Fa0/2, Fa0/3, Fa0/4, Fa0/7
                                                Fa0/8, Fa0/9, Fa0/10, Fa0/11
                                                Fa0/12, Fa0/13, Fa0/14, Fa0/15
                                                Fa0/16, Fa0/17, Fa0/18, Fa0/19
                                                Fa0/20, Fa0/21, Fa0/22, Fa0/23
                                                Fa0/24, Gig0/1, Gig0/2
1000 Sobstv                           active    
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1    enet  100001     1500  -      -      -        -    -        0      0
20   enet  100020     1500  -      -      -        -    -        0      0
30   enet  100030     1500  -      -      -        -    -        0      0
40   enet  100040     1500  -      -      -        -    -        0      0
999  enet  100999     1500  -      -      -        -    -        0      0
1000 enet  101000     1500  -      -      -        -    -        0      0
1002 fddi  101002     1500  -      -      -        -    -        0      0   
1003 tr    101003     1500  -      -      -        -    -        0      0   
1004 fdnet 101004     1500  -      -      -        ieee -        0      0   
1005 trnet 101005     1500  -      -      -        ibm  -        0      0   

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------

Remote SPAN VLANs
------------------------------------------------------------------------------

Primary Secondary Type              Ports
------- --------- ----------------- ------------------------------------------
S1(config-if-range)#
S1(config)#ip de
S1(config)#ip default-gateway 10.20.0.1
S1(config)#int vlan 20
S1(config-if)#
%LINK-5-CHANGED: Interface Vlan20, changed state to up

S1(config-if)#
S1(config-if)#ip ad
S1(config-if)#ip address 10.20.0.2 255.255.255.0
```

```
S2(config)#vlan 20
S2(config-vlan)#name Management
S2(config-vlan)#vlan 30
S2(config-vlan)#name Operations
S2(config-vlan)#vlan 40
S2(config-vlan)#name Salex
S2(config-vlan)#vlan 999
S2(config-vlan)#name Parkinklot
S2(config-vlan)#vlan 1000
S2(config-vlan)#name Sobst
S2(config-vlan)#exit
S2(config)#

S2(config-if)#int fa0/2-4, fa0/6-17, fa0/19-24, gi0/1-2
               ^
% Invalid input detected at '^' marker.
	
S2(config-if)#int range fa0/2-4, fa0/6-17, fa0/19-24, gi0/1-2
S2(config-if-range)#swi
S2(config-if-range)#switchport mo
S2(config-if-range)#switchport mode ac
S2(config-if-range)#switchport mode access 
S2(config-if-range)#swi
S2(config-if-range)#switchport ac
S2(config-if-range)#switchport access vlan 999
S2(config-if-range)#shu

%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/3, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/4, changed state to administratively down

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

%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to administratively down

%LINK-5-CHANGED: Interface GigabitEthernet0/2, changed state to administratively down
S2(config-if-range)#exit

S2(config)#ip default-gateway 10.20.0.1
S2(config)#int vlan 20
S2(config-if)#
%LINK-5-CHANGED: Interface Vlan20, changed state to up

S2(config-if)#
S2(config-if)#
S2(config-if)#ip ad
S2(config-if)#ip address 10.20.0.3 255.255.255.0
S2(config-if)#
```

### Назначьте сети VLAN соответствующим интерфейсам коммутатора  
```
S2(config)#int fa0/18
S2(config-if)#swi
S2(config-if)#switchport m
S2(config-if)#switchport mode ac
S2(config-if)#switchport mode access 
S2(config-if)#sw
S2(config-if)#switchport ac
S2(config-if)#switchport access vlan 40
S2(config)#int fa0/5
S2(config-if)#swi
S2(config-if)#switchport m
S2(config-if)#switchport mode ac
S2(config-if)#switchport mode access 
S2(config-if)#sw
S2(config-if)#switchport ac
S2(config-if)#switchport access vlan 20
```
```
S1(config-vlan)#int fa0/6
S1(config-if)#swi
S1(config-if)#switchport mo
S1(config-if)#switchport mode ac
S1(config-if)#switchport mode access 
S1(config-if)#sei
S1(config-if)#sw
S1(config-if)#switchport ac
S1(config-if)#switchport access vlan 30
```

# Настройте транки (магистральные каналы  
## Вручную настройте магистральный интерфейс F0/1  
```
S1(config-if)#int fa0/1
S1(config-if)#swi
S1(config-if)#switchport mo
S1(config-if)#switchport mode tr
S1(config-if)#switchport mode trunk 

S1(config-if)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan20, changed state to up
swi
S1(config-if)#switchport tr
S1(config-if)#switchport trunk na
S1(config-if)#switchport trunk native vlan 1000
S1(config-if)#sw
S1(config-if)#switchport tr
S1(config-if)#switchport trunk al
S1(config-if)#switchport trunk allowed vla
%CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on FastEthernet0/1 (1000), wswitchport trunk native vlan 1000
%CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on FastEthernet0/1 (1000), with S2 FastEthernet0/1 (1).

S1(config-if)#
S1(config-if)#
S1(config-if)#
S1(config-if)#sw
S1(config-if)#switchport tr
S1(config-if)#switchport trunk al
S1(config-if)#switchport trunk allowed vlan 20,30,40,1000
```

```
S2(config-if)#int fa0/1
S2(config-if)#sw
S2(config-if)#switchport mo
S2(config-if)#switchport mode tr
S2(config-if)#switchport mode trunk 
S2(config-if)#swi
S2(config-if)#switchport tr
S2(config-if)#switchport trunk vl
S2(config-if)#switchport trunk na
S2(config-if)#switchport trunk native vlan 1000
S2(config-if)#%SPANTREE-2-UNBLOCK_CONSIST_PORT: Unblocking FastEthernet0/1 on VLAN1000. Port consistency restored.

%SPANTREE-2-UNBLOCK_CONSIST_PORT: Unblocking FastEthernet0/1 on VLAN0001. Port consistency restored.


S2(config-if)#
S2(config-if)#sw
S2(config-if)#switchport tr
S2(config-if)#switchport trunk al
S2(config-if)#switchport trunk allowed vla
S2(config-if)#switchport trunk allowed vlan 20,30,40,1000
S2(config-if)#do sh int tr
Port        Mode         Encapsulation  Status        Native vlan
Fa0/1       on           802.1q         trunking      1000

Port        Vlans allowed on trunk
Fa0/1       10,20,30,1000

Port        Vlans allowed and active in management domain
Fa0/1       20,30,1000

Port        Vlans in spanning tree forwarding state and not pruned
Fa0/1       none
```
## 1)	Вручную настройте магистральный интерфейс F0/5 на коммутаторе S1  
```
S1(config-if)#int fa0/5
S1(config-if)#sw
S1(config-if)#switchport m
S1(config-if)#switchport mode tr
S1(config-if)#switchport mode trunk 
S1(config-if)#swi
S1(config-if)#switchport tr
S1(config-if)#switchport trunk na
S1(config-if)#switchport trunk native vlan 1000
S1(config-if)#sw
S1(config-if)#switchport tr
S1(config-if)#switchport trunk al
S1(config-if)#switchport trunk allowed vlan 10,20,30,1000
```
# Настройте маршрутизацию  
## Настройка маршрутизации между сетями VLAN на R1  
```
R1(config)#int g0/0/1
R1(config-if)#no shu

R1(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up

R1(config-if)#
R1(config-if)#
R1(config-if)#
R1(config-if)#int gi0/0/1.20
R1(config-subif)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.20, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.20, changed state to up

R1(config-subif)#
R1(config-subif)#en
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q 20
R1(config-subif)#ip a
R1(config-subif)#ip ad
R1(config-subif)#ip address 10.20.0.1
% Incomplete command.
R1(config-subif)#ip address 10.20.0.1 255.255.255.0
R1(config-subif)#int gi0/0/1.30
R1(config-subif)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.30, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.30, changed state to up

R1(config-subif)#en
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q 30
R1(config-subif)#ip ad
R1(config-subif)#ip address 10.30.0.1
% Incomplete command.
R1(config-subif)#ip address 10.30.0.1 255.255.255.0
R1(config-subif)#int gi0/0/1.40
R1(config-subif)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.40, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.40, changed state to up

R1(config-subif)#en
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q 40
R1(config-subif)#ip
R1(config-subif)#ip ad
R1(config-subif)#ip address 10.40.0.1 255.255.255.0
% 10.30.0.0 overlaps with GigabitEthernet0/0/1.30
R1(config-subif)#int gi0/0/1.1000
R1(config-subif)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.1000, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.1000, changed state to up

R1(config-subif)#en
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q 1000
R1(config-subif)#en
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q 1000 na
R1(config-subif)#encapsulation dot1Q 1000 native 

R1(config-subif)#int gi0/0/1
R1(config-if)#int lo
R1(config-if)#int loop
R1(config-if)#int loopback 1

R1(config-if)#
%LINK-5-CHANGED: Interface Loopback1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback1, changed state to up
ip ad
R1(config-if)#ip address 172.16.1.1 255.255.255.0
```
## Настройка интерфейса R2 g0/0/1 с использованием адреса из таблицы и маршрута по умолчанию с адресом следующего перехода 10.20.0.1  
```
R2(config)#int gi0/0/1
R2(config-if)#no sh

R2(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up

R2(config-if)#ip ad
R2(config-if)#ip address 10.20.0.4 255.255.255.0

R2(config)#ip route 10.20.0.0 255.255.255.0 10.20.0.1
R2(config)#
```
### Настройте все сетевые устройства для базовой поддержки SSH.  
```
R1(config)#ip domain-name ccna-lab.com
R1(config)#cry
R1(config)#crypto ke
R1(config)#crypto key gen rsa
The name for the keys will be: R1.ccna-lab.com
Choose the size of the key modulus in the range of 360 to 2048 for your
  General Purpose Keys. Choosing a key modulus greater than 512 may take
  a few minutes.

How many bits in the modulus [512]: 1024
% Generating 1024 bit RSA keys, keys will be non-exportable...[OK]

R1(config)#ip ss
*Mar 1 1:1:46.693: %SSH-5-ENABLED: SSH 1.99 has been enabled
R1(config)#ip ssh ver 2
R1(config)#use
R1(config)#username SSHadmin secret $cisco123!
R1(config)#line v
R1(config)#line vty 0 4
R1(config-line)#logi
R1(config-line)#login lo
R1(config-line)#login local 
R1(config-line)#tr
R1(config-line)#transport in
R1(config-line)#transport input ss
R1(config-line)#transport input ssh

АНАЛОГИЧНО НАСТРОЕНЫ НА ВСЕХ УСТРОЙСТВАХ
```
## Включите защищенные веб-службы с проверкой подлинности на R1  
```
R1(config)#ip http secure-server 
               ^
% Invalid input detected at '^' marker.
	
R1(config)#ip htt?
% Unrecognized command
R1(config)#ip htt
               ^
% Invalid input detected at '^' marker.
	
R1(config)#ip https
               ^
% Invalid input detected at '^' marker.
	
R1(config)#ip http
               ^
% Invalid input detected at '^' marker.
	
R1(config)#ip http authentication local
               ^
% Invalid input detected at '^' marker.
	
R1(config)#
```
## Настройте узлы ПК  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab11/pc1.png)  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab11/pc2.png)  
# Выполните следующие тесты. Эхозапрос должен пройти успешно  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab11/ping1.png)  
```
C:\>ping 10.40.0.10

Pinging 10.40.0.10 with 32 bytes of data:

Request timed out.
Reply from 10.40.0.10: bytes=32 time<1ms TTL=127
Reply from 10.40.0.10: bytes=32 time<1ms TTL=127
Reply from 10.40.0.10: bytes=32 time<1ms TTL=127

Ping statistics for 10.40.0.10:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```
```
Pinging 10.20.0.1 with 32 bytes of data:

Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time=3ms TTL=255

Ping statistics for 10.20.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 3ms, Average = 0ms
```

```
C:\>ping 10.30.0.10

Pinging 10.30.0.10 with 32 bytes of data:

Reply from 10.30.0.10: bytes=32 time<1ms TTL=127
Reply from 10.30.0.10: bytes=32 time<1ms TTL=127
Reply from 10.30.0.10: bytes=32 time=1ms TTL=127
Reply from 10.30.0.10: bytes=32 time<1ms TTL=127

Ping statistics for 10.30.0.10:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 1ms, Average = 0ms
```
```
C:\>ping 10.20.0.1

Pinging 10.20.0.1 with 32 bytes of data:

Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time<1ms TTL=255

Ping statistics for 10.20.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```
```
C:\>ping 172.16.1.1

Pinging 172.16.1.1 with 32 bytes of data:

Reply from 172.16.1.1: bytes=32 time<1ms TTL=255
Reply from 172.16.1.1: bytes=32 time<1ms TTL=255
Reply from 172.16.1.1: bytes=32 time<1ms TTL=255
Reply from 172.16.1.1: bytes=32 time<1ms TTL=255

Ping statistics for 172.16.1.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```
```
C:\>ssh -l SSHadmin 10.20.0.1

Password: 


NO ENTRY

R1>C:\>ssh -l SSHadmin 172.16.1.1

Password: 


NO ENTRY

R1>
```
## Настройка и проверка списков контроля доступа (ACL)  
При проверке базового подключения компания требует реализации следующих политик безопасности:  
Политика1. Сеть Sales не может использовать SSH в сети Management (но в  другие сети SSH разрешен).   
Политика 2. Сеть Sales не имеет доступа к IP-адресам в сети Management с помощью любого веб-протокола (HTTP/HTTPS). Сеть Sales также не имеет доступа к интерфейсам R1 с помощью любого веб-протокола. Разрешён весь другой веб-трафик (обратите внимание — Сеть Sales  может получить доступ к интерфейсу Loopback 1 на R1).  
Политика3. Сеть Sales не может отправлять эхо-запросы ICMP в сети Operations или Management. Разрешены эхо-запросы ICMP к другим адресатам  
Политика 4: Cеть Operations  не может отправлять ICMP эхозапросы в сеть Sales. Разрешены эхо-запросы ICMP к другим адресатам.  

##  Проанализируйте требования к сети и политике безопасности для планирования реализации ACL.  

Реализация двух расширенных списков доступа,как можно ближе к источнику фильтруемого трафика, эти ACL будут размещаться на интерфейсах G0/0/0.30 и G0/0/0.40.  

## Разработка и применение расширенных списков доступа, которые будут соответствовать требованиям политики безопасности  
```
R1(config)# access-list 101 deny tcp 10.40.0.0 0.0.0.255 10.20.0.0 0.0.0.255 eq 22
R1(config)# access-list 101 deny tcp 10.40.0.0 0.0.0.255 10.20.0.0 0.0.0.255 eq 80
R1(config)# access-list 101 deny tcp 10.40.0.0 0.0.0.255 10.30.0.1 0.0.0.0 eq 80
R1(config)# access-list 101 deny tcp 10.40.0.0 0.0.0.255 10.40.0.1 0.0.0.0 eq 80
R1(config)# access-list 101 deny tcp 10.40.0.0 0.0.0.255 10.20.0.0 0.0.0.255 eq 443
R1(config)# access-list 101 deny tcp 10.40.0.0 0.0.0.255 10.30.0.1 0.0.0.0 eq 443
R1(config)# access-list 101 deny tcp 10.40.0.0 0.0.0.255 10.40.0.1 0.0.0.0 eq 443
R1(config)# access-list 101 deny icmp 10.40.0.0 0.0.0.255 10.20.0.0 0.0.0.255 echo
R1(config)# access-list 101 deny icmp 10.40.0.0 0.0.0.255 10.30.0.0 0.0.0.255 echo
R1(config)# access-list 101 permit ip any any
R1(config)# interface g0/0/1.40
R1(config-subif)# ip access-group 101 in

R1(config)# access-list 102 remark ACL 102 fulfills policy 4
R1(config)# access-list 102 deny icmp 10.30.0.0 0.0.0.255 10.40.0.0 0.0.0.255 echo
R1(config)# access-list 102 permit ip any any
R1(config)# interface g0/0/1.30
R1(config-subif)# ip access-group 102 in
```
## Убедитесь, что политики безопасности применяются развернутыми списками доступа  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab11/ping2.png)  
```
C:\>ping 10.40.0.10

Pinging 10.40.0.10 with 32 bytes of data:

Reply from 10.30.0.1: Destination host unreachable.
Reply from 10.30.0.1: Destination host unreachable.
Reply from 10.30.0.1: Destination host unreachable.
Reply from 10.30.0.1: Destination host unreachable.

Ping statistics for 10.40.0.10:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
	
	
	
	C:\>ping 10.20.0.1

Pinging 10.20.0.1 with 32 bytes of data:

Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time<1ms TTL=255
Reply from 10.20.0.1: bytes=32 time<1ms TTL=255

Ping statistics for 10.20.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```
```
C:\>ping 10.30.0.10

Pinging 10.30.0.10 with 32 bytes of data:

Reply from 10.40.0.1: Destination host unreachable.
Reply from 10.40.0.1: Destination host unreachable.
Reply from 10.40.0.1: Destination host unreachable.
Reply from 10.40.0.1: Destination host unreachable.

Ping statistics for 10.30.0.10:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),


C:\>ping 10.20.0.1

Pinging 10.20.0.1 with 32 bytes of data:

Reply from 10.40.0.1: Destination host unreachable.
Reply from 10.40.0.1: Destination host unreachable.
Reply from 10.40.0.1: Destination host unreachable.
Reply from 10.40.0.1: Destination host unreachable.

Ping statistics for 10.20.0.1:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
	
	
	
	ping 172.16.1.1

Pinging 172.16.1.1 with 32 bytes of data:

Reply from 172.16.1.1: bytes=32 time<1ms TTL=255
Reply from 172.16.1.1: bytes=32 time<1ms TTL=255
Reply from 172.16.1.1: bytes=32 time<1ms TTL=255
Reply from 172.16.1.1: bytes=32 time<1ms TTL=255

Ping statistics for 172.16.1.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	
	C:\>ssh -l SSHadmin 10.20.0.4

% Connection timed out; remote host not responding


C:\>ssh -l SSHadmin 10.20.0.4

% Connection timed out; remote host not responding
C:\>ssh -l SSHadmin 172.16.1.1

Password: 
% Login invalid


Password: 


NO ENTRY

R1>
```







