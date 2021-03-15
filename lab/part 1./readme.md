# Шаг 1. Создайте сеть согласно топологии.
https://github.com/Dr-Krot/HW_01/blob/main/lab/image/step%201.png
*`Примечание:` При использовании Netlab отключите интерфейс F0/6*
Команды *(водимые мною)*: 
```Switch>en
Switch>enable 
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#i
Switch(config)#in
Switch(config)#interface f
Switch(config)#interface fastEthernet 0?
/  
Switch(config)#interface fastEthernet 0/6
Switch(config-if)#sh
Switch(config-if)#shutdown 
 
%LINK-5-CHANGED: Interface FastEthernet0/6, changed state to administratively down
Switch(config-if)#^Z
Switch#
%SYS-5-CONFIG_I: Configured from console by console
^Z
Switch#sho
Switch#show f0/6
             ^
% Invalid input detected at '^' marker.
	
Switch#show i
Switch#show int
Switch#show interfaces f0?
/  
Switch#show interfaces f0/6
FastEthernet0/6 is administratively down, line protocol is down (disabled)
  Hardware is Lance, address is 0060.3e4a.ea06 (bia 0060.3e4a.ea06)
 BW 100000 Kbit, DLY 1000 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  Keepalive set (10 sec)
  Half-duplex, 100Mb/s
  input flow-control is off, output flow-control is off
  ARP type: ARPA, ARP Timeout 04:00:00
  Last input 00:00:08, output 00:00:05, output hang never
  Last clearing of "show interface" counters never
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0
  Queueing strategy: fifo
  Output queue :0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     956 packets input, 193351 bytes, 0 no buffer
     Received 956 broadcasts, 0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
     0 watchdog, 0 multicast, 0 pause input
     0 input packets with dribble condition detected
     2357 packets output, 263570 bytes, 0 underruns
     0 output errors, 0 collisions, 10 interface resets
     0 babbles, 0 late collision, 0 deferred
     0 lost carrier, 0 no carrier
     0 output buffer failures, 0 output buffers swapped out
```

## Шаг 2. Проверьте настройки коммутатора по умолчанию.
Команды *(водимые мною)*:
```Switch>en
Switch#
Switch#
Switch#show
Switch#show ru
Switch#show running-config 
Building configuration...
 
Current configuration : 1090 bytes
!
version 12.2
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
 shutdown
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


b-e) Cisco IOS Software, C2960 Software (C2960-LANBASE-M), Version 12.2(25)FX, RELEASE SOFTWARE (fc1)
Copyright (c) 1986-2005 by Cisco Systems, Inc.
Compiled Wed 12-Oct-05 22:05 by pt_team
Image text-base: 0x80008098, data-base: 0x814129C4
 
 
 
Cisco WS-C2960-24TT (RC32300) processor (revision C0) with 21039K bytes of memory.
 
 
24 FastEthernet/IEEE 802.3 interface(s)
2 Gigabit Ethernet/IEEE 802.3 interface(s)
 
63488K bytes of flash-simulated non-volatile configuration memory.
Base ethernet MAC Address       : 0001.6433.C63C
Motherboard assembly number     : 73-9832-06
Power supply part number        : 341-0097-02
Motherboard serial number       : FOC103248MJ
Power supply serial number      : DCA102133JA
Model revision number           : B0
Motherboard revision number     : C0
Model number                    : WS-C2960-24TT
System serial number            : FOC1033Z1EY
Top Assembly Part Number        : 800-26671-02
Top Assembly Revision Number    : B0
Version ID                      : V02
CLEI Code Number                : COM3K00BRA
Hardware Board Revision Number  : 0x01
 
 
Switch   Ports  Model              SW Version              SW Image
------   -----  -----              ----------              ----------
*    1   26     WS-C2960-24TT      12.2                    C2960-LANBASE-M
 
Cisco IOS Software, C2960 Software (C2960-LANBASE-M), Version 12.2(25)FX, RELEASE SOFTWARE (fc1)
Copyright (c) 1986-2005 by Cisco Systems, Inc.
Compiled Wed 12-Oct-05 22:05 by pt_team
```

**f)** Подсоедините кабель Ethernet компьютера PC-A к порту 6 
Картинка

*`Примечание.` При использовании Netlab включите интерфейс F0/6 на коммутаторе S1.*
картинка
Команды *(водимые мною)*:
```Switch>enab
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#in
Switch(config)#interface f0/6
Switch(config-if)#no shu
Switch(config-if)#no shutdown 
 
Switch(config-if)#
%LINK-5-CHANGED: Interface FastEthernet0/6, changed state to up
 
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/6, changed state to up
 
Switch(config-if)#^Z
Switch#
%SYS-5-CONFIG_I: Configured from console by console
 картинка

h) Switch(config-if)#^Z
Switch#
%SYS-5-CONFIG_I: Configured from console by console
 
Switch#show int
Switch#show interfaces f0/6
FastEthernet0/6 is up, line protocol is up (connected)
  Hardware is Lance, address is 0060.3e4a.ea06 (bia 0060.3e4a.ea06)
 BW 100000 Kbit, DLY 1000 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  Keepalive set (10 sec)
  Full-duplex, 100Mb/s
  input flow-control is off, output flow-control is off
  ARP type: ARPA, ARP Timeout 04:00:00
  Last input 00:00:08, output 00:00:05, output hang never
  Last clearing of "show interface" counters never
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0
  Queueing strategy: fifo
  Output queue :0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     956 packets input, 193351 bytes, 0 no buffer
     Received 956 broadcasts, 0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
     0 watchdog, 0 multicast, 0 pause input
     0 input packets with dribble condition detected
     2357 packets output, 263570 bytes, 0 underruns
     0 output errors, 0 collisions, 10 interface resets
     0 babbles, 0 late collision, 0 deferred
     0 lost carrier, 0 no carrier
     0 output buffer failures, 0 output buffers swapped out
i) Switch>show vlan1
                ^
% Invalid input detected at '^' marker.
	
Switch>show vlan
 
VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                Fa0/9, Fa0/10, Fa0/11, Fa0/12
                                                Fa0/13, Fa0/14, Fa0/15, Fa0/16
                                                Fa0/17, Fa0/18, Fa0/19, Fa0/20
                                                Fa0/21, Fa0/22, Fa0/23, Fa0/24
                                                Gig0/1, Gig0/2
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    
 
VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1    enet  100001     1500  -      -      -        -    -        0      0
1002 fddi  101002     1500  -      -      -        -    -        0      0   
1003 tr    101003     1500  -      -      -        -    -        0      0   
1004 fdnet 101004     1500  -      -      -        ieee -        0      0   
1005 trnet 101005     1500  -      -      -        ibm  -        0      0   
 
VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
 
Remote SPAN VLANs
------------------------------------------------------------------------------
 
Primary Secondary Type              Ports
------- --------- ----------------- ------------------------------------------
```

**j)** Изучить флеш память
```Switch> show
Switch> show fla
Switch> show flash: 
Directory of flash:/
 
    1  -rw-     4414921          <no date>  c2960-lanbase-mz.122-25.FX.bin
 
64016384 bytes total (59601463 bytes free)
```
