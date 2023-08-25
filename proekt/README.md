### Курс Network engineer. Basic
### Тема проекта: Проектирование сети организации с использованием технологий динамической маршрутизации, резервированием и безопасности 
### Автор: Башаев Юрий

Цели проекта:  
В качестве цели проекта была выбрано создать с нуля сеть небольшой организации "Карта мира", которая имеет несколько удаленных друг от друга филиалов.  
Задачами к проектированию сети ставилось обеспечить: Создание VLAN`ов для каждого отдела организации, Обеспечение защиты от сетевых атак, Настройка динамической маршрутизации, Настройка динамической выдачи IP адресов  
Для реализации были выбраны следующие технологии:  OSPF, Spanning Tree Protocol, NAT, VLAN, Port Security,DHCP  
## Разработанная схема локальной сети организации:  

Начинаем с базовой настройки каждого коммутатора
```
switch(config)# hostname S1
S1(config)# no ip domain-lookup
S1(config)# enable secret class
S1(config)# line console 0
S1(config-line)# password cisco
S1(config-line)# login
S1(config)# line vty 0 4
S1(config-line)# password cisco
S1(config-line)# login
S1(config)# service password-encryption
S1(config)# banner motd $ Authorized Users Only! $
S1(config)# exit
S1# copy running-config startup-config
```

Далее базовая настройка каждого маршрутизатора:
```
router(config)# hostname R1
router(config)# hostname R1
R1(config)# enable secret class
R1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# line vty 0 4
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# service password-encryption
R1(config)# banner motd $ Authorized Users Only! $
R1# copy running-config startup-config
```
Создадим необходимые VLAN и распеделим порты на коммутаторе S1
```
S1(config-vlan)#vlan 10
S1(config-vlan)#name Sales
S1(config-vlan)#vlan 20
S1(config-vlan)#name Operations
S1(config-vlan)#vlan 999
S1(config-vlan)#name Parking_lot
S1(config-if-range)#int fa0/5
S1(config-if)#switchport mode access 
S1(config-if)#switchport access vlan 10
S1(config-if-range)#int range fa0/6-7
S1(config-if)#switchport mode access 
S1(config-if)#switchport access vlan 20
S1(config)#int range f0/8-24, gi0/1-2
S1(config-if-range)#switchport mode access 
S1(config-if-range)#switchport access vlan 999
S1(config-if-range)#shutdown 
```
Создадим необходимые VLAN и распеделим порты на коммутаторе S2
```
S2(config-vlan)#vlan 10
S2(config-vlan)#name Sales
S2(config-vlan)#vlan 20
S2(config-vlan)#name Operations
S2(config-vlan)#vlan 999
S2(config-vlan)#name Parking_lot
S2(config-if-range)#int fa0/6
S2(config-if)#switchport mode access 
S2(config-if)#switchport access vlan 20
S2(config-if-range)#int range fa0/5, fa0/7
S2(config-if)#switchport mode access 
S2(config-if)#switchport access vlan 10
S2(config)#int range f0/8-24, gi0/1-2
S2(config-if-range)#switchport mode access 
S2(config-if-range)#switchport access vlan 999
S2(config-if-range)#shutdown 
```


### Выводы и планы по развитию: В дальнейшем планируется организовать сеть провайдера с помощью технологии MPLS, В каждой офисе компании реализовать 3-х уровневую сетевую архитектуру, Развернуть VOIP SIP сервер в офисах компании.






