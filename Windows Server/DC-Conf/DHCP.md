## DHCP Manager Kurulum ve Yapılandırma:
Rol Ekleme DHCP Ekleme; DHCP Server Seçtik ,Ad Roles and Features den dhcp kurduk sonra Yapılandırma yapacağız
Önce “scope” oluşturmamız lazım.
Server Manager > Tools > DHCP Açtık
IPv4 Üzerinden önce “scope” oluşturmamız lazım.
IPv4 Sağ tıklayıp “New Scope” dedik
Kategorize etmek için Name ve Desc düzenliyoruz
Not: 192.168.10.1-192.168.10.255 aralığındaki ağ 192.168.10.0 ağı diyoruz. 0 dediğimiz zaman O aralıktaki tüm IP ler.
192.168.10.255 Ağı broadcast adresidir.
192.168.10.1 Default Gateway dir, Çıkış kapısı, Dışarıya çıkış kapısı internete çıkış kapısı. Default gateway ler her zaman ilk ıp yi kullanır.
 
“Add Exclusions and Delay” Ayrı tutulacak bölüm 192.168.10.50-192.168.10.60 Arası IP ler kimseye verilmiyor Yazıcılar ve Isı cihazları IP si değişmeyecek cihazları NVR lar için bu kısımda ayırma yapabiliriz.
“Subnet delay in milli second” Aynı ağ da 2 adet DHCP server varsa DC1 – DC2 mili saniye olarak IP vermesini engelleyebiliyoruz mesela 1000milisaniye IP verme gibi
Buraya tek IP adresi de yazabiliriz
 
“Lease Duration” Kira süresi belirleyebiliyoruz, 8 gün süresince %50 geldiğinde soruyor IP kullanıyormusun cevap evet ise süre %100 oluyor. %50 den sonra bir daha %50 bekliyor yani %87.5 oluyor soruyor kullanıyorsa sıfırlıyor ama bir sonraki periyotta cevap gelmiyorsa IP yi elinden alıyor.
IP nin boşa çıkmadığı sürekli yenilendiği “renewal” deniyor.
 
 

Burada default gateway yapılandırılmasını yapalım mı yapmayalım mı soruyor.
 
İpconfig /all – tüm ip bilgilerini dns ve etki alanı bilgileri görme
İpconfig /release – IP yi bırakma Yani kabloyu çıkartma ve DHCP Sunucusundan IP yi bırakma
İpconfig /renew – IP mi yenile yeni IP al 

 

