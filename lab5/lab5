```
Router>en
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#host R1
R1(config)#ena
R1(config)#enable sec
R1(config)#enable secret class
R1(config)#line vty 0 
R1(config-line)#line vty 0 4
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#tr
R1(config-line)#transport in
R1(config-line)#transport input all
R1(config-line)#exit
R1(config)#ban
R1(config)#banner mo
R1(config)#banner motd *
Enter TEXT message.  End with the character '*'.
NO ENTRY*

R1(config)#ser
R1(config)#service pa
R1(config)#service password-encryption 
R1#cloc
R1#clock  se
R1#clock  set  11:11:00 21 aprik 2023
                           ^
% Invalid input detected at '^' marker.
	
R1#clock  set  11:11:00 21 april 2023
R1#sh clo
R1#sh clock 
11:11:2.719 UTC Fri Apr 21 2023
R1#wr mem
Building configuration...
[OK]
R1#
```



```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#en
Switch(config)#ena
Switch(config)#enable se
Switch(config)#enable secret class
Switch(config)#host
Switch(config)#hostname S1
S1(config)#line vty 0 4
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#tar
S1(config-line)#tra
S1(config-line)#transport in
S1(config-line)#transport input all
S1(config-line)#exit
S1(config)#ser
S1(config)#service pa
S1(config)#service password-encryption 
S1(config)#ba
S1(config)#banner mod
S1(config)#banner mo
S1(config)#banner motd *
Enter TEXT message.  End with the character '*'.
NO ENTRY*

S1(config)#clo
S1(config)#clock se
S1(config)#clock se
S1(config)#clock se?
% Unrecognized command
S1(config)#clock set ?
% Unrecognized command
S1(config)#clock ?
  timezone  Configure time zone
S1(config)#clock set
                 ^
% Invalid input detected at '^' marker.
	
S1(config)#clock c
S1(config)#clock con
S1(config)#clock cong
S1(config)#clock conf
S1(config)#clock confi
S1(config)#exit
S1#
%SYS-5-CONFIG_I: Configured from console by console

S1#
S1#
S1#
S1#clo
S1#clock s
S1#clock set 11:10:00 21 april 2023
S1#sh clock
11:10:3.145 UTC Fri Apr 21 2023
S1#wr 
Building configuration...
```

```
Switch>
Switch>
Switch>en 
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#en
Switch(config)#ena
Switch(config)#enable se
Switch(config)#enable secret class
Switch(config)#hos
Switch(config)#hostname S2
S2(config)#line v
S2(config)#line vty 0 4
S2(config-line)#password cisco
S2(config-line)#login
S2(config-line)#tar
S2(config-line)#tra
S2(config-line)#transport in
S2(config-line)#transport input a
S2(config-line)#transport input all 
S2(config-line)#exit
S2(config)#ser
S2(config)#service pas
S2(config)#service password-encryption 
S2(config)#ba
S2(config)#banner m
S2(config)#banner motd *
Enter TEXT message.  End with the character '*'.
NO ENTRY*

S2(config)#exit
S2#
%SYS-5-CONFIG_I: Configured from console by console
cloc
S2#clock set 11:13:00 21 april 2023
S2#sh clocl
          ^
% Invalid input detected at '^' marker.
	
S2#sh cloc
S2#sh clock 
11:13:4.101 UTC Fri Apr 21 2023
S2#wr mem
Building configuration...
[OK]
```

```
S1(config)#vlan 10
S1(config-vlan)#vlan 20
S1(config-vlan)#name Sales
S1(config-vlan)#vlan 30
S1(config-vlan)#name Operations
S1(config-vlan)#vlan 999
S1(config-vlan)#name Parking_lot
S1(config-vlan)#vlan 1000
S1(config-vlan)#
```

```
S2(config)#ip default-gateway 192.168.10.1
S2(config)#int vlan 10
S2(config-if)#
%LINK-5-CHANGED: Interface Vlan10, changed state to up
ip
% Incomplete command.
S2(config-if)#
S2(config-if)#
S2(config-if)#ip
S2(config-if)#ip  ad
S2(config-if)#ip  address  192.168.10.12 255.255.255.0
```

```
S1(config)#ip de
S1(config)#ip default-gateway 192.168.10.1
S1(config)#int vlan 10
S1(config-if)#
%LINK-5-CHANGED: Interface Vlan10, changed state to up

S1(config-if)#
S1(config-if)#ip ad
S1(config-if)#ip address 192.168.10.11 255.255.255.0
```

```
S1(config)#int range f0/2-4, f0/7-24, g0/1-2
S1(config-if-range)#sw
S1(config-if-range)#switchport mo
S1(config-if-range)#switchport mode ac
S1(config-if-range)#switchport mode access 
S1(config-if-range)#sw
S1(config-if-range)#switchport ac
S1(config-if-range)#switchport access vlan 999
S1(config-if-range)#sh
S1(config-if-range)#shutdown 

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
S1(config-if-range)#
```

```
S2(config)#int range f0/2-17, f0/19-24, g0/1-2
S2(config-if-range)#sw
S2(config-if-range)#switchport mo
S2(config-if-range)#switchport mode ac
S2(config-if-range)#switchport mode access 
S2(config-if-range)#sw
S2(config-if-range)#switchport ac
S2(config-if-range)#switchport access vlan 999
S2(config-if-range)#sh
S2(config-if-range)#shutdown 

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

%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to administratively down

%LINK-5-CHANGED: Interface GigabitEthernet0/2, changed state to administratively down
```

```
S1(config-if-range)#int fa0/6
S1(config-if)#sw
S1(config-if)#switchport mo
S1(config-if)#switchport mode ac
S1(config-if)#switchport mode access 
S1(config-if)#sw
S1(config-if)#switchport ac
S1(config-if)#switchport access vlan 20
S1(config-if)#
```

```
S2(config)#int f0/18
S2(config-if)#swi
S2(config-if)#switchport mo
S2(config-if)#switchport mode ac
S2(config-if)#switchport mode access 
S2(config-if)#swi
S2(config-if)#switchport ac
S2(config-if)#switchport access vlan 30
S2(config-if)#exit
```

```
S1(config-if)#int fa0/1
S1(config-if)#swi
S1(config-if)#switchport mod
S1(config-if)#switchport mode trunk

S1(config-if)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan10, changed state to up

S1(config-if)#swi
S1(config-if)#switchport tr
S1(config-if)#switchport trunk native vlan 1000
S1(config-if)#sw
S1(config-if)#switchport tr
S1(config-if)#switchport trunk all
S1(config-if)#switchport trunk allowed vlan 10,20,30,1000
```

```
S2(config)#int fa0/1
S2(config-if)#swi
S2(config-if)#switchport mod
S2(config-if)#switchport mode trunk
S2(config-if)#swi
S2(config-if)#switchport tr
S2(config-if)#switchport trunk na
S2(config-if)#switchport trunk native 
%CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on FastEthernet0/1 (1), with S1 switchport tr
S2(config-if)#switchport trunk na
S2(config-if)#switchport trunk native vlan 1000
S2(config-if)#%SPANTREE-2-UNBLOCK_CONSIST_PORT: Unblocking FastEthernet0/1 on VLAN1000. Port consistency restored.

%SPANTREE-2-UNBLOCK_CONSIST_PORT: Unblocking FastEthernet0/1 on VLAN0001. Port consistency restored.

sw
S2(config-if)#switchport tr
S2(config-if)#switchport trunk all
S2(config-if)#switchport trunk allowed vlan 10,20,30,1000
S2(config-if)#sw
S2(config-if)#switchport no
S2(config-if)#switchport nonegotiate 
S2(config-if)#do sh vlan

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    
10   VLAN0010                         active    
20   Sales                            active    
30   Operations                       active    Fa0/18
999  Parking_Lot                      active    Fa0/2, Fa0/3, Fa0/4, Fa0/5
                                                Fa0/6, Fa0/7, Fa0/8, Fa0/9
                                                Fa0/10, Fa0/11, Fa0/12, Fa0/13
                                                Fa0/14, Fa0/15, Fa0/16, Fa0/17
                                                Fa0/19, Fa0/20, Fa0/21, Fa0/22
                                                Fa0/23, Fa0/24, Gig0/1, Gig0/2
1000 VLAN1000                         active    
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1    enet  100001     1500  -      -      -        -    -        0      0

S2(config-if)#o sh int runk
              ^
% Invalid input detected at '^' marker.
	
S2(config-if)#do sh int trunk
Port        Mode         Encapsulation  Status        Native vlan
Fa0/1       on           802.1q         trunking      1000

Port        Vlans allowed on trunk
Fa0/1       10,20,30,1000

Port        Vlans allowed and active in management domain
Fa0/1       10,20,30,1000

Port        Vlans in spanning tree forwarding state and not pruned
Fa0/1       none

S2(config-if)#
```

