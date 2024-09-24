## VLAN Türleri
1. Data Vlan (10,20,30,...) - Verilerin (bilgisayar, yazıcı vb.) taşındığı VLAN türüdür. Bu VLAN, çalışanların günlük veri trafiğini taşıyan VLAN’dır.

2. Default VLAN - VLAN 1(1) - Cisco switch’lerde varsayılan olarak VLAN 1’dir. Bu VLAN, switch'in başlangıç yapılandırmasında tüm portlar için kullanılan VLAN'dır. Her yeni switch'te varsayılan olarak oluşturulmuştur.

3. Native VLAN (99) - Native VLAN, trunk portu üzerinden etiketlenmemiş (tagless) trafiği taşıyan VLAN'dır. Varsayılan olarak, VLAN 1 Native VLAN olarak yapılandırılmıştır, ancak değiştirilebilir. Trunk hattı üzerinden "switchport trunk native vlan 99" ile değiştirebiliriz

4. Management VLAN (51)-Switch'in uzaktan yönetimi için kullanılan VLAN'dır. Yönetim VLAN’ı, switch'in IP adresine erişim sağlanan VLAN’dır. Genellikle switch'e SSH veya Telnet gibi protokollerle erişim sağlanır.

5. Voice VLAN (20)= IP telefonlar gibi ses cihazları için ayrılmış VLAN’dır. Bu VLAN, ses trafiğinin (VoIP) diğer veri trafiğinden ayrılmasını ve ses hizmetlerinin optimize edilmesini sağlar. Voice VLAN ile ağda QoS (Quality of Service) gibi özelliklerle ses paketleri önceliklendirilebilir.

6. Unused VLAN (999) = Kullanılmayan portları bu vlan e atıyoruz ve trunk hattı üzerinden geçişine izin vermiyoruz.

Vlan 0-1005 Arası Kullanılabilir;
Data Vlan (10,20,30,...)
Default VLAN - VLAN 1(1)
Native VLAN (99)
Management VLAN (51-200)
Voice VLAN (100-150)
BlackHole Vlan (999)

10   DATA-VLAN-10                     active    
20   DATA-VLAN-20                     active    
51   MANAGEMENT-VLAN                  active    
99   NATIVE-VLAN                      active    
110  VOICE-VLAN-110                   active    
120  VOICE-VLAN-120                   active    
999  BlackHole-VLAN                   active 
 


## DTP (Dynamic Trunking Protocol)
1. Cisco switchler arasında trunk bağlantıların dinamik olarak oluşturulmasını sağlıyor. DTP, iki switch arasında trunk port yapılandırmasını otomatikleştirir ve iki portun trunk veya access modu arasında anlaşmasına olanak tanır. 
2. DTP Modları:
- Dynamic Auto - Bu modda switch, eğer karşıdaki cihaz trunk modundaysa kendini trunk olarak yapılandırır. Eğer karşıdaki port access modundaysa, kendini access modunda bırakır.
- Dynamic Desirable - Bu modda switch, karşıdaki switch ile trunk olmak için aktif olarak trunk talebi gönderir. Eğer karşıdaki switch trunk destekliyorsa, port trunk moduna geçer.
- Trunk - Switch, trunk modunda sabitlenir. Karşıdaki switch ne olursa olsun bu port trunk olarak çalışır.
- Access - Switch, access modunda sabitlenir ve DTP trunk talebi göndermez.

Access bağlantısı switch -> pc bağlantısı 
Trunk bağlantısı Switch -> Switch vlanların geçmesini sağlar

> Cisco diyor ki bu yapılandırmaları auto da bırakma elle yap. 

3. DTP Devre dışı bırakma
- Switch1(config)# interface gigabitEthernet 0/1
- Switch1(config-if)# switchport mode trunk
- Switch1(config-if)# switchport nonegotiate --- dtp devre dışı bırakıyoruz

