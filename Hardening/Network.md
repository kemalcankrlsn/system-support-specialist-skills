## Network Cihazları için Hardening / Sıkılaştırma:
1. Güncelleme-Güncel Kalmak: IOS Sürüm güncellemeleri, şifreleme algoritmaları güncelliği ve devamında açıklanmış güvenlik güncelleştirmelerinin yüklenmesi.
2. Güvenli Giriş: Güvenli giriş yöntemlerinin oluşturulması.
    - Enable/ssh/telnet Tüm parolaların farklılaştırılması
    - Enable Parolası Değiştirilmesi
    - ```Switch(config)# login block-for 600 attempts 3 within 60``` Başarısız giriş denemelerini kapatma
    - SSH "crypto key generate rsa" 2048 ile daha güçlü şifreleme
    - SSH Domain belirlenmesi
    - "ip ssh version 2" uygulaması
    - `Switch(config)# username kemalcan privilege 15 secret password`SSH İçin kullanıcı oluşturulması standart admin hesapları dışında 
    - `Switch(config-line)# transport input ssh` Sadece SSH Kullanılması telnet kapatılması
    - `Switch(config)# line vty 0 15` Burada 16 kullanıcıya izin veriliyor, Bu hattın daraltılması sadece ihtiyaç kadar kullanıcı girişine izin verilmesi 
    - `Switch(config-line)# exec-timeout 3 30` line vty hattı için boşta kalma süresi ayarlanması, ssh/telnet için zaman aşımı uygulaması
    - ACL ile sadece belirli adreslerin veya cihazların erişimine açmak
3. Port Güvenliği
    - `Switch(config)# interface range fa0/1–3` `Switch(config-if-range)# shutdown` Kullanılmayan portların kapatılması
    - Vlan Hopping saldırısını önlemek için MAC Adress kısıtlama veya belirli mac adreslerine izin vermek `Switch(config-if)# switchport port-security maximum 2`
    - Yetkisiz kişinin bağlanması halinde portun kapatılması (PORT NAC) `Switch(config-if)# switchport port-security - Switch(config-if)# switchport port-security violation shutdown`
    - DTP ' nin kullanılmayan portlarda kapatılması trunk ın elle yapılandırılması
4. Native VLAN : Native VLAN değiştirrerek trunk hatları üzerinden geçen vlan 1 kullanımına kapatıyoruz. `Switch(config-if)# switchport trunk native vlan 100`
5. VTP (VLAN Trunk Protocol) : VTP kapatılması vlanların elle girilmesi. `Switch(config)# vtp mode transparent`
6. Kullanılmayan servislerin kapatılması;
    - CDP : `Switch(config)# no cdp run` cdp cisco cihazlarının birbirlerini tanımak için kullandığı servis.
    - LLDP : `Switch(config)# no lldp run` LLDP, CDP'ye benzer bir protokoldür ve cihazların birbirini keşfetmesine yardımcı olur. Bu protokol de güvenlik riski oluşturabilir.
    - HTTP,HTTPS : `Switch(config)# no ip http server - Switch(config)# no ip http secure-server`: Switch'in web tabanlı yönetimi için kullanılır. Eğer web arayüzünü kullanmıyorsanız, bu servislerin kapatılması güvenlik açısından faydalıdır.
    - Unnecessary Services : `Switch(config)# no service tcp-small-servers / Switch(config)# no service udp-small-servers` Diğer gereksiz servisler arasında TCP küçük sunucular (Echo, Chargen, Discard) ve UDP küçük sunucular (Echo, Discard) bulunur. Bunlar genellikle ağ yönetimi için kullanılmaz ve potansiyel güvenlik riski oluşturabilir.
    - Finger Servisi: `Switch(config)# no service finger` Finger servisi, kullanıcı hakkında bilgi almak için kullanılır ve genellikle güvenlik riski olarak kabul edilir.
    - Switch(config)# no snmp-server
    - Switch(config)# no ip proxy-arp
    - Switch(config)# no ip directed-broadcast
7. Spanning Tree Protocol'ü için BPDU Guard Etkinleştirme: 
    - Switch(config)# spanning-tree portfast bpduguard default
    - Switch(config)# interface GigabitEthernet0/1
    - Switch(config-if)# spanning-tree bpduguard enable
8. DTP devre dışı bırakma otomatik haberleşen trunk hatları için gerekli
9. Loglama ve İzleme: `Switch(config)# logging host <ip-address>`
10. DHCP Snooping



Kaynakça: https://medium.com/@zehraakmanlar26/switch-hardening-abb3ca4d3a5f
