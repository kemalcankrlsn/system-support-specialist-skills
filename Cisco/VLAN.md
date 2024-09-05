## VLAN

1. VLAN OLUŞTURMA;
    - Switch(config)#vlan 10
    - Switch(config-vlan)#name VLAN10

2. PORTLARI VLAN DAHİL ETMEK:
    - Switch(config)#int fa0/1
    - Switch(config-if)#switchport mode access 
    - Switch(config-if)#switchport access vlan 10
    - > Switch(config)#int range fastEthernet 0/1-10 (Port aralığı seçmek)

3. TRUNK HATTI OLUŞTURMAK:
    - Switch(config)# interface gigabitEthernet 0/1
    - Switch(config-if)# switchport mode trunk
    - Switch(config-if)# switchport trunk allowed vlan 10,20
    - Switch(config-if)# switchport trunk native vlan 99






 ## SHOW Komutları
 - Switch#show vlan brief 
 - Switch#show vlan 
 - Switch# show vlan id [VLAN_ID]
 - Switch#show interfaces switchport
 - 