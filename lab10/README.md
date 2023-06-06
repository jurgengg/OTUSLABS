# OTUSLABS
```
Router>en
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#enable sec
Router(config)#enable secret class
Router(config)#line con
Router(config)#line console 0
Router(config-line)#pass
Router(config-line)#password cisco
Router(config-line)#login
Router(config-line)#line vty 0 4
Router(config-line)#password cisco
Router(config-line)#login
Router(config-line)#pass
Router(config-line)#ser
Router(config-line)#serv
Router(config-line)#pass
Router(config-line)#password ser
Router(config-line)#password serv
Router(config-line)#password servi
Router(config-line)#ex
% Ambiguous command: "ex"
Router(config-line)#exit
Router(config)#ser
Router(config)#service pa
Router(config)#service password-encryption 
Router(config)#host R1
R1(config)#bann
R1(config)#banner m
R1(config)#banner motd *
Enter TEXT message.  End with the character '*'.
NO ENTRY*
R1(config)#no ip domain-lookup
R1(config)#copy
R1(config)#copy ru
R1(config)#copy ru
R1(config)#copy run
R1(config)#copy run
R1#
%SYS-5-CONFIG_I: Configured from console by console

R1#co
R1#copy
R1#copy ru
R1#copy running-config s
R1#copy running-config st
R1#copy running-config startup-config 
Destination filename [startup-config]? 
Buildi
```


```
Switch>
Switch>
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#host S1
S1(config)#no ip domai
S1(config)#no ip domain-
S1(config)#no ip domain-lo
S1(config)#no ip domain-lookup 
S1(config)#ena
S1(config)#enable sec
S1(config)#enable secret class
S1(config)#line con
S1(config)#line console 0
S1(config-line)#paasword cisco
                  ^
% Invalid input detected at '^' marker.
	
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#li
S1(config-line)#line vty 04
S1(config-line)#line vty 0 
S1(config-line)#line vty 0 4
S1(config-line)#pa
S1(config-line)#pas
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#exit
S1(config)#ser
S1(config)#service pa
S1(config)#service password-encryption 
S1(config)#ban
S1(config)#banner mo
S1(config)#banner motd *
Enter TEXT message.  End with the character '*'.
NO ENTRY*

S1(config)#wr mem
           ^
% Invalid input detected at '^' marker.
	
S1(config)#
S1#
%SYS-5-CONFIG_I: Configured from console by console
wr mem
Building configuration...
[OK]
S1#
```

```
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#
R1(config)#
R1(config)#int g0/0/1
R1(config-if)#ip ad
R1(config-if)#ip address 10.53.0.1 255.255.255.0
R1(config-if)#exit
R1(config)#int lo
R1(config)#int loopback 1

R1(config-if)#
%LINK-5-CHANGED: Interface Loopback1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback1, changed state to up
ip ad
R1(config-if)#ip address 172.16.1.1 255.255.255.0
R1(config-if)#no shu
R1(config-if)#int g0/0/1
R1(config-if)#no shu

R1(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up
R2(config)#int g0/0/1
R2(config-if)#ip ad
R2(config-if)#ip address  10.53.0.2 255.255.255.0
R2(config-if)#no shu

R2(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up

R2(config-if)#int lo
R2(config-if)#int loo
R2(config-if)#exi
R2(config)#int lo
R2(config)#int loopback 1

R2(config-if)#
%LINK-5-CHANGED: Interface Loopback1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback1, changed state to up
ip ad
R2(config-if)#ip address 192.168.1.1 255.255.255.0
R2(config-if)#
```


```
R2(config-if)#ip address 192.168.1.1 255.255.255.0
R2(config-if)#
R2(config-if)#
R2(config-if)#
R2(config-if)#exi
R2(config)#ro
R2(config)#router os
R2(config)#router ospf 56
R2(config-router)#ro
R2(config-router)#router-id 2.2.2.2
R2(config-router)#int gi0/0/1
R2(config-if)#ip os
R2(config-if)#ip ospf 56 area 0
R2(config-if)#
```


