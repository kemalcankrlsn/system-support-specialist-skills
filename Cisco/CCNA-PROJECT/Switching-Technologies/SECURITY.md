1. Secure All Unused Switchports 
> Switch üzerinde kullanılmayan portları kapatmak ve blackhole 999 vlan ı ne dahil etmek.
> Trunk hattı üzerinde geçebilecek vlanleri işaretlemek ve native vlan değiştirmek ve dtp kapatmak
 - PORT GÜVENLİĞİ - KULLANILMAYAN PORTLAR
    - Switch(config)#int range fa0/4-24
    - Switch(config-if-range)#switchport mode access --- modu elle yapılandırdık
    - Switch(config-if-range)#switchport nonegotiate --- dtp kapatma
    - Switch(config-if-range)#switchport access vlan 999 --- karadelik vlan ı na atadık
    - Switch(config-if-range)#shutdown  --- portu kapattık
 - TRUNK HATTI OLUŞTURMAK:
    - Switch(config)# interface gigabitEthernet 0/1
    - Switch(config-if)# switchport mode trunk
    - Switch(config-if)# switchport trunk allowed vlan 10,20,51,99,110,120 --- SADECE 10,20 Vlanları geçer
    - Switch(config-if)# switchport trunk native vlan 99 --- native vlan 99 oluyor
    - Switch(config-if)# switchport nonegotiate --- dtp kapatma

2. STP Attack Prevention
> Portfast VE Bpduguard

Switch(config)#interface fastEthernet 0/10 --- interface seçtik
Switch(config-if)#spanning-tree portfast --- 
Switch(config-if)#spanning-tree bpduguard enable --- 
> Şimdi pvst yapılandırma olan portlarda switchlerde porta istemci pc client takıldığından gecikme yaşanıyor bu gecikme yaşanmaması için portfast diyoruz bu portu hızlandırıyoruz yani rapid pvst yapıyoruz bu uygulamayı yaptıktan sonra bu porta switch hub takıldığı zaman loop olmaması için bpduguard enable diyoruz bu porta switch takıldığında portu kapatıyor.
> Switch hub takıldığı zaman port down oluyor portu tekrar açmak için

Switch(config)#int fa0/10
Switch(config-if)#shutdown
Switch(config-if)#no shutdown 

yaparak portu tekrar açıyoruz.


3. Disable CDP on the Devices
> CDP Cisco cihazların birbirlerine bilgiler gönderdiği servis bunu kapatıyoruz.
- Switch(config)# no cdp run ne işe yarar

> Yada kullanılmayan portlarda sadece kapatabiliriz.
- Switch(config)# interface gigabitEthernet 0/1
- Switch(config-if)# no cdp enable

4. VLAN Hoping Attack Pevention
Switch(config-if)# switchport nonegotiate
> trunk hattı ve tüm portlarda dtp kapatmak dtp dinamik trunk hattı oluşturan protokol

5. DHCP Snooping
Switch(config)#ip dhcp snooping 
Switch(config)#ip dhcp snooping vlan 1
> dhcp snooping etkinleştirme

Switch(config)#int range fastEthernet 0/4-5
Switch(config-if-range)#ip dhcp snooping trust 
> fastethernet 4-5 e dhcp güveniyor


Switch#show ip dhcp snooping 

6. Dynamic ARP Inspection
 1. önce dhcp snooping etkinleştiriyoruz
 2. Belirli VLAN'larda DAI’yi etkinleştirmek için şu komutu kullanabilirsiniz:
   - Switch(config)#ip arp inspection vlan 1
 3. Güvenilir ve Güvenilmeyen Portlar Tanımlama
   - Switch(config)#int range fastEthernet 0/1-5
   - Switch(config-if-range)#ip arp inspection trust 

   - Switch#sh ip arp inspection interfaces --- güvenilir portları görmek
   - Switch#sh ip arp inspection interfaces --- detaylı görmek

7. IP Source Guard
> deneyemedim

8. Port Security
## PORT SECURİTY Portlarda aktif ediyoruz
- Switch(config)#interface range fa0/1-6
- Switch(config-if-range)#switchport mode access 
- Switch(config-if-range)#switchport port-security 

## Kurallar
- Switch(config-if)# switchport port-security maximum 2 --- İzin Verilen Maksimum MAC Adresi öğrenme

## MAC Adress öğrenme
- Switch(config-if)# switchport port-security mac-address 0001.1234.5678 --- Statik MAC Adresi Tanımlama
- Switch(config-if)# switchport port-security mac-address sticky --- Dinamik Olarak MAC Adresi Öğrenme

## Eylemler (Güvenlik İhlali Eylemi (Violation Mode) Ayarlama)
- Switch(config-if)# switchport port-security violation protect --- İhlal durumunda, port sadece yetkisiz trafiği düşürür, herhangi bir bildirim yapılmaz.
- Switch(config-if)# switchport port-security violation restrict --- İhlal durumunda, yetkisiz trafiği düşürür ve log'lama (syslog) yapar, aynı zamanda güvenlik sayacını artırır.
- Switch(config-if)# switchport port-security violation shutdown --- İhlal durumunda, portu tamamen devre dışı bırakır (err-disabled moduna geçirir). Bu mod varsayılan olarak kullanılır

## SHOW 
- Switch# show port-security interface gigabitEthernet 0/1
- Switch# show port-security



Switch(config)#interface fastEthernet 0/1
Switch(config-if-range)#switchport mode access 
Switch(config-if-range)#switchport port-security 
Switch(config-if-range)#switchport port-security maximum 1
Switch(config-if-range)#switchport port-security mac-address sticky 
Switch(config-if-range)#switchport port-security violation shutdown
 