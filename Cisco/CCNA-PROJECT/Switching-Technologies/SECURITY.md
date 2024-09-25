1. Secure All Unused Switchports
 - PORT GÜVENLİĞİ - KULLANILMAYAN PORTLAR
    - Switch(config)#int range fa0/4-24
    - Switch(config-if-range)#switchport mode access 
    - Switch(config-if-range)#switchport nonegotiate 
    - Switch(config-if-range)#switchport access vlan 999 
    - Switch(config-if-range)#shutdown
 - TRUNK HATTI OLUŞTURMAK:
    - Switch(config)# interface gigabitEthernet 0/1
    - Switch(config-if)# switchport mode trunk
    - Switch(config-if)# switchport trunk allowed vlan 10,20,51,99,110,120 
    - Switch(config-if)# switchport trunk native vlan 99 
    - Switch(config-if)# switchport nonegotiate 

2. STP Attack Prevention
 - Portfast VE Bpduguard
   - Switch(config)#interface fastEthernet 0/10 
   - Switch(config-if)#spanning-tree portfast 
   - Switch(config-if)#spanning-tree bpduguard enable 
 - PORTU TEKRAR AÇMAK
   - Switch(config)#int fa0/10
   - Switch(config-if)#shutdown
   - Switch(config-if)#no shutdown 


3. Disable CDP on the Devices
   - Switch(config)# no cdp run
   - Switch(config)# interface range fastethernet 0/4-24
   - Switch(config-if)# no cdp enable

4. VLAN Hoping Attack Pevention
   - Switch(config-if)# switchport nonegotiate

5. DHCP Snooping
   - Switch(config)#ip dhcp snooping
   - Switch(config)#ip dhcp snooping vlan 10,20,30.....
 - Güvenilir portlar SW-SW / SW-RUTER Gibi
   - Switch(config)#int range gi 0/1-2
   - Switch(config-if-range)#ip dhcp snooping trust -fastethernet 4-5 e dhcp güveniyor
 - Kullanılmayan portlarda rate 1 yapalım sadece 1 dhcp paketi geçsin
   - Switch(config-if)#int ra fa0/3,24
   - Switch(config-if-range)#ip dhcp snooping limit rate 1

6. Dynamic ARP Inspection
   - Switch(config)#ip dhcp snooping
   - Switch(config)#ip arp inspection vlan 10,20,30 --- Bu komut, VLAN 10, 20, 30 üzerinde ARP denetimini etkinleştirir.

   - Switch(config)#int range gi 0/1-2
   - Switch(config-if-range)#ip arp inspection trust 

   - Switch#sh ip arp inspection interfaces

7. IP Source Guard
   - Router(config)# login block-for 300 attempts 5 within 60 

8. Port Security

   - Switch(config)#interface range fa0/1-6
   - Switch(config-if-range)#switchport mode access 
   - Switch(config-if-range)#switchport port-security 

   - Switch(config-if)# switchport port-security maximum 1 
   - Switch(config-if)# switchport port-security aging time 15 

   - Switch(config-if)# switchport port-security mac-address 0001.1234.5678 --- Statik MAC Adresi Tanımlama
   - Switch(config-if)# switchport port-security mac-address sticky --- Dinamik Olarak MAC Adresi Öğrenme

   - Switch(config-if)# switchport port-security violation protect 
   - Switch(config-if)# switchport port-security violation restrict 
   - Switch(config-if)# switchport port-security violation shutdown 

   - Switch# show port-security interface gigabitEthernet 0/1
   - Switch# show port-security


9. ACL for VTY interfaces
   1. Router üzerinden yönlendirmeleri yaptık
   2. uzakta management pc var
   3. test yapılacak switch üzerinde ssh yapılandırmaları yaptık int vlan 1 ip atadık
   4. TEST-SSH(config)#access-list 10 permit host 192.168.1.11 --- 192.168.1.11 ip adresli cihaza izin veriyoruz
   5. TEST-SSH(config)#access-list 10 deny any ---- deny any diğerlerini engelliyoruz.
   6. TEST-SSH(config)#line vty 0 4 --- oluşturulan line hattına giriyoruz
   7. TEST-SSH(config-line)#access-class 10 in --- access list 10 u seçiyoruz.
   > [Connection to 192.168.2.150 closed by foreign host] diğer cihazların aldığı mesaj
   > 192.168.1.11 cihazı sadece erişebiliyor.

