DNS:
DNS Manager;
Forward Lookup zones : DOMAIN > IP isimden ip çözümlemesi
Reverze Lookup Zones: IP > DOMAIN ip den isim çözümlemesi
Kayıt türleri:
www = web kayıt türü
a-aaaa = a ipv4/aaaa ipv6 çözümlemesi
cname = dns listelerini bağlayabiliyoruz
Root hints = dns kayıtlarında bulunamayan ip domainleri root hints e yönlendiriyor
forwarding = dns kayıtlarımızda yoksa google dns giriyoruz bizde olmayan dns leri gidip buluyor
SOA Kaydı = zone ile ilgili bilgileri tutuyor


Server DNS Giriş
Kısayolu “dnsmgmt.msc”
DNS Açılımı “Domain Name System”
“ipconfig /all”
Server DNS üzerinden kayıt defterini ıp-link yapılandırmasını düzenleyebiliriz.
DNS kendi içinde 2 ye ayrılıyor
“Forward lookup zone” – Name > IP Dönüştürüyor
“Reverse lookup zone” – IP > Name Dönüştürücü 

Bi makine domain de ise “DC” DNS servisi o makineyi tanır
Ping atmama olursa güvenlik duvarındadır sorun
