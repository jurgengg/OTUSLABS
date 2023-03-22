# Лабораторная №2 - View the Switch MAC Address Table  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_12.png)    
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_13.png)  
### Конфигурация коммутатора S1  
```
S1#sh run
Building configuration...

Current configuration : 1217 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname S1
!
enable secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
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
!
!
!
line con 0
 password 7 0822455D0A16
 login
!
line vty 0 4
 password 7 0822455D0A16
 login
 transport input telnet
line vty 5 15
 login
!
!
!
!
end
```
### Конфигурация коммутатора S2  
```
S2#sh run
Building configuration...

Current configuration : 1193 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname S2
!
enable secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
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
 ip address 192.168.1.12 255.255.255.0
!
!
!
!
line con 0
 password 7 0822455D0A16
 login
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 login
!
!
!
!
end
```
### ⦁	Запишите МАС-адреса сетевых устройств.
Назовите физические адреса адаптера Ethernet  
MAC адреса в строчке Physical Address  
ПК PC-A  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_1.png)  
ПК PC-B  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_2.png)   
⦁	МАС-адрес коммутатора S1 Fast Ethernet 0/1:  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_5.png)  
МАС-адрес коммутатора S2 Fast Ethernet 0/1:  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_4.png)  
### ⦁	Просмотрите таблицу МАС-адресов коммутатора.  
Подключитесь к коммутатору S2 через консоль и просмотрите таблицу МАС-адресов до и после тестирования сетевой связи с помощью эхо-запросов.  
ДО:  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_6.png)  
Записаны ли в таблице МАС-адресов какие-либо МАС-адреса? Какие МАС-адреса записаны в таблице? С какими портами коммутатора они сопоставлены и каким устройствам принадлежат? Да, 2 mac адреса: для Vlan 1 и интервейса fa0/1 коммутатора S1  
После:  
```
S2#sh mac 
S2#sh mac address-table 
          Mac Address Table
-------------------------------------------

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----

   1    0001.43b3.b877    DYNAMIC     Fa0/1
   1    0009.7c1e.7601    DYNAMIC     Fa0/1
   1    000a.41d0.57d2    DYNAMIC     Fa0/1
   1    0060.70a3.3625    DYNAMIC     Fa0/18
   ```  
  ### После отправки ping - Появляются еще и записи о ПК в сети
Если вы не записали МАС-адреса сетевых устройств в шаге 1, как можно определить, каким устройствам принадлежат МАС-адреса, используя только выходные данные команды show mac address-table? Можно, так как есть привязка к портам и мы знаем какие утсройства к ним подклчены  .  
Работает ли это решение в любой ситуации? Нет, если у нас стоит несколько коммутаторов подряд, т.е. мы будем видеть несколько MAC адресов за 1 портом.  
### ⦁	Очистите таблицу МАС-адресов коммутатора S2 и снова отобразите таблицу МАС-адресов.  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_3.png)  
⦁	Снова быстро введите команду show mac address-table.  
### Вопросы:  
Указаны ли в таблице МАС-адресов адреса для VLAN 1? Указаны ли другие МАС-адреса? Нет, таблица пуста.  
Через 10 секунд введите команду show mac address-table и нажмите клавишу ввода. Появились ли в таблице МАС-адресов новые адреса?  Да, MAC адрес порта fa0/1 коммутатора S1 . Для Vlan 1 -нет  
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_7.png)  
### ⦁	С компьютера PC-B отправьте эхо-запросы устройствам в сети и просмотрите таблицу МАС-адресов коммутатора.
Вопрос:
Не считая адресов многоадресной и широковещательной рассылки, сколько пар IP- и МАС-адресов устройств было получено через протокол ARP?  3 пары, т.е. 3 других устройства  
```
C:\>arp -a
  Internet Address      Physical Address      Type
  192.168.1.1           0001.43b3.b877        dynamic
  192.168.1.11          000a.41d0.57d2        dynamic
  192.168.1.12          0004.9a19.8c80        dynamic
  ```  
  ⦁	Из командной строки PC-B отправьте эхо-запросы на компьютер PC-A, а также коммутаторы S1 и S2.  
Вопрос:  
От всех ли устройств получены ответы? Да!  
### Подключившись через консоль к коммутатору S2, введите команду show mac address-table.  
Вопрос:  
Добавил ли коммутатор в таблицу МАС-адресов дополнительные МАС-адреса? Если да, то какие адреса и устройства?  Да
![](https://github.com/jurgengg/OTUSLABS/blob/main/lab2/Screenshot_10.png)  
⦁	На компьютере PC-B откройте командную строку и еще раз введите команду arp -a.  
Вопрос:  
⦁	Появились ли в ARP-кэше компьютера PC-B дополнительные записи для всех сетевых устройств, которым были отправлены эхо-запросы? Да, все устройства  
## Вопрос для повторения  
В сетях Ethernet данные передаются на устройства по соответствующим МАС-адресам. Для этого коммутаторы и компьютеры динамически создают ARP-кэш и таблицы МАС-адресов. Если компьютеров в сети немного, эта процедура выглядит достаточно простой. Какие сложности могут возникнуть в крупных сетях? Broadcast рассылки ARP могут вызвать широковещательный шторм. Можно подделать устройство в сети, т.к. нет аутентификации и проверки на соответсвие IP адреса MAC адресу (ARP Spoofing)


  




