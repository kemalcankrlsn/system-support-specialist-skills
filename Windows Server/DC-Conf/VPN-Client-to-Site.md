## Client to Site VPN bağlantısı Yapılandırması:
1. NAT yapılandırmamızda internal(LAN) ağımız dışarıya çıkıyordu ama external(WAN) ağındaki birisi içeriye giremiyordu, vlient to site vpn de dışardan içeriye bir tünel oluşturacağız.
2. VPN için domainde vpn kullanıcına ihtiyacımız var.
3. Yönetimi için DC ve RRAS lazım ve RRAS cihazımız yönetimde olacağı için domaine dahil olması gerekiyor.
4. DC ve RRAS makinemizin uzaktan erişimi açık olması gerekiyor.
5. RRAS makinemize domain admini ile giriş yapıyoruz.
### Başlıyoruz
1. vpn kullanıcısı açıyoruz ve NPS server şimdi olmadığı için "dial-in" allow access diyoruz.
2. RRAS cihazımızı domaine dahil ettik.
3. RRAS da yeniden configure ediyoruz ve VPN or NAT ı seçiyoruz, ve DHCP verilecek aralığı belirliyoruz. Şimdilik RADIUS olmadığı için "no use" diyoruz
4. Site dışında olan cihazlarımızı windows vpn den ekleme yapıyoruz. sunucu adresi adı rras yani router görevi gören cihazı veriyoruz. ve vpn kullanıcımızı giriyoruz.
5. VPN Türleri:
    - Point-to-Point Tunneling Protocol (PPTP):Kolay yapılandırılabilir ve yaygın olarak kullanılır.Güvenlik açısından eski olduğu için modern standartlar kadar güvenli değildir.
    - Layer 2 Tunneling Protocol (L2TP) over IPsec: L2TP, genellikle IPsec (Internet Protocol Security) ile birlikte kullanılır.Güvenli ve yaygın olarak tercih edilen bir VPN çözümüdür.
    - Secure Socket Tunneling Protocol (SSTP): SSL (Secure Sockets Layer) kullanır ve genellikle güvenlik duvarlarından kolay geçer. Windows ortamlarında iyi bir uyumluluk sunar.
    - IKEv2 (Internet Key Exchange version 2):Mobil cihazlar için özellikle güvenilir ve kararlı bir protokoldür.Bağlantı kopmalarına karşı daha dayanıklıdır ve yeniden bağlantı süresi hızlıdır.
6. RRAS makinemizde rras manager da "properties" de L2TP security key girdik ve 
site dışı makinemiz ile vpn ayarlarını yaptık.
7. ve bana site dışı makinem site içinden ip verdi
8. Diğer VPN türleri ile de bağlantı deneyeceğiz.






