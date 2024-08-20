## VLAN

1. VLAN OLUŞTURMA;
    - Switch(config)#vlan 10
    - Switch(config-vlan)#name VLAN10

2. PORTLARI VLAN DAHİL ETMEK:
    - Switch(config)#int fa0/1
    - Switch(config-if)#switchport mode access 
    - Switch(config-if)#switchport access vlan 10


TRUNK HATTI OLUŞTURMAK:
Switch(config)#int gi0/1
Switch(config-if)#SWitchport trunk encapsulation dot1q 
Switch(config-if)#switchport mode trunk 
Switch(config-if)#switchport trunk native vlan 111 --- native vlan değiştirdik
Switch(config-if)#switchport trunk allowed vlan 10,20

ACL Access Control List
Switch(config)#access-list 100 permit ip 192.168.1.0 0.0.0.255 any
Switch(config)#access-list 100 deny ip any any
Switch(config)#int vlan 10
Switch(config-if)#ip access-group 100 in


 ## SHOW Komutları
 - Switch#show vlan brief 
 - Switch#show vlan 
 - 