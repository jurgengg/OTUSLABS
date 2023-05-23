# OTUSLABS
# OTUSLABS
### Настройте маршрутизатор  
```
Router>en
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#en
Router(config)#ena
Router(config)#enable sw
Router(config)#enable se
Router(config)#enable secret class
Router(config)#host R1
R1(config)#ban
R1(config)#banner m
R1(config)#banner motd *
Enter TEXT message.  End with the character '*'.
NO ENRTY*

R1(config)#li
R1(config)#lin
R1(config)#line 
R1(config)#line v
R1(config)#line vty  0 4
R1(config-line)#pas
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#tar
R1(config-line)#tra
R1(config-line)#transport in
R1(config-line)#transport input all
R1(config-line)#exit
R1(config)#ser
R1(config)#service pa
R1(config)#service password-encryption 
R1(config)#^Z
R1#
%SYS-5-CONFIG_I: Configured from console by console

R1#
R1#wr mem
Building configuration...
[OK]
```

### Настройте коммутатор  
```
Switch>
Switch>
Switch>
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#host S1
S1(config)#ena
S1(config)#enable sec
S1(config)#enable secret class
S1(config)#ban
S1(config)#banner m
S1(config)#banner motd *
Enter TEXT message.  End with the character '*'.
NO ENTRY*

S1(config)#line
S1(config)#line v
S1(config)#line vty 0 4
S1(config-line)#pas
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#exi
S1(config)#ser
S1(config)#service pa
S1(config)#service password-encryption 
S1(config)#line vty 0 4
S1(config-line)#tra
S1(config-line)#transport i
S1(config-line)#transport input all
S1(config-line)#exit
S1(config)#wr mem
           ^
% Invalid input detected at '^' marker.
	
S1(config)#
S1(config)#
S1(config)#
S1(config)#^Z
S1#
%SYS-5-CONFIG_I: Configured from console by console

S1#
S1#
S1#wr  me
Building configuration...
[OK]
S1#
%LINK-5-CHANGED: Interface FastEthernet0/5, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/5, changed state to up









S1 con0 is now available






Press RETURN to get started.












NO ENTRY
```
### Назначьте IPv6-адреса интерфейсам Ethernet на R1  
### Назначьте глобальные индивидуальные IPv6-адреса, указанные в таблице адресации обоим интерфейсам Ethernet на R1  
### Чтобы обеспечить соответствие локальных адресов канала индивидуальному адресу, вручную введите локальные адреса канала на каждом интерфейсе Ethernet на R1  

```
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#int g0/0/0
R1(config-if)#ipv
R1(config-if)#ipv6 ad
R1(config-if)#ipv6 address 2001:db8:acad:a::1/64
R1(config-if)#int g0/0/1
R1(config-if)#ipv
R1(config-if)#ipv6 ad
R1(config-if)#ipv6 address 2001:db8:acad:1::1/64
R1(config-if)#ipv6 ad
R1(config-if)#ipv6 address fe80::1 local
                                    ^
% Invalid input detected at '^' marker.
	
R1(config-if)#ipv6 address fe80::1 ?
  link-local  Use link-local address
R1(config-if)#ipv6 address fe80::1 lin
R1(config-if)#ipv6 address fe80::1 link-local 
R1(config-if)#int g0/0/0
R1(config-if)#ipv6 address fe80::1 link-local 
```
### Введите команду show ipv6 interface brief, чтобы проверить, назначен ли каждому интерфейсу корректный индивидуальный IPv6-адрес.
```
R1(config-if)#do show ip
R1(config-if)#do show ipv
R1(config-if)#do show ipv6 int br
GigabitEthernet0/0/0       [administratively down/down]
    FE80::1
    2001:DB8:ACAD:A::1
GigabitEthernet0/0/1       [administratively down/down]
    FE80::1
    2001:DB8:ACAD:1::1
Vlan1                      [administratively down/down]
    unassigned
R1(config-if)#int g0/0/0
R1(config-if)#no sh

R1(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0, changed state to up
int g0/0/1
R1(config-if)#no sh

R1(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up
```

### ⦁	Активируйте IPv6-маршрутизацию на R1  
В командной строке на PC-B введите команду ipconfig, чтобы получить данные IPv6-адреса, назначенного интерфейсу ПК  
```
C:\>ipconfig

FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: 
   Link-local IPv6 Address.........: FE80::210:11FF:FE39:D5AE
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0

Bluetooth Connection:

   Connection-specific DNS Suffix..: 
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0
```
Назначен ли индивидуальный IPv6-адрес сетевой интерфейсной карте (NIC) на PC-B? Нет  
### Активируйте IPv6-маршрутизацию на R1 с помощью команды IPv6 unicast-routing  

```
R1#
R1#ipv
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#ipv
R1(config)#ipv6 un
R1(config)#ipv6 unicast-routing 
R1(config)#
```
### Теперь, когда R1 входит в группу многоадресной рассылки всех маршрутизаторов, еще раз введите команду ipconfig на PC-B. Проверьте данные IPv6-адреса.
```
C:\>ipconfig

FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: 
   Link-local IPv6 Address.........: FE80::210:11FF:FE39:D5AE
   IPv6 Address....................: 2001:DB8:ACAD:A:210:11FF:FE39:D5AE
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: FE80::1
                                     0.0.0.0

Bluetooth Connection:

   Connection-specific DNS Suffix..: 
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
   ```
