## SWİTCH Genel Config Kodları:
- Switch# clock set 08:10:50 29 August 2023 	--- zamanı ayarla
- Switch# reload 					--- sw yeniden başlat
- Switch(config)#no ip domain-lookup ---Bilgi: Bu komut ile ip domain sorgusunu kapatıyoruz. CTRL+SHIFT+6 ile de sorgu esnasında kapatabiliyoruz.
- Switch(config)#ip default-gateway 192.168.1.1 --- Default Gateway
- Switch#end -- enable ekranına götürür
- Switch>exit veya Switch>logout --- cihazdan çıkış yapar
- Switch#reload --- cihazı yeniden başlatma


## CISCO Kullanıcı Modları
- Switch> 					(User Executive Mode) 
- Switch#(enable) 				(Privileged Execute Mode)
- Switch(config)#(conf t) 			(Global Configuration Mode)
- Switch(config)#(interface GigabitEthernet0/0) 	(interface GigabitEthernet0/0 yapılandırması modu)
>
- enable - user privilege mode
- disable - user privilege mode dan çıkma

# SIRASIYLA ; >
## Hostname
- Switch(config)#hostname DC-SW

## EKRANA UYARI
- Switch(config)#banner motd %			% 	= satırlara yazma

## Konsol Config ve Kablosu Güvenlik İşlemleri:
- Switch(config)#line console 0
- Switch(config-line)#password cisco
- Switch(config-line)#exec-timeout 3 30
- Switch(config-line)#login local
- Switch(config-line)#end
> Bilgi: exec-timeout 3 30 = 3dakika30saniye işlem olmaz ise kapat.

## Kullanıcı oluşturma:
- Switch(config)#username kemalcan secret cisco - user ve şifre oluşturma
- Switch(config)#username admin secret ciso - user ve şifre oluşturma

## Enable parolası:
- Switch(config)#enable password cisco (enable parolası belirledik.)


## Switch Telnet Ayarları:
- Switch>en
- Switch#conf t
- Switch(config)#interface vlan 1
- Switch(config-if)#ip address 192.168.1.11 255.255.255.0
- Switch(config-if)#no sh
>
- Switch(config)#line vty 0 4 (5 Aktif bağlantı aynı anda)
- Switch(config-line)#password cisco (telnet parolası)
- Switch(config-line)#exec-timeout 3 30 (3.30 dakika işlem olmazise sonlandır)
- Switch(config-line)#login local (login ile bu girişi açıyoruz.)
- Switch(config-line)#exit

> Not: Burada cisco cihazımızı rs232 portumuz console ile bağlandık ve interface vlan 1 yarattık ve ip adresi verdik line vty ile 0 kullanıcı girecek şekilde açtık ve telnet parolası verdik ve sonrasında "enable" parolası belirledik.

> "no exec-timeout" ile zaman sınırlandırmasını kaldırıyoruz.

## Telnet ve Console den geçen Şifreleri Kriptolama
- Switch(config)#service password-encryption 		= ŞİFRELERİ KRİPTOLAMA
> Görünen kullanıcıların şifrelerini krittolama bunu yapmaz isek sh run da şifreler gözükür.



## SSH Ayarları:
- Switch(config)#ip domain name kemalck.local
- Switch(config)#crypto key generate rsa
- How many bits in the modulus [512]: 1024
- Switch(config)#line vty 0 4
- Switch(config-line)#password cisco (telnet parolası)
- Switch(config-line)#exec-timeout 3 30 (3.30 dakika işlem olmazise sonlandır)
- Switch(config-line)#login local
- Switch(config-line)#transport input ssh
- Switch(config-line)#exit
- Switch(config)# ip ssh version 2
> IP SSH gücü 1024 normal 2048 daha güçlü kriptolama işlemi, ip ssh version 2 de güncel olan versiyon seçiyoruz.line vty de sonrasında da yazabiliriz.



## Ayarları Sw-Router Kayıt Etme
- Switch#show running-config 				= YAPTIĞIMIZ "RAM" KAYITLI YAPTIĞIMIZ İŞLER
- Switch#show startup-config 				= ROM kayıtlı işlerimiz yani 
- Switch#copy running-config startup-config 		= running-config den startup config e kopyalama işlemi
-  Switch#wr 


## BAŞLANGIÇ SWİTCH AYARLARI:
en
conf t
hostname DC-SW
banner motd !GIRIS YASAK!
line console 0
password cisco
exec-timeout 3 30
login local
exit
username kemalcan secret cisco
username admin secret cisco
enable password cisco
interface vlan 1
ip address 192.168.1.11 255.255.255.0
no sh
exit
ip default-gateway 192.168.1.1
service password-encryption
ip domain name kemalck.local
crypto key generate rsa
1024
line vty 0 4
password cisco
exec-timeout 3 30
login local
transport input ssh
exit
ip ssh version 2
end
wr




