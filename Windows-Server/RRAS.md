---------------------------------------------------
2 RRAS arası bağlantıyı elle yapmak için "Static Routes"
Nasıl;
Routing and Remote Access Açıyoruz
Configure Enable açıyoruz->Custom Configure->LAN Routing servisini açıyoruz
RRAS1->IPv4->Static Routes sağ tıklayıp "New Static Route"
Interface = Router yapılacak makinenin dış dünya ile kurduğu ağ WAN ağı yani
Destination = İletişim kurulacak hedef ağın network id si Bizim yapımızda istanbuldaki RRAS için kocaelideki RRAS network id si 192.168.17.0
Network Mask = Ağın subneti 255.255.255.0
Gateway = diğer iletişim kurulacak RRAS ın IP Adresi verilecek
---------------------------------------------------

---------------------------------------------------
Bu bağlantıları otomatik yapmak için RIP ile
Nasıl;
Routing and Remote Access Açıyoruz
Configure Enable açıyoruz->Custom Configure->LAN Routing servisini açıyoruz
RRAS1->IPv4->RIP sağ tıklayıp "New Interface"
"external" yani iletişim kurulacak interface dış ağ interfacesi-diğer tarafda da bu değerleri alıcaz
yani aslında external dediğimizde RRAS makine internal ağını öğretiyor 
---------------------------------------------------


---------------------------------------------------
Ağımızdaki Cihazları dışarı çıkartmak için NAT
NAT altında new interface diyoruz ve external için public interface connected to the internet - Enable NAT on this interface seçiyoruz,
Yani RRAS makine kendisine bağlı cihazları NAT ile dışarıya dışartma izni veriyor.
---------------------------------------------------
