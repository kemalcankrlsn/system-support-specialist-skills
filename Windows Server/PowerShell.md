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