## VTP (VLAN Trunking Protocol) Yapılandırması
VTP'nin 3 ana modu vardır:
Server Mode: Bu modda VLAN'lar oluşturulabilir, değiştirilebilir ve silinebilir. Tüm switch'lere bu bilgiyi dağıtır.
Client Mode: Bu modda VLAN'lar sadece server modundaki switch'ten alınır. Yeni VLAN oluşturamaz veya mevcut VLAN'ları değiştiremez.
Transparent Mode: Bu modda switch, kendi lokal VLAN yapılandırmasını saklar ama VTP mesajlarını iletir. Başka switch'lere VLAN bilgilerini yaymaz.
> Cisco diyorki önce switchlerinizi client moda alın server dan verileri çekin sonra transparent moda alın


## CLI VLAN
1. VLAN OLUŞTURMA;
    - Switch(config)#vlan 10
    - Switch(config-vlan)#name DATA-VLAN-10

2. TRUNK HATTI OLUŞTURMAK:
    - Switch(config)# interface gigabitEthernet 0/1
    - Switch(config-if)# switchport mode trunk
    - Switch(config-if)# switchport trunk allowed vlan 10,20,51,99,110,120 --- SADECE 10,20 Vlanları geçer
    - Switch(config-if)# switchport trunk native vlan 99 --- native vlan 99 oluyor
    - Switch(config-if)# switchport nonegotiate --- dtp kapatma
      
3. DTP KAPATMA-PORTLARI ACCESS MOD A ÇEKME
    - Switch(config)#int range fa0/1-24
    - Switch(config-if-range)#switchport mode access
    - Switch(config-if-range)#switchport nonegotiate
    - Switch(config)#int gi0/2
    - Switch(config-if-range)#switchport mode access
    - Switch(config-if-range)#switchport nonegotiate

4. VTP:
    - SERVER;
    - Switch1(config)# vtp domain NETWORK
    - Switch1(config)# vtp mode server
    - Switch1(config)# vtp password Cisco123
    - Switch1(config)# vtp version 2
  
    - CLİENT
    - Switch2(config)# vtp domain NETWORK
    - Switch2(config)# vtp mode client
    - Switch2(config)# vtp password kemalc4n*
    - Switch2(config)# vtp version 2
  
    - TRANSPARENT;
    - Switch(config)# vtp mode transparent

      
5. PC PORTLARINI VLAN DAHİL ETMEK:
    - Switch(config)#int fa0/1
    - Switch(config-if)#switchport mode access 
    - Switch(config-if)#switchport access vlan 10
    - Switch(config-if)#switchport voice vlan 110 ---- voice vlan eklemek
    - > Switch(config)#int range fastEthernet 0/1-10 (Port aralığı seçmek)

6. PORT GÜVENLİĞİ - KULLANILMAYAN PORTLAR
    - Switch(config)#int range fa0/4-24
    - Switch(config-if-range)#switchport mode access --- modu elle yapılandırdık
    - Switch(config-if-range)#switchport nonegotiate --- dtp kapatma
    - Switch(config-if-range)#switchport access vlan 999 --- karadelik vlan ı na atadık
    - Switch(config-if-range)#shutdown  --- portu kapattık

7. Management VLAN (svı)
    - Switch(config)# vlan 51
    - Switch(config-vlan)# name Management_VLAN
    - Switch(config)# interface vlan 51
    - Switch(config-if)#ip address 192.168.3.10 255.255.0.0
    - Switch(config)# interface fa0/3
    - Switch(config-if)# switchport mode access
    - Switch(config-if)# switchport access vlan 51



 ## SHOW Komutları
Switch#sh int gi0/1 switchport  --- portun dtp özelliklerini görmek
Switch#show interfaces trunk  ---- trunk ları görmek için
Switch#show vlan brief  --- vlanları görmek
Switch#show vlan  ---- vlanları görmek
Switch#show vlan id 10 --- 10 vlanı görmek
Switch#show interfaces switchport --- tüm portları görmek 
Switch#show interfaces gi0/1 status --- status olarak görmek
Switch#show vtp status --- vtp görmek
Switch#show ip interface brief  ---- int lerin ip adreslerini görmek
Switch#show cdp neighbors --- komşuları görme


