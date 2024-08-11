## WSUS 2022 

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


## WSUS Kaldırılması:
 1. Remove Roles üzerinden "Windows Update Service" ve "Windows Inter Database WID" Kaldırdık
 2. C:\Windows\WID'yi kaldırın (özellikle: C:\Windows\WID\Data'daki SUSDB.mdf ve SUSDB_log.ldf'yi silin). Yeniden yüklemede WID rolünü ve dosyalarını kaldırmazsanız, aynı veritabanına yeniden bağlanacaktır.
 3. "C:\Program Files\Update Services" klasörünü silin.
 4. IIS'de, hala mevcutsa 'WSUS Yönetimi' web sitesini ve 'WsusPool' Uygulama Havuzunu kaldırın.
 5. WSUS-Cleanup.ps1 Dosyasını çalıştırın. runas yönetici olarak
 6.  ``` Remove-WindowsFeature -Name UpdateServices-WidDB ``` kontrol ettik
 7. Yedekleme klasöründeki dosyaları kaldırdık "D:\WSUS" GİBİ
 8. Kaynak : >**https://learn.microsoft.com/en-us/answers/questions/754982/windows-server-2022-wsus-fatal-error-the-schema-ve**





WSUS Clean Script : https://github.com/kemalcankrlsn/system-support-specialist-skills/blob/main/Windows%20Server/SCRIPT/WSUS-Cleanup.ps1

Kaynak: https://www.ajtek.ca/wsus/wsus-post-deployment-configuration-failed-windows-server-2022/

