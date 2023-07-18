### Произведите базовую настройку маршрутизаторов  

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
### Настройте базовые параметры каждого коммутатора  


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
## Настройте адреса интерфейса и базового OSPFv2 на каждом маршрутизаторе  
### Настройте адреса интерфейсов на каждом маршрутизаторе, как показано в таблице адресации выше  

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

⦁	Перейдите в режим конфигурации маршрутизатора OSPF, используя идентификатор процесса 56.  
⦁	Настройте статический идентификатор маршрутизатора для каждого маршрутизатора (1.1.1.1 для R1, 2.2.2.2 для R2).  
⦁	Настройте инструкцию сети для сети между R1 и R2, поместив ее в область 0.  

```
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
### Только на R2 добавьте конфигурацию, необходимую для объявления сети Loopback 1 в область OSPF 0.  
```
R2(config)#router ospf 56
R2(config-router)#int lo
R2(config-router)#int loo
R2(config-router)#int loopback 1
R2(config-if)#ip os
R2(config-if)#ip ospf 56 area 0
```
### Убедитесь, что OSPFv2 работает между маршрутизаторами. Выполните команду, чтобы убедиться, что R1 и R2 сформировали смежность.  

```
R1# show ip ospf neighbor
Neighbor ID     Pri   State           Dead Time   Address         Interface
2.2.2.2           1   FULL/DR         00:00:33    10.53.0.2       GigabitEthernet0/0/1

R2# show ip ospf neighbor

Neighbor ID     Pri   State           Dead Time   Address         Interface
1.1.1.1           1   FULL/BDR        00:00:37    10.53.0.1       GigabitEthernet0/0/1
```
⦁	Какой маршрутизатор является DR? Какой маршрутизатор является BDR? Каковы критерии отбора?
Маршрутизатор R1 был настроен первым и начал использовать OSPF перед маршрутизатором R2. Таким образом, во время выборов OSPF только маршрутизатор R1 был настроен для OSPF и стал DR. После того, как R2 был настроен для OSPF, он стал BDR.
Маршрутизатор с наивысшим идентификатором маршрутизатора используется при выборе DR и BDR.  
⦁	На R1 выполните команду show ip route ospf, чтобы убедиться, что сеть R2 Loopback1 присутствует в таблице маршрутизации
```
R1# show ip route ospf
<output omitted>
Gateway of last resort is not set
      192.168.1.0/32 is subnetted, 1 subnets
O        192.168.1.1 [110/2] via 10.53.0.2, 00:03:12, GigabitEthernet0/0/1
```

⦁	Запустите Ping до  адреса интерфейса R2 Loopback 1 из R1. Выполнение команды ping должно быть успешным.

```
R1# ping 192.168.1.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
```

⦁	На R1 настройте приоритет OSPF интерфейса G0/0/1 на 50, чтобы убедиться, что R1 является назначенным маршрутизатором.
```
R1(config)# interface g0/0/1
R1(config-if)# ip ospf priority 50
```

⦁	Настройте таймеры OSPF на G0/0/1 каждого маршрутизатора для таймера приветствия, составляющего 30 секунд.

```
(config)# interface g0/0/1
R1(config-if)# ip ospf hello-interval 30

R2(config)# interface g0/0/1
R1(config-if)# ip ospf hello-interval 30
```
⦁	На R1 настройте статический маршрут по умолчанию, который использует интерфейс Loopback 1 в качестве интерфейса выхода. Затем распространите маршрут по умолчанию в OSPF. Обратите внимание на сообщение консоли после установки маршрута по умолчанию.

```
R1(config)# ip route 0.0.0.0 0.0.0.0 loopack 1
%Default route without gateway, if not a point-to-point interface, may impact performance
R1(config)# router ospf 56
R1(config-router)# default-information originate
```


⦁	добавьте конфигурацию, необходимую для OSPF для обработки R2 Loopback 1 как сети точка-точка. Это приводит к тому, что OSPF объявляет Loopback 1 использует маску подсети интерфейса
```
R2(config)# interface loopback 1
R2(config-if)# ip ospf network point-to-point
R2(config-if)# exit
```
⦁	Только на R2 добавьте конфигурацию, необходимую для предотвращения отправки объявлений OSPF в сеть Loopback 1.
```
R2(config)# router ospf 56
R2(config-router)# passive-interface loopback 1
R2(config-router)# exit
```

⦁	Измените базовую пропускную способность для маршрутизаторов. После этой настройки перезапустите OSPF с помощью команды clear ip ospf process . Обратите внимание на сообщение консоли после установки новой опорной полосы пропускания.
```
R1(config)# router ospf 56
R1(config-router)# auto-cost reference-bandwidth 1000
%OSPF: Reference bandwidth is changed.
Please ensure reference bandwidth is consistent across all routers.
R1(config-router)# end
R1# clear ip ospf process
Reset ALL OSPF processes? [no]: yes

