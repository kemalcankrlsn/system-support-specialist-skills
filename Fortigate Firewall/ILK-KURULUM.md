İlk Kurulum Sonrası Yapılacaklar List:
1-Network->Interfaces (Portların IP lerinin yapılandırılmalarını yaptık)(LAN-WAN interfaceleri belirtip ip lerini veriyoruz.)
2-Firewall/UTM Cihazımızı internete çıkartmak için Network->Static Routes yapılandırması yapıyoruz. Bu sadece Firewall cihazımızı internete çıkartır, clientler için Policy yazmamız lazım.
3-Policy&Object->Firewall Policy - Portları internete çıkartmak 
4-"admin" hesabını parolasını değiştirdik 2 faktörlü giriş etkin ettik
5-System->Settings->Host name --- cihaz ismini değiştirelim
6-System->Settings->System Time --- ntp kullanımı ve saatin güncelliği
7-System->Settings->HTTP/HTTPS port --- Portlarını değiştirmek
8-System->Settings->SSH/TELNET Port --- ilgili portlarımızı değiştirelim
9-WAN Interfacesi için ping,http,https,ssh bunları kapatalım dışardan bir adam firewall cihazına erişemesin
10-DHCP ayarları - client tarafı dhcp ayarlarını yaptık


NELER Öğrendik:
Interface yapılandırmaları
Static Routes - firewall ın internete çıkması
Firewall backup alma geri yükleme
NTP Yapılandırılması
Firewall Policy - IPv4 Policy - portları yönlendirme ve kurallar verme
Addressess - belirli grup ip lere ve belirli ip lere yetki verme
Services - Servis bazlı izin vermek
Schedules - Zaman bazlı kısıtlamalar.
Vertual IPs - Sadece belirli portlara izin verme
Antivirüs - dosya engellemeleri
Web Filter - Belirli grup kategorili siteleri engelleme URL Filter ile tek site engelleme
IPS - 2 port bacak arasında güvenlik önlemleri 



YAPILANDIRMALAR:
-----------------------------------
Network->Interfaces-> Role (interfaceleri düzenledik)
LAN - (İçerisi güvenlikli alan)
WAN - (Dışarısı interneti aldığımız yer)
Estimated Bandwidth(Tahmini Bant Genişliği) - 
-----------------------------------

-----------------------------------
Network->Static Routes-> (Fortigate cihazımızı internete çıkarttık)
Destination - 0.0.0.0/0.0.0.0 - Gideceğimiz Tüm adresler
Interface - WAN Bacağımız
Gateway Address - WAN İnterface ' in Default Gateway i (192.168.1.1)
-----------------------------------


-----------------------------------
Policy & Object->Firewall Policy-> 
Name  -> Kuralın adı
Schedule -> Zaman kısıtlaması koymak 
Action -> Accept mi Deny mi yani bu protokol yasaklama mı izin verme mi
Incoming Interface -> İnternete Çıkacak Portun kendisi (LAN)
Outgoing Interface -> İnternete nereden çıkacağı (WAN)
Source -> Gideceği kaynaklar tüm (all) hepsi
Destination -> all
Service -> Kuralın kullanabileceği servisler (all) hepsi
-----------------------------------
