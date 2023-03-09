# Lab_Basic_Switch_Configuration

- ##	Задачи
- Часть 1. Проверка конфигурации коммутатора по умолчанию
- Часть 2. Создание сети и настройка основных параметров устройства
- Настройте базовые параметры коммутатора.
- 	Настройте IP-адрес для ПК.
- Часть 3. Проверка сетевых подключений
- 	Отобразите конфигурацию устройства.
- Протестируйте сквозное соединение, отправив эхо-запрос.
- Протестируйте возможности удаленного управления с помощью Telnet.



Часть 1. Проверка конфигурации коммутатора по умолчанию
```
Switch#show  running-config 
Building configuration...

Current configuration : 1080 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
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
 no ip address
 shutdown
!
!
!
!
line con 0
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end
```
### Изучите текущий файл running configuration  
Вопросы:  
Сколько интерфейсов FastEthernet имеется на коммутаторе 2960? - **24**  
Сколько интерфейсов Gigabit Ethernet имеется на коммутаторе 2960? - **2**  
Каков диапазон значений, отображаемых в vty-линиях? **line vty 0 4 line vty 5 15**  
### Изучите файл загрузочной конфигурации (startup configuration), который содержится в энергонезависимом ОЗУ (NVRAM).  
```
Switch# show startup-config
startup-config is not present
```
Почему появляется это сообщение? **Так как конфигурация еще не задана**  
### Изучите характеристики SVI для VLAN 1.
```
Switch# show interface vlan1
```
Назначен ли IP-адрес сети VLAN 1? - **Нет**  
Данный интерфейс включен?
``` Vlan1 is administratively down, line protocol is down ```   
  Какой MAC-адрес имеет SVI?  
  ``` Hardware is CPU Interface, address is 0009.7ce5.0d30 (bia 0009.7ce5.0d30)  ```  
  ### Изучите IP-свойства интерфейса SVI сети VLAN 1.  
```  
Switch#sh ip int vlan 1
Vlan1 is administratively down, line protocol is down
  Internet protocol processing disable 
```  
  ### Изучите сведения о версии ОС Cisco IOS на коммутаторе.  
  Под управлением какой версии ОС Cisco IOS работает коммутатор?  
![](https://github.com/jurgengg/OTUSLABS/blob/main/Screenshot_7.png)  
Как называется файл образа системы?  
![](https://github.com/jurgengg/OTUSLABS/blob/main/Screenshot_9.png)  
Какой базовый MAC-адрес назначен коммутатору?  
![](https://github.com/jurgengg/OTUSLABS/blob/main/Screenshot_8.png)  
### Изучите свойства по умолчанию интерфейса FastEthernet, который используется компьютером PC-A.

  Интерфейс включен или выключен? - **FastEthernet0/6 is up, line protocol is up (connected)**  
Что нужно сделать, чтобы включить интерфейс? - **no shutdown**  
Какой MAC-адрес у интерфейса? **Hardware is Lance, address is 000a.4141.0506 (bia 000a.4141.0506)** 
Какие настройки скорости и дуплекса заданы в интерфейсе? - **Full-duplex, 100Mb/s**  
### Изучите параметры сети VLAN по умолчанию на коммутаторе.
Какое имя присвоено сети VLAN 1 по умолчанию?  
![](https://github.com/jurgengg/OTUSLABS/blob/main/Screenshot_13.png)  
Какие порты расположены в сети VLAN 1?  
![](https://github.com/jurgengg/OTUSLABS/blob/main/Screenshot_12.png)  
Активна ли сеть VLAN 1?!  
К какому типу сетей VLAN принадлежит VLAN по умолчанию?  
![](https://github.com/jurgengg/OTUSLABS/blob/main/Screenshot_14.png) 

