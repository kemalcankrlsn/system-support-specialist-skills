## LAYER3 SW (MULTİLAYER) İnterVLAN - Routing On A Stick
vlan 10
name IT-DEPT
VLAN 20
NAME HR-DEPT
VLAN 30
NAME FIN-DEPT
ex

ip routing

int ra fa0/1-2
sw m a
sw ac vl 30
ex
int ra fa0/3-4
sw m a
sw ac vl 20
ex

int gi0/1
switchport trunk encapsulation dot1q
sw mode trunk 
ex

int vlan 30
ip address 192.168.30.1 255.255.255.0
no sh
ex
-----------------------------
LAYER3 SW
Switch(config)#int range gi1/0/1-3
Switch(config-if-range)#switchport mode trunk 
Switch(config-if-range)#exit
Switch(config)#vtp domain itu
Switch(config)#vtp password itupass
Switch(config)#exit


Switch(config-if)#int vlan 100
Switch(config-if)#ip address 192.168.100.1 255.255.255.0
Switch(config-if)#int vlan 200
Switch(config-if)#ip address 172.16.200.1 255.255.255.0
Switch(config-if)#exit


Switch(config)#ip routing --- 


Vlanleri oluşturduk-Portlara vlanleri atadık
ip routing etkinleştirdik
L3 Üzerinde svı ları oluşturduk no sh ile vlanleri açtık
layer3 sw trunk portunu encapsulation dot1q açtık
pc lere ip adreslerini gatewaylerini verdik
NOT: 3650 layer3 sw portlar direkt trunk oluyor encapsulation protokolü istemiyor
3560 layer3 sw "switchport trunk encapsulation dot1q" ile portu protokole dahil etmemiz gerek