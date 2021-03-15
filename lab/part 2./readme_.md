# Шаг 1. Настройка базовых параметров сетевых устройств
*=) Настройка времени*
Проверка времени которая сейчас установлено:
``` Switch>en
Switch#show cl
*1:6:5.589 UTC Mon Mar 1 1993
Switch#
```
Установка новой даты
``` Switch>en
Switch#show cl
*1:6:5.589 UTC Mon Mar 1 1993
Switch#cloc
Switch#clock set 16:25:30 15 March 2021
Switch#Show cl
16:25:37.437 UTC Mon Mar 15 2021
Switch# 
```
**a)** Параметры конфигурации
Переименование устройства
``` 
Switch#conf t
Enter configuration commands, one per line  End with CNTL/Z
Switch(config)#hostname S1 
S1(config)# 
```

Выключаем разрешения имен
``` 
S1(config)#no ip dom
S1(config)#no ip domain
S1(config)#no ip domain-loo
S1(config)#no ip domain-lookup 
S1(config)# 
```

Назначаем пароль

```S1>en
S1#
S1#
S1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)#li
S1(config)#line con
S1(config)#line console 0
S1(config-line)#ena
S1(config-line)#pass
S1(config-line)#password cisco
S1(config-line)#lo
S1(config-line)#logi
S1(config-line)#login 
S1(config-line)# 
```

``` 
Press RETURN to get started!
User Access Verification
Password:
```

 ``` 
 line con 0
 password 7 0822455D0A16
 login 
 ```

Пароль привилегированного режима

``` 
line con 0
 password 7 0822455D0A16
 login 
 ```

``` 
S1>ena
Password: 
  ```

``` 
hostname S1
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0 
```

Баннер

``` 
S1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)# ban
S1(config)# banner mot
S1(config)# banner motd #Unauthorized access is strictly prohibited.#
S1(config
```

```  
Unauthorized access is strictly prohibited.
User Access Verification
Password: 
  ```
*b)* Назначьте IP-адрес интерфейсу SVI на коммутаторе.

``` S1(config)#int
S1(config)#interface v
S1(config)#interface vlan 1
S1(config-if)#ip
S1(config-if)#ip add
S1(config-if)#ip address 192.168.1.20 255.255.255.0
S1(config-if)#no sh
S1(config-if)#no shutdown 
S1(config-if)#
%LINK-5-CHANGED: Interface Vlan1, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up
  ```
*c)*   

``` 
S1#line con
S1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)# line con
S1(config)# line console 0
S1(config-line)#line vty 0 15
S1(config-line)#pass
S1(config-line)#password cisco
S1(config-line)#log
S1(config-line)#log
S1(config-line)#login
S1(config-line)#tran
S1(config-line)#transport inp
S1(config-line)#transport input {ss
S1(config-line)#transport input {ssh | telet}
                                ^
% Invalid input detected at '^' marker.
	
S1(config-line)#transport input {ssh | telet}
                                ^
% Invalid input detected at '^' marker.
	
S1(config-line)#transport input ssh
S1(config-line)#transport input telnet
S1(config-line)#disa
S1(config-line)#disa
                 ^
% Invalid input detected at '^' marker.
	
S1(config-line)#exit
S1(config-line)#exit 
 ```
## Шаг 2. Настройте IP-адрес на компьютере PC-A.
Картинка
