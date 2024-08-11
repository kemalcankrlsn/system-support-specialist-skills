## WSUS(Windows Server Update Services) Kurulum ve Yapılandırılması

1. ### 1. Adım :Kurulum Add Roles and Features
    - DNS Manager üzerinden 8.8.8.8 dns ekledik
    - WSUS Kurulumunu yapıyoru add roles and features tarafından ve deployment hatası almamak için 
    - Aşağıda bulunan "WSUS VersionCheck.sql Güncellenmesi" scriptini çalıştırmamız gerekmektedir.
    - Eğer yine hata alırsak "WSUS-Deployment-Failed.md" dosyasına bakalım.
2. Kurulum Tamamlandı yukarıdaki scripti çalıştırmadan post-deploymenti çalıştırmayalım bozuluyor.
3. WSUS Configuration Wizard ekranı bizi karşılıyor adımları geçiyoruz.
4. Clientler için GPO Ayarlanması Computer Configuration->Policies->Administratibe Templates->Windows Components->Windows Update->"Configure Automatic Updates" policy yazmak için Enable ediyoruz ve zaman ve otomatik kurulum seçeneklerini seçiyoruz.
5. "Specify intranet Microsoft update service location" giriyoruz ve WSUS Serverimizi giriyoruz. "http://wsus.kemalck.local:8530" örnek olarak bu seçilde giriyoruz.
"Automatic Updates detection frequency" clientler updateleri hangi aralıklarla kontrol etsin, "Always automatically restart at the scheduled time" kullanıcının updateyi ertelediği restart sayısını belirleme.
6. Computer Configuration->Policies->Administratibe Templates->System-> "Specify settings for optional component installation and componenet repair" WSUS seçiyoruz.







## WSUS VersionCheck.sql Güncellenmesi
 1. Yönetici olarak "runas" Powershell açıyoruz ve aşşağıdaki kodu çalıştırıyoruz.
 2. 
 ```  
Start-Process takeown.exe -ArgumentList '/f "C:\Program Files\Update Services\Database\VersionCheck.sql"' -Wait
Start-Process icacls.exe -ArgumentList '"C:\Program Files\Update Services\Database\VersionCheck.sql" /grant "administrator:(F)"' -Wait
(Get-Content "C:\Program Files\Update Services\Database\VersionCheck.sql") -replace "(^DECLARE @scriptMinorVersion\s+ int = \(11\)$)","DECLARE @scriptMinorVersion int = (51)" | Set-Content "C:\Program Files\Update Services\Database\VersionCheck.sql"
``` 
3. C:\Program Files\Update Services\Database\VersionCheck.sql dosyasındaki
```
DECLARE @scriptMinorVersion     int = (11)
```
bu satırın int (11) değeri 51 ile değiştiğini görüyoruz.


 - WSUS VİDEO 1: https://www.youtube.com/watch?v=GSdK1fc8BfM
 - WSUS VİDEO 2: https://www.youtube.com/watch?v=VTCzszyiFz4

## WSUS 0% SYNC Hatası:
1. WSUS kurulumundan sonra "Update Services -> WSUS" ana ekranında sync %0 da kalıyor yaptığım işlemleri not alıyorum.
2. Güvenlik duvarını kaldırdım.


## WSUS MANUEL IMPORT
1. Catalog update sitesinden indirilecek update nin id sini buluyoruz.
2. Yönetici olarak powershell ise açıyoruz
3. ImportUpdateToWSUS.ps1 dosyasını indirim C:\ altına koyuyoruz
4. "C:\ImportUpdateToWSUS.ps1 -UpdateId b0d64413-23af-486a-b29e-c02480fc871f"
5. Import sırasında "white error" hatası alırsak ;
``` 
Set-ItemProperty -Path ‘HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NetFramework\v4.0.30319’ -Name ‘SchUseStrongCrypto’ -Value ‘1’ -Type DWord

Set-ItemProperty -Path ‘HKLM:\SOFTWARE\Microsoft\.NetFramework\v4.0.30319’ -Name ‘SchUseStrongCrypto’ -Value ‘1’ -Type DWord

Restart-Computer 
```
6. WSUS Ekranına gelmiş oluyor onaylanması gereken güncelleme


- Script : https://github.com/kemalcankrlsn/system-support-specialist-skills/blob/main/Windows-Server/SCRIPT/ImportUpdateToWSUS.ps1 
- Yönergeler için : https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/manage/wsus-and-the-catalog-site
- Catalog Update: https://www.catalog.update.microsoft.com/Home.aspx
- White Error hatası : https://www.butsch.ch/post/wsus-importupdatetowsus-ps1-march-2024-security-update-dc-fails-srv-2019-and-2022-how-to-fix-all-steps/
- WSUS Manuel Update Cözümpark : https://www.cozumpark.com/powershell-ile-wsusa-guncelleme-paketi-yukleme/
- WSUS Clean Script : https://github.com/kemalcankrlsn/system-support-specialist-skills/blob/main/Windows%20Server/SCRIPT/WSUS-Cleanup.ps1
Kaynak: https://www.ajtek.ca/wsus/wsus-post-deployment-configuration-failed-windows-server-2022/
Kaynak: https://learn.microsoft.com/en-us/answers/questions/754982/windows-server-2022-wsus-fatal-error-the-schema-ve



## WSUS Kaldırılması:
 1. Remove Roles üzerinden "Windows Update Service" ve "Windows Inter Database WID" Kaldırdık
 2. C:\Windows\WID'yi kaldırın (özellikle: C:\Windows\WID\Data'daki SUSDB.mdf ve SUSDB_log.ldf'yi silin). Yeniden yüklemede WID rolünü ve dosyalarını kaldırmazsanız, aynı veritabanına yeniden bağlanacaktır.
 3. "C:\Program Files\Update Services" klasörünü silin.
 4. IIS'de, hala mevcutsa 'WSUS Yönetimi' web sitesini ve 'WsusPool' Uygulama Havuzunu kaldırın.
 5. WSUS-Cleanup.ps1 Dosyasını çalıştırın. runas yönetici olarak
 6.  ```  Remove-WindowsFeature -Name UpdateServices-WidDB  ``` kontrol ettik
 7. Yedekleme klasöründeki dosyaları kaldırdık "D:\WSUS" GİBİ
 8. > Bu kaldırma işe yaramadı :(

## WSUS Kurulumu Sonrası "Post-deployment Conf" Failed: Fatal Error: failed to start and configure the wsus service

1. Kurulum sonrasında post-deployment de failed alırsak tmp. dosyasına bakıyoruz.
2. "Fatal Error: failed to start and configure the wsus service" Hatası aldıysak 
3. ISS Den "wsuspool" ve "WSUS Administration" ilgili yerleri silip tekrar çalıştıroyuruz post deploymenti.





