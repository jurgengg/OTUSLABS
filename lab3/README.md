# Лабораторная №4 - View the Switch MAC Address Table  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab3/11.png) 
### Конфигурация коммутатора S1 
```
S1#show run
Building configuration...

Current configuration : 1344 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname S1
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
!
!
!
ip ssh version 2
ip domain-name otus.ru
!
username jurgengg secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
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
 ip address 192.168.1.11 255.255.255.0
!
ip default-gateway 192.168.1.1
!
banner motd ^CNO ENTRY^C
!
!
!
line con 0
!
line vty 0 4
 password 7 0822455D0A16
 login local
 transport input ssh
line vty 5 15
 login
!
!
!
!
end
```
###	Настройка основных параметров устройств  

⦁	Создайте сеть согласно топологии.  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab3/34.png)  
⦁	Настройте маршрутизатор.  
### Конфигурация маршрутизатора R1  
```
R1#sh run
Building configuration...

Current configuration : 763 bytes
!
version 15.4
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname R1
!
!
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
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
username jurgengg secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
!
!
!
!
!
!
!
!
ip ssh version 2
ip domain-name otus.ru
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0/0
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface GigabitEthernet0/0/1
 ip address 192.168.1.1 255.255.255.0
 duplex auto
 speed auto
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
!
ip flow-export version 9
!
!
!
banner motd ^C
^C
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 password 7 0822404F1A0A
 login local
!
!
!
end
```
###	Настройте компьютер PC-A.  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab3/6.png)  
⦁	Проверьте подключение к сети  

```
Pinging 192.168.1.1 with 32 bytes of data:

Reply from 192.168.1.1: bytes=32 time<1ms TTL=255
Reply from 192.168.1.1: bytes=32 time<1ms TTL=255
Reply from 192.168.1.1: bytes=32 time<1ms TTL=255
Reply from 192.168.1.1: bytes=32 time<1ms TTL=255

Ping statistics for 192.168.1.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
    ```
    
    ###⦁	Настройка маршрутизатора для доступа по протоколу SSH  
    
    ```
    R1(config)#ip domain-name otus.ru
R1(config)#cry
R1(config)#crypto ke
R1(config)#crypto key ge
R1(config)#crypto key generate rsa
The name for the keys will be: R1.otus.ru
Choose the size of the key modulus in the range of 360 to 2048 for your
  General Purpose Keys. Choosing a key modulus greater than 512 may take
  a few minutes.

How many bits in the modulus [512]: 1024
% Generating 1024 bit RSA keys, keys will be non-exportable...[OK]

R1(config)#ip ssh ver
*Mar 1 0:13:52.748: %SSH-5-ENABLED: SSH 1.99 has been enabled
R1(config)#ip ssh version 2
R1(config)#use
R1(config)#username jurgengg secret class
R1(config)#line
R1(config)#line vty 0 4
R1(config-line)#lo
R1(config-line)#login
R1(config-line)#login loc
R1(config-line)#login local 
R1(config-line)#exit
R1(config)#tr
R1(config)#line vty 0 4
R1(config-line)#tra
R1(config-line)#transport in
R1(config-line)#transport input all
```


### ⦁	Установите соединение с маршрутизатором по протоколу SSH.  



```
C:\>ssh -l jurgengg 192.168.1.1

Password: 




R1>en
Password: 
Password: 
Password: 
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#
```
