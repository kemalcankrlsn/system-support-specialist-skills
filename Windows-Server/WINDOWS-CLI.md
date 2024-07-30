# Windows ve Server Komutları

## Windows

- `netstat -r` Port tablosunu görüntülemek için bir Windows ana bilgisayarında kullanılabilir.
- `ipconfig /displaydns` Kayıtlı olan DNS sunucularını gösterir.
- `ipconfig /flushdns` DNS önbelleğini temizler.
- `ipconfig /all` Tüm IP-DNS IP yapılandırma bilgilerini gösterir.
- `tracert` Sorgulanan IP adresi veya web adresi üzerinden geçen durakları listeler. Yavaş bağlantı ama web sayfasına ulaşılıyorsa, yolda takılan ne var diye kullanılır (hangi durak yavaşlatıyor).
- `tracert -d` Hostname ve adres olmadan hızlıca test yapar.
- `pathping` Hangi routerlardan geçtiğini gösterir.
- `nslookup` IP adres/domain name çözümlemesi yapar, yani web sitenin IP adresini verir.
- `gpresult /r /scope computer` Uygulanan group policy'leri görme. `rsop.msc` ile de görebiliriz.
- `mstsc` RDP kısayolu.
- `oobe\bypassnro` Windows 11 kurulumu sırasında e-postasız devam etme. Shift + F10 ile komut satırını açıp bunu yaz.
- `HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Explorer` Kayıt defteri yolu.
- `arp -a` Network interfaceleri gösterir.
- `ping -l 1500 192.168.0.1` 1500 byte'lık veri gönderme.
- `ipv6config` IPv6 adreslerini gösterme.
- `optionalfeatures` Windows özelliklerini açar, program ekle/kaldır menüsüne girer.
- `ncpa.cpl` Network yönetimini açar.
- `nslookup/set type=all/kemalck.com` Gelişmiş DNS sorgusu.

## Server

- `dnscmd /clearcache`
  - Server tarafındaki DNS önbelleğini temizler.

- `sconfig`
  - Kısayoldan yapılacak ayarları yönetir.

- `dcgpofix /target:Domain`
  - Default policy'yi resetler.

- `gpresult /h C:\gpo_report.html`
  - GPO'ları çeker. `rsop.msc` ile de kullanılabilir.

- `netdom query fsmo`
  - DC'nin rollerini gösterir.