R2(config)# router ospf 56
R2(config-router)# auto-cost reference-bandwidth 1000
%OSPF: Reference bandwidth is changed.
Please ensure reference bandwidth is consistent across all routers.
R2(config-router)# end
R2# clear ip ospf process
Reset ALL OSPF processes? [no]: yes
```

⦁	Выполните команду show ip ospf interface g0/0/1 на R1 и убедитесь, что приоритет интерфейса установлен равным 50, а временные интервалы — Hello 30, Dead 120, а тип сети по умолчанию — Broadcast
```
R1# show ip ospf interface g0/0/1
GigabitEthernet0/0/1 is up, line protocol is up
  Internet Address 10.53.0.1/24, Interface ID 7, Area 0
  Attached via Network Statement
  Process ID 56, Router ID 1.1.1.1, Network Type BROADCAST, Cost: 10
  Topology-MTID    Cost    Disabled    Shutdown      Topology Name
        0           10        no          no            Base
  Transmit Delay is 1 sec, State DR, Priority 50
  Designated Router (ID) 1.1.1.1, Interface address 10.53.0.1
  Backup Designated router (ID) 2.2.2.2, Interface address 10.53.0.2
  Timer intervals configured, Hello 30, Dead 120, Wait 120, Retransmit 5
    oob-resync timeout 120
    Hello due in 00:00:09
  Supports Link-local Signaling (LLS)
  Cisco NSF helper support enabled
  IETF NSF helper support enabled
  Index 1/1/1, flood queue length 0
  Next 0x0(0)/0x0(0)/0x0(0)
  Last flood scan length is 1, maximum is 1
  Last flood scan time is 0 msec, maximum is 0 msec
  Neighbor Count is 1, Adjacent neighbor count is 1
    Adjacent with neighbor 2.2.2.2  (Backup Designated Router)
  Suppress hello for 0 neighbor(s)
```
⦁	На R1 выполните команду show ip route ospf, чтобы убедиться, что сеть R2 Loopback1 присутствует в таблице маршрутизации. Обратите внимание на разницу в метрике между этим выходным и предыдущим выходным. Также обратите внимание, что маска теперь составляет 24 бита, в отличие от 32 битов, ранее объявленных.
```
R1# show ip route ospf
<output omitted>
Gateway of last resort is 0.0.0.0 to network 0.0.0.0
O     192.168.1.0/24 [110/11] via 10.53.0.2, 00:03:11, GigabitEthernet0/0/1
```

⦁	Введите команду show ip route ospf на маршрутизаторе R2. Единственная информация о маршруте OSPF должна быть распространяемый по умолчанию маршрут R1.
```
R2# show ip route ospf
<output omitted>
Gateway of last resort is 10.53.0.1 to network 0.0.0.0
O*E2  0.0.0.0/0 [110/1] via 10.53.0.1, 00:08:01, GigabitEthernet0/0/1
```

⦁	Запустите Ping до адреса интерфейса R1 Loopback 1 из R2. Выполнение команды ping должно быть успешным.
```
R2# ping 172.16.1.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.16.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
```
Почему стоимость OSPF для маршрута по умолчанию отличается от стоимости OSPF в R1 для сети 192.168.1.0/24?
Статическому маршруту по умолчанию, импортированному в OSPF, по умолчанию присваивается тип метрики «E2» или внешний тип 2. «E2» по умолчанию поддерживает одинаковую стоимость OSPF во всей сети OSPF. В этом случае метрика для маршрута по умолчанию была равна 1, поэтому везде в сети OSPF 56 он имеет метрику 1. Сеть 192.168.1.0/24 — это внутренний маршрут OSPF, метрика которого является кумулятивной.