```
R1(config)#router ospf 56
R1(config-router)#ro
R1(config-router)#router-id 1.1.1.1
R1(config-router)#int g0/0/1
R1(config-if)#ip os
R1(config-if)#ip ospf 56 area 0
R1(config-if)#
00:21:01: %OSPF-5-ADJCHG: Process 56, Nbr 2.2.2.2 on GigabitEthernet0/0/1 from LOADING to FULL, Loading Done
```
```
R2(config)#router ospf 56
R2(config-router)#int lo
R2(config-router)#int loo
R2(config-router)#int loopback 1
R2(config-if)#ip os
R2(config-if)#ip ospf 56 area 0
```

```
R1#sh ip ospf ne


Neighbor ID     Pri   State           Dead Time   Address         Interface
2.2.2.2           1   FULL/BDR        00:00:36    10.53.0.2       GigabitEthernet0/0/1
R1#sh ip ro
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C       10.53.0.0/24 is directly connected, GigabitEthernet0/0/1
L       10.53.0.1/32 is directly connected, GigabitEthernet0/0/1
     172.16.0.0/16 is variably subnetted, 2 subnets, 2 masks
C       172.16.1.0/24 is directly connected, Loopback1
L       172.16.1.1/32 is directly connected, Loopback1
     192.168.1.0/32 is subnetted, 1 subnets
O       192.168.1.1/32 [110/2] via 10.53.0.2, 00:11:02, GigabitEthernet0/0/1
```


```
R1#sh ip rou ospf
     192.168.1.0/32 is subnetted, 1 subnets
O       192.168.1.1 [110/2] via 10.53.0.2, 00:13:21, GigabitEthernet0/0/1

```

```
R1#ping 192.168.1.1

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/4 ms

```
```
R1(config)#router ospf 56
R1(config-router)#int g0/0/1
R1(config-if)#ip os
R1(config-if)#ip ospf p
R1(config-if)#ip ospf priority 50
R1(config-if)#ip os
R1(config-if)#ip ospf h
R1(config-if)#ip ospf hello-interval 30
```
```
R2(config-router)#router ospf 56
R2(config-router)#int gi0/0/1
R2(config-if)#ip os
R2(config-if)#ip ospf h
R2(config-if)#ip ospf hello-interval 30
```

```
R1(config)#ip route ?
  A.B.C.D  Destination prefix
R1(config)#ip route 0.0.0.0 0.0.0.0 lo
R1(config)#ip route 0.0.0.0 0.0.0.0 loopback 1
%Default route without gateway, if not a point-to-point interface, may impact performance
R1(config)#
R1#
%SYS-5-CONFIG_I: Configured from console by console

R1#
R1#en
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#ro
R1(config)#router os
R1(config)#router ospf 56
R1(config-router)#de
R1(config-router)#default-information o
R1(config-router)#default-information originate 
R1(config-router)#end
R1#
%SYS-5-CONFIG_I: Configured from console by console
```
```
R2(config)#int loopback 1
R2(config-if)#ip os
R2(config-if)#ip ospf ne
R2(config-if)#ip ospf network po
R2(config-if)#ip ospf network point-to-point 
```

```
R2(config)#router os
R2(config)#router ospf 56
R2(config-router)#ine lo
R2(config-router)#int lo
R2(config-router)#int loo 1
R2(config-if)#no ip ospf 56 area 0
R2(config-if)#
```
```
R1(config)#router os
R1(config)#router ospf  56
R1(config-router)#a
R1(config-router)#au
R1(config-router)#auto-cost re
R1(config-router)#auto-cost reference-bandwidth 10000
% OSPF: Reference bandwidth is changed.
       Please ensure reference bandwidth is consistent across all routers.
       R2(config)#router ospf  56
R2(config-router)#au
R2(config-router)#auto-cost re
R2(config-router)#auto-cost reference-bandwidth 10000
% OSPF: Reference bandwidth is changed.
        Please ensure reference bandwidth is consistent across all routers.
R2(config-router)#clear ip os
 ```
