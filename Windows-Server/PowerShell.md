Windows PowerShell

update-help ---- powershell güncellemek için
Get-service ---- servisleri görüntülemeye yarıyor
Get-Command *service* ---- içinde service komutu olan tüm komutları getir
$PSVersionTable.PSVersion ---- powershel sürümünü kontrol etme
Get-Service | where Status -eq "Running" --- get-service içinde statusu running olanları getir.
| ---- koşul 
Get-Service | where {$_.Name -like "a*" -and $_.Status -eq "Running"} --- name a ile başlayanlar ve statusünü running olanları getir
Get-EventLog -LogName Security -InstanceId 4624 ---- Oturum Açma Denetimlerini Almak:


Toplu Kullanıcı oluşturma, excel üzerinden;
https://www.firatboyan.com/active-directory-de-script-ile-toplu-kullanici-nesneleri-olusturma.aspx




