# Başlayalım:
## PowerShell ile Excel üzerinden toplu kullanıcı ekleme;

1. Excel oluşturulması Sütunlar: `Name	SamAccountName	GivenName	Surname	Initials	DisplayName	UserPrincipalName	Department	Description	Office	OfficePhone	EmailAddress	StreetAddress	POBox 	City	State	Country	PostalCode	Title	Company	Password	Path
`
![image](https://github.com/user-attachments/assets/6e7216bd-5daf-42f3-bc38-ec9572960037)
Şirketimizin vereceği kullanıcıları excele tek tek işleyelim ve "PATH" kısmı için devam edelim

2. ```cpp
Get-ADOrganizationalUnit -Filter 'Name -like "*"' | FT Name, DistinguishedName -A
``` komutu ile DC mizdeki tüm OU ları getirelim
3.  ' Get-ADOrganizationalUnit -Filter 'Name -like "*"' | where {$_.Name -like "*Department*"} | FT Name, DistinguishedName -A ' içerisinde Department olan ou name leri getirelim sadece
4.  ' Get-ADOrganizationalUnit -SearchBase 'OU=IT,OU=Users,OU=KEMALCK,DC=kemalck,DC=com' -SearchScope OneLevel -Filter * | FT Name, DistinguishedName -A ' IT ou su altındaki tüm ou ları getir
5.  







Kaynak: https://www.firatboyan.com/active-directory-de-script-ile-toplu-kullanici-nesneleri-olusturma.aspx