Почему PC-B получил глобальный префикс маршрутизации и идентификатор подсети, которые вы настроили на R1?  
```
R1#show ipv6 int g0/0/0
GigabitEthernet0/0/0 is up, line protocol is up
  IPv6 is enabled, link-local address is FE80::1
  No Virtual link-local address(es):
  Global unicast address(es):
    2001:DB8:ACAD:A::1, subnet is 2001:DB8:ACAD:A::/64
  Joined group address(es):
    FF02::1
    FF02::2
    FF02::1:FF00:1
```



### Назначьте IPv6-адреса интерфейсу управления (SVI) на S1.  
⦁	Назначьте адрес IPv6 для S1. Также назначьте этому интерфейсу локальный адрес канала.  
⦁	Проверьте правильность назначения IPv6-адресов интерфейсу управления с помощью команды show ipv6 interface vlan1.  

```
S1>
S1>
S1>en
Password: 
S1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)#int vlan1
S1(config-if)#ipv
S1(config-if)#ipv6 ad
S1(config-if)#ipv6 address 2001:db8:acad:1::b/64
S1(config-if)#ipv6 address fe80::1 l
S1(config-if)#ipv6 address fe80::1 link-local 
S1(config-if)#^Z
S1#
%SYS-5-CONFIG_I: Configured from console by console

S1#
S1#
S1#sh
S1#show ipv
S1#show ipv6 int vlan1
                     ^
% Invalid input detected at '^' marker.
	
S1#show ipv6 int vlan 1
Vlan1 is administratively down, line protocol is down
  IPv6 is tentative, link-local address is FE80::1 [TEN]
  No Virtual link-local address(es):
  Global unicast address(es):
    2001:DB8:ACAD:1::B, subnet is 2001:DB8:ACAD:1::/64 [TEN]
  Joined group address(es):
    FF02::1
  MTU is 1500 bytes
  ICMP error messages limited to one every 100 milliseconds
  ICMP redirects are enabled
  ICMP unreachables are sent
  Output features: Check hwidb
  ND DAD is enabled, number of DAD attempts: 1
  ND reachable time is 30000 milliseconds
S1#
S1#
S1#
S1#int vlan 1
       ^
% Invalid input detected at '^' marker.
	
S1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)#int vlan 1
S1(config-if)#no shut

S1(config-if)#
%LINK-5-CHANGED: Interface Vlan1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up









S1 con0 is now available






Press RETURN to get started.

```






### С PC-A отправьте эхо-запрос на FE80::1. Это локальный адрес канала, назначенный G0/1 на R1.  
```
C:\>ping FE80::1

Pinging FE80::1 with 32 bytes of data:

Reply from FE80::1: bytes=32 time<1ms TTL=255
Reply from FE80::1: bytes=32 time<1ms TTL=255
Reply from FE80::1: bytes=32 time=1ms TTL=255
Reply from FE80::1: bytes=32 time<1ms TTL=255

Ping statistics for FE80::1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 1ms, Average = 0ms
```

### ⦁	Введите команду tracert на PC-A, чтобы проверить наличие сквозного подключения к PC-B  
```
C:\>tracert 2001:db8:acad:a::3

Tracing route to 2001:db8:acad:a::3 over a maximum of 30 hops: 

  1   0 ms      0 ms      0 ms      2001:DB8:ACAD:1::1
  2   1 ms      0 ms      0 ms      2001:DB8:ACAD:A::3

Trace complete.

C:\>
C:\>
C:\>
```
### Отправьте эхо-запрос на интерфейс управления S1 с PC-A  
```
C:\>ping 2001:db8:acad:1::b

Pinging 2001:db8:acad:1::b with 32 bytes of data:

Reply from 2001:DB8:ACAD:1::B: bytes=32 time=2001ms TTL=255
Reply from 2001:DB8:ACAD:1::B: bytes=32 time<1ms TTL=255
Reply from 2001:DB8:ACAD:1::B: bytes=32 time<1ms TTL=255
Reply from 2001:DB8:ACAD:1::B: bytes=32 time<1ms TTL=255

Ping statistics for 2001:DB8:ACAD:1::B:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 2001ms, Average = 500ms

C:\>
```
### С PC-B отправьте эхо-запрос на PC-A.   

```
C:\>ping 2001:db8:acad:1::3

Pinging 2001:db8:acad:1::3 with 32 bytes of data:

Reply from 2001:DB8:ACAD:1::3: bytes=32 time<1ms TTL=127
Reply from 2001:DB8:ACAD:1::3: bytes=32 time<1ms TTL=127
Reply from 2001:DB8:ACAD:1::3: bytes=32 time<1ms TTL=127
Reply from 2001:DB8:ACAD:1::3: bytes=32 time<1ms TTL=127

Ping statistics for 2001:DB8:ACAD:1::3:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```
### С PC-B отправьте эхо-запрос на локальный адрес канала G0/0 на R1.
```
C:\>ping fe80::1

Pinging fe80::1 with 32 bytes of data:

Reply from FE80::1: bytes=32 time<1ms TTL=255
Reply from FE80::1: bytes=32 time<1ms TTL=255
Reply from FE80::1: bytes=32 time<1ms TTL=255
Reply from FE80::1: bytes=32 time<1ms TTL=255

Ping statistics for FE80::1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```
    

# Вопросы для повторения  
⦁	Почему обоим интерфейсам Ethernet на R1 можно назначить один и тот же локальный адрес канала — FE80::1? так как находятся в разных сетях  
⦁	Какой идентификатор подсети в индивидуальном IPv6-адресе 2001:db8:acad::aaaa:1234/64? aaaa:1234  