```
S1(config-if)#int fa0/5
S1(config-if)#sw
S1(config-if)#switchport m
S1(config-if)#switchport mode trunk
S1(config-if)#sw
S1(config-if)#switchport trunk
S1(config-if)#switchport trunk na
S1(config-if)#switchport trunk native vlan 1000
S1(config-if)#swi
S1(config-if)#switchport no
S1(config-if)#switchport nonegotiate 
S1(config-if)#sw
S1(config-if)#switchport tr
S1(config-if)#switchport trunk allow
S1(config-if)#switchport trunk allowed vlan 10,20,30,1000
S1(config-if)#exit
S1(config)#
S1(config)#
S1(config)#
S1(config)#exit
S1#
%SYS-5-CONFIG_I: Configured from console by console

S1#
S1#cope
S1#copy
S1#copy ru
S1#copy running-config st
S1#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
S1#
```

```
R1(config)#int g0/0/1
R1(config-if)#no sh

R1(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up

R1(config-if)#
R1(config-if)#
R1(config-if)#int gi0/0/1.10
R1(config-subif)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.10, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.10, changed state to up

R1(config-subif)#
R1(config-subif)#enc
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q 10
R1(config-subif)#ip ad
R1(config-subif)#ip address 192.168.10.1 255.255.255.0
R1(config-subif)#int gi0/0/1.20
R1(config-subif)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.20, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.20, changed state to up
en
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q 20
R1(config-subif)#ip add
R1(config-subif)#ip address 192.168.20.1 255.255.255.0
R1(config-subif)#int gi0/0/1.30
R1(config-subif)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.30, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.30, changed state to up

R1(config-subif)#
R1(config-subif)#en
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q  30
R1(config-subif)#ip ad
R1(config-subif)#ip address 192.168.30.1
% Incomplete command.
R1(config-subif)#ip address 192.168.30.1 255.255.255.0
R1(config-subif)#
R1(config-subif)#
R1(config-subif)#
R1(config-subif)#int gi0/0/1.1000
R1(config-subif)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.1000, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.1000, changed state to up

R1(config-subif)#
R1(config-subif)#
R1(config-subif)#
R1(config-subif)#do
R1(config-subif)#e
R1(config-subif)#en
R1(config-subif)#encapsulation d
R1(config-subif)#encapsulation dot1Q 1000
R1(config-subif)#
```

```
C:\>ping 192.168.20.1

Pinging 192.168.20.1 with 32 bytes of data:

Reply from 192.168.20.1: bytes=32 time<1ms TTL=255
Reply from 192.168.20.1: bytes=32 time=1ms TTL=255
Reply from 192.168.20.1: bytes=32 time<1ms TTL=255
Reply from 192.168.20.1: bytes=32 time<1ms TTL=255
```

```
C:\>ping 192.168.30.3

Pinging 192.168.30.3 with 32 bytes of data:

Request timed out.
Reply from 192.168.30.3: bytes=32 time=1ms TTL=127
Reply from 192.168.30.3: bytes=32 time<1ms TTL=127
Reply from 192.168.30.3: bytes=32 time<1ms TTL=127

Ping statistics for 192.168.30.3:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss),
```

```
C:\>ping 192.168.10.12

Pinging 192.168.10.12 with 32 bytes of data:

Request timed out.
Request timed out.
Reply from 192.168.10.12: bytes=32 time<1ms TTL=254
Reply from 192.168.10.12: bytes=32 time<1ms TTL=254
```

```
C:\>tracert 192.168.20.3

Tracing route to 192.168.20.3 over a maximum of 30 hops: 

  1   0 ms      0 ms      0 ms      192.168.30.1
  2   1 ms      0 ms      0 ms      192.168.20.3

Trace complete.
```

