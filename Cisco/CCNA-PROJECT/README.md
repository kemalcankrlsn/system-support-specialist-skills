## [BASIC CONFIGURATIONS](https://github.com/kemalcankrlsn/system-support-specialist-skills/blob/main/Cisco/CCNA-PROJECT/Basic-Configuration/SW-BASIC-CONFIG.md)
1. Navigating User Levels --- EN-CONFT User modları
2. Hostname --- cihaz adı router switch adı
3. Banner motd/message --- ilk giriş mesajı
4. Enable Password --- "en" parolası
5. Line console password --- telnet hattı 
6. Line VTY password --- telnet hattı parolası
7. Exec timeout --- işlemsizlik zamanı logout süresi
8. Logging Synchronous --- komut yazarken ekrana bilgi komutları gelmesi
9. Disabling ip domain lookup --- switch üzerinden dns search kaldırma normalde ctrl shift 6 ile kapatılıyor
10. IP domain name ---- ssh için sw router a ip domain name girilmesi
11. Username and password --- kullanıcı ve parolası oluşturma
12. Encrypting all passwords ---- şifrelerin config dosyalarına şifrelenerek kayıt edilmesi
13. Set Current Clock Time ---- sw router zaman girilmesi
14. Set management IP Address-SW ---- svı yapılandırılması router de loopback 0
15. Prevent Brute-force Attack-Router ---- blcok-for
16. Viewing Running & Startup Configs ---- sh run komutu
17. Saving running into startup configs ---- wr komutu

## SWITCHING TECHNOLOGIES
1. VLANs --- vlan.md
2. VLAN Trunking Protocol- VTP --- vlan.md
3. Trunk- Allowed/Denied VLANs --- vlan.md
4. Configure Native VLAN --- vlan.md
5. Remote Access- Telnet --- SW-BASIC-CONFIG.md
6. Remote Access- SSH --- SW-BASIC-CONFIG.md
7. L2 EtherChannel- PAGP/LACP --- etherchannel.md
8. L2 EtherChannel- ON Mode --- etherchannel.md
9. Secure All Unused Switchports --- vlan.md / security.md
10. STP Attack Prevention --- stp.md / security.md
11. Disable CDP on the Devices  --- secirity.md
12. VLAN Hoping Attack Pevention --- vlan.md / secirity.md
13. DHCP Snooping --- security.md
14. Dynamic ARP Inspection --- security.md
15. IP Source Guard --- security.md
16. Port Security --- security.md
17. ACL for VTY interfaces --- 




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



