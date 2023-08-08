# Configure_NAT_for_IPv4
![](https://github.com/jurgengg/OTUSLABS/blob/main/NAT/hj.png)  
### ⦁	Произведите базовую настройку маршрутизаторов.

```
router(config)# hostname R1
R1(config)# no ip domain-lookup
R1(config)# enable secret class
R1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# line vty 0 4
R1(config-line)# password cisco
R1(config-line)# login
R1(config)# service password-encryption
R1(config)# banner motd $ Authorized Users Only! $
R1(config)# interface g0/0/0
R1(config-if)# ip address 209.165.200.230 255.255.255.248
R1(config-if)# no shutdown
R1(config-if)# interface g0/0/1
R1(config-if)# ip address 192.168.1.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)# ip route 0.0.0.0 0.0.0.0 209.165.200.225
R1(config)# exit
R1# copy running-config startup-config
```
### ⦁	Настройте базовые параметры каждого коммутатора
```
switch(config)# hostname S1
S1(config)# no ip domain-lookup
S1(config)# enable secret class
S1(config)# line console 0
S1(config-line)# password cisco
S1(config-line)# login
S1(config)# line vty 0 15
S1(config-line)# password cisco
S1(config-line)# login
S1(config)# service password-encryption
S1(config)# banner motd $ Authorized Users Only! $
S1(config)# interface range f0/2-4, f0/6-24, g0/1-2
S1(config-if-range)# shutdown
S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.1.12 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# exit
S1(config)# ip default-gateway 192.168.1.1
S1(config-if-range)# exit
S1# copy running-config startup-config
```

## Настройте NAT на R1, используя пул из трех адресов 209.165.200.226-209.165.200.228
```
R1(config)# access-list 1 permit 192.168.1.0 0.0.0.255
R1(config)# ip nat pool PUBLIC_ACCESS 209.165.200.226 209.165.200.228 netmask 255.255.255.248
R1(config)# ip nat inside source list 1 pool PUBLIC_ACCESS
R1(config)# interface g0/0/1
R1(config-if)# ip nat inside
R1(config)# interface g0/0/0
R1(config-if)# ip nat outside
```
## ⦁	Проверьте и проверьте конфигурацию
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
---  209.165.200.226       192.168.1.3           ---                   ---
icmp 209.165.200.226:1     192.168.1.3:1         209.165.200.1:1       209.165.200.1:1
Total number of translations: 2
```
Во что был транслирован внутренний локальный адрес PC-B? 209.165.200.226
Какой тип адреса NAT является переведенным адресом? Inside Global
### На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
---  209.165.200.227       192.168.1.2           ---                   ---
---  209.165.200.226       192.168.1.3           ---                   ---
icmp 209.165.200.227:1     192.168.1.2:1         209.165.200.1:1       209.165.200.1:1
icmp 209.165.200.226:1     192.168.1.3:1         209.165.200.1:1       209.165.200.1:1
Total number of translations: 4
```
⦁	Обратите внимание, что предыдущая трансляция для PC-B все еще находится в таблице. Из S1, эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. Если эхо-запрос не прошел, выполните отладку. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
---  209.165.200.227       192.168.1.2           ---                   ---
---  209.165.200.226       192.168.1.3           ---                   ---
---  209.165.200.228       192.168.1.11          ---                   ---
icmp 209.165.200.226:1     192.168.1.3:1         209.165.200.1:1       209.165.200.1:1
icmp 209.165.200.228:0     192.168.1.11:0        209.165.200.1:0       209.165.200.1:0
Total number of translations: 5
```
⦁	Теперь запускаем пинг R2 Lo1 из S2. На этот раз перевод завершается неудачей, и вы получаете эти сообщения (или аналогичные) на консоли R1:
Sep 23 15:43:55.562: %IOSXE-6-PLATFORM: R0/0: cpp_cp: QFP:0.0 Thread:000 TS:00000001473688385900 %NAT-6-ADDR_ALLOC_FAILURE: Address allocation failed; pool 1 may be exhausted [2]
⦁	Это ожидаемый результат, потому что выделено только 3 адреса, и мы попытались ping Lo1 с четырех устройств. Напомним, что NAT — это трансляция «один-в-один». Как много выделено трансляций? Введите команду show ip nat translations verbose , и вы увидите, что ответ будет 24 часа.
```
R1# show ip nat translations verbose
Pro  Inside global         Inside local          Outside local         Outside global
---  209.165.200.226       192.168.1.3           ---                   ---
  create: 08/08/23 14:35:27, use: 08/09/23 14:35:27, timeout: 23:56:42
  Map-Id(In): 1
<output omitted>
```
⦁	Учитывая, что пул ограничен тремя адресами, NAT для пула адресов недостаточно для нашего приложения. Очистите преобразование NAT и статистику, и мы перейдем к PAT.
```
R1# clear ip nat translations *
R1# clear ip nat statistics
```
## ⦁	Настройка и проверка PAT для IPv4.
```
R1(config)# no ip nat inside source list 1 pool PUBLIC_ACCESS
R1(config)# ip nat inside source list 1 pool PUBLIC_ACCESS overload
```
⦁	Давайте проверим, что PAT работает. С PC-B,  запустите эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. Если эхо-запрос не прошел, выполните отладку. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
icmp 209.165.200.226:1     192.168.1.3:1         209.165.200.1:1       209.165.200.1:1
Total number of translations: 1#
```
Во что был транслирован внутренний локальный адрес PC-B? 209.165.200.226
 Какой тип адреса NAT является переведенным адресом? Inside Global
 Чем отличаются выходные данные команды show ip nat translations из упражнения NAT? Специального перевода между внутренним и внешним адресом в списке нет.
### ⦁	С PC-A, запустите эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. Если эхо-запрос не прошел, выполните отладку. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
icmp 209.165.200.226:1     192.168.1.2:1         209.165.200.1:1       209.165.200.1:1
Total number of translations: 1
```
### Обратите внимание, что есть только одна трансляция. Отправьте ping еще раз, и быстро вернитесь к маршрутизатору и введите команду show ip nat translations verbose , и вы увидите, что произошло
```
R1# show ip nat translations verbose
Pro  Inside global         Inside local          Outside local         Outside global
icmp 209.165.200.226:1     192.168.1.2:1         209.165.200.1:1       209.165.200.1:1
  create: 08/08/23 14:57:22, use: 08/08/23 16:57:25, timeout: 00:01:00
<output omitted>
```
### ⦁	Генерирует трафик с нескольких устройств для наблюдения PAT. На PC-A и PC-B используйте параметр -t с командой ping, чтобы отправить безостановочный ping на интерфейс Lo1 R2 (ping -t 209.165.200.1), затем вернитесь к R1 и выполните команду show ip nat translations:
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
icmp 209.165.200.226:1     192.168.1.2:1         209.165.200.1:1       209.165.200.1:1
icmp 209.165.200.226:2     192.168.1.3:1         209.165.200.1:1       209.165.200.1:2
Total number of translations: 2
```
Как маршрутизатор отслеживает, куда идут ответы?  Присваиваются уникальные номера портов.
### ⦁	PAT в пул является очень эффективным решением для малых и средних организаций. Тем не менее есть неиспользуемые адреса IPv4, задействованные в этом сценарии. Мы перейдем к PAT с перегрузкой интерфейса, чтобы устранить эту трату IPv4 адресов. Остановите ping на PC-A и PC-B с помощью комбинации клавиш Control-C, затем очистите трансляции и статистику:

```
R1# clear ip nat translations *
R1# clear ip nat statistics
```
## ⦁	На R1 удалите команды преобразования nat pool
```
R1(config)# no ip nat inside source list 1 pool PUBLIC_ACCESS overload
R1(config)# no ip nat pool PUBLIC_ACCESS
```
## ⦁	Добавьте команду PAT overload, указав внешний интерфейс.
```
R1(config)# ip nat inside source list 1 interface g0/0/0 overload
```
## ⦁	Протестируйте и проверьте конфигурацию. 
⦁	Давайте проверим PAT, чтобы интерфейс работал. С PC-B,  запустите эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. Если эхо-запрос не прошел, выполните отладку. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
icmp 209.165.200.230:1     192.168.1.3:1         209.165.200.1:1       209.165.200.1:1
Total number of translations: 1
```

⦁	Сделайте трафик с нескольких устройств для наблюдения PAT. На PC-A и PC-B используйте параметр -t с командой ping для отправки безостановочного ping на интерфейс Lo1 R2 (ping -t 209.165.200.1). На S1 и S2 выполните привилегированную команду exec ping 209.165.200.1 повторить 2000. Затем вернитесь к R1 и выполните команду show ip nat translations.

```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
icmp 209.165.200.230:3     192.168.1.11:1        209.165.200.1:1       209.165.200.1:3
icmp 209.165.200.230:2     192.168.1.2:1         209.165.200.1:1       209.165.200.1:2
icmp 209.165.200.230:4     192.168.1.3:1         209.165.200.1:1       209.165.200.1:4
icmp 209.165.200.230:1     192.168.1.12:1        209.165.200.1:1       209.165.200.1:1
Total number of translations: 4
```
## Настройка и проверка статического NAT для IPv4.
```
R1# clear ip nat translations *
R1# clear ip nat statistics
```
```
R1(config)# ip nat inside source static 192.168.1.2 209.165.200.229
```
## ⦁	Протестируйте и проверьте конфигурацию.
⦁	Давайте проверим, что статический NAT работает. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations, и вы увидите статическое сопоставление.
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
---  209.165.200.229       192.168.1.2           ---                   ---
Total number of translations: 1
```
⦁	На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations, и вы увидите статическое сопоставление и преобразование на уровне порта для входящих pings
```
R1# show ip nat translations
Pro  Inside global         Inside local          Outside local         Outside global
---  209.165.200.229       192.168.1.2           ---                   ---
icmp 209.165.200.229:3     192.168.1.2:3         209.165.200.225:3     209.165.200.225:3
Total number of translations: 2
```







