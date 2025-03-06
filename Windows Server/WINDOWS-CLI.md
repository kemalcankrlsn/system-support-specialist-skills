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
- `cleanmgr` Disk kurtarma alanı
- `winver` windows versionu gösterir
- `systeminfo` cmd den bu kodu girince detaylı windows versiyonu ve pc bilgileri
- `gpresult /h C:\gpo_report.html` GPO'ları çeker. `rsop.msc` ile de kullanılabilir.
- `curl ip.sb` DIŞ Private ip adresi öğrenme 

## Windows Network Ağ İzleme
- "Resource Monitor" ile kısmi ağ izleme yapabiliriz, Kaynakların network aktiviteleri, Network activity, TCP bağlantıları, Listening Ports
- "netstat -ano" - Bu komut, mevcut tüm ağ bağlantılarını, protokollerini, yerel ve uzak adresleri, bağlantı durumunu ve ilgili işlem kimliğini (PID) gösterir.
- "netstat -anob 5" Bu komut her 5 saniyede bir güncellenen bir bağlantı listesi sağlar.
- Wireshark
- "Get-NetTCPConnection | Format-Table -Property State, LocalAddress, LocalPort, RemoteAddress, RemotePort, OwningProcess" Powershell üzerinden listeleme
- "while ($true) {Get-NetTCPConnection | Format-Table -Property State, LocalAddress, LocalPort, RemoteAddress, RemotePort, OwningProcess; Start-Sleep -Seconds 5}
" Powershell üzerinden sürekli izleme





# WINDOWS PowerShell Komutları

update-help ---- powershell güncellemek için

Get-service ---- servisleri görüntülemeye yarıyor

Get-Command *service* ---- içinde service komutu olan tüm komutları getir

$PSVersionTable.PSVersion ---- powershel sürümünü kontrol etme

Get-Service | where Status -eq "Running" --- get-service içinde statusu running olanları getir.

| ---- koşul 

Get-Service | where {$_.Name -like "a*" -and $_.Status -eq "Running"} --- name a ile başlayanlar ve statusünü running olanları getir

Get-EventLog -LogName Security -InstanceId 4624 ---- Oturum Açma Denetimlerini Almak:

OU=IT,OU=Users,OU=KEMALCK,DC=kemalck,DC=com ---- AD deki tüm kullanıcıları getirme

`Get-ADOrganizationalUnit -Filter 'Name -like "*"' | FT Name, DistinguishedName -A` komutu ile DC mizdeki tüm OU ları getirelim

`Get-ADOrganizationalUnit -Filter 'Name -like "*"' | where {$_.Name -like "*Department*"} | FT Name, DistinguishedName -A` içerisinde Department olan ou name leri getirelim sadece

`Get-ADOrganizationalUnit -SearchBase 'OU=IT,OU=Users,OU=KEMALCK,DC=kemalck,DC=com' -SearchScope OneLevel -Filter * | FT Name, DistinguishedName -A` IT ou su altındaki tüm ou ları getir

Update-Help -Verbose -Force -ErrorAction SilentlyContinue ---- Verbose bilgi veriyor force zorla error action slient hataları geçiyor





## Server

- `dnscmd /clearcache`
  - Server tarafındaki DNS önbelleğini temizler.

- `sconfig`
  - Kısayoldan yapılacak ayarları yönetir.

- `dcgpofix /target:Domain`
  - Default policy'yi resetler.



- `netdom query fsmo`
  - DC'nin rollerini gösterir.


netsh interface show interface - Ağ Bağlantılarınızı Listeleyin
netsh interface set interface "Bağlantı_Adı" admin=enable - Belirli Bir Ağ Bağlantısını Aktif Etme
netsh interface set interface "Bağlantı_Adı" admin=disable - devre dışı




https://www.donanimhaber.com/windows-cmd-komutlari-ve-kodlari--160039
