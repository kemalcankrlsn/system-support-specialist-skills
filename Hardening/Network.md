## Network Cihazları için Hardening / Sıkılaştırma:
1. Güncelleme-Güncel Kalmak: IOS Sürüm güncellemeleri, şifreleme algoritmaları güncelliği ve devamında açıklanmış güvenlik güncelleştirmelerinin yüklenmesi.
2. Güvenli Giriş: Güvenli giriş yöntemlerinin oluşturulması.
    - Enable/ssh/telnet Tüm parolaların farklılaştırılması
    - Enable Parolası Değiştirilmesi
    - ```Switch(config)# login block-for 600 attempts 3 within 60``` deneme
    - SSH "crypto key generate rsa" 2048 ile daha güçlü şifreleme
    - "ip ssh version 2" uygulaması
    - "exec-timeout" ssh/telnet için zaman aşımı uygulaması
    - telnet kapatma.
    - line vty hattının daraltılması
    - ACL ile sadece belirli adreslerin veya cihazların erişimine açmak
3. Port Güvenliği
    - Kullanılmayan portların kapatılması
    - MAC Adress bazında izin vermek vlan hopping saldırısını engelleme
    - Portlar üzerinde sadece belirli sayıda mac adresinin çalışması
    - Yetkisiz kişinin bağlanması halinde portun kapatılması (PORT NAC)
    - 
4. Native VLAN : Native VLAN değiştirrerek trunk hatları üzerinden geçen vlan 1 kullanımına kapatıyoruz.
5. VTP (VLAN Trunk Protocol) : VTP kapatılması vlanların elle girilmesi.



Kaynakça: https://medium.com/@zehraakmanlar26/switch-hardening-abb3ca4d3a5f
