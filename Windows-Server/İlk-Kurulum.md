ADIM ADIM SERVER KURULUMU CONFİG
1.	Server kurulumu yaptın
2.	Server/Bilgisayar İsmi Değiştir ( Kullanım amacı ne olacaksa ismini öyle ver) DCSRV
3.	Lisanslama yapın
4.	Server Manager Açtın
5.	“Server Roles > AD DS Active Directory Domain Services” Add Features diyip kuracağı diğer eklentileri de kabul ediyoruz. Features de “Group Policiy Management” var. Restart Diyip kurulum için reset atmasını bekliyoruz.
6.	Restart Atıltıktan sonra Active Directory Domain Services Conf Wizard ekranını açıyoruz Sağ üst uyarılardan geliyor
7.	Sırasıyla Forest > Tree > Child 
8.	“Add a new forest” diyoruz
9.	İnternete açacaksak “.com” açmayacaksak “.local”
10.	“Domain Controller Options” Forest Function level = Forest içerisinde sürümü düşük server varsa seçiyoruz ona göre ayarlıyor DC
11.	DNS = IP leri isme isimleri IP çevirme.
12.	Read only domain controller (RODC) = 1 Domain var o domaine 1 adet DC daha oluşturmak istiyoruz ve sadece okuma yapabilme yetkisi vermek için Yani sadece okuma yapacak bi controller oluşturma.
13.	DSRM Directort Services Restore Mode = Kurtarma şifresi 
14.	NetBIOS = DNS in eski adı eski dns servisi diyebiliriz.
15.	Yeniden başlatılıyor. Admin girişi yapıyoruz.
16.	Domain e alma “Etki Alanı”

