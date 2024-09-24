## CISCO Kullanıcı Modları
- Switch> 					(User Executive Mode) 
- Switch#(enable) 				(Privileged Execute Mode)
- Switch(config)#(conf t) 			(Global Configuration Mode)
- Switch(config)#(interface GigabitEthernet0/0) 	(interface GigabitEthernet0/0 yapılandırması modu)
>
- enable - user privilege mode
- disable - user privilege mode dan çıkma

## Hostname
- Switch(config)#hostname DC-SW

## EKRANA UYARI
- Switch(config)#banner motd %			% 	= satırlara yazma

## Enable parolası:
- Switch(config)#enable password cisco (enable parolası belirledik.)

## Kullanıcı oluşturma:
- Switch(config)#username kemalcan secret cisco - user ve şifre oluşturma
- Switch(config)#username admin secret ciso - user ve şifre oluşturma

## Konsol Config ve Kablosu Güvenlik İşlemleri:
- Switch(config)#line console 0
- Switch(config-line)#password cisco
- Switch(config-line)#exec-timeout 3 30 
- Switch(config-line)#logging synchronous 
- Switch(config-line)#login --- login local dersek kullanıcı adı istiyor
- Switch(config-line)#end
> Bilgi: exec-timeout 3 30 = 3dakika30saniye işlem olmaz ise kapat.

## Switch SVI Ayarları:
- Switch>en
- Switch#conf t
- Switch(config)#interface vlan 1
- Switch(config-if)#ip address 192.168.1.11 255.255.255.0
- Switch(config-if)#no sh

## SWİTCH Genel Config Kodları:
- Switch#clock set 15:54:00 24 OCTOBER 2024 	--- zamanı ayarla
- Switch(config)#no ip domain-lookup ---Bilgi: Bu komut ile ip domain sorgusunu kapatıyoruz. CTRL+SHIFT+6 ile de sorgu esnasında kapatabiliyoruz.
- Switch(config)#ip default-gateway 192.168.1.1 --- Default Gateway
- Switch(config)#service password-encryption 		= ŞİFRELERİ KRİPTOLAMA

> Görünen kullanıcıların şifrelerini krittolama bunu yapmaz isek sh run da şifreler gözükür.

## SSH/LINE Hattı Ayarları:
- Switch(config)#ip domain name kemalck.local
- Switch(config)#crypto key generate rsa
- How many bits in the modulus [512]: 1024
- Switch(config)#line vty 0 4 (5 Aktif bağlantı aynı anda)
- Switch(config-line)#password cisco (telnet parolası)
- Switch(config-line)#exec-timeout 3 30 (3.30 dakika işlem olmazise sonlandır)
- Switch(config-line)#login local
- Switch(config-line)#transport input ssh
- Switch(config-line)#exit
- Switch(config)# ip ssh version 2
> IP SSH gücü 1024 normal 2048 daha güçlü kriptolama işlemi, ip ssh version 2 de güncel olan versiyon seçiyoruz.line vty de sonrasında da yazabiliriz.
> Not: Burada cisco cihazımızı rs232 portumuz console ile bağlandık ve interface vlan 1 yarattık ve ip adresi verdik line vty ile 0 kullanıcı girecek şekilde açtık ve telnet parolası verdik ve sonrasında "enable" parolası belirledik.
> "no exec-timeout" ile zaman sınırlandırmasını kaldırıyoruz.


## Ayarları Sw-Router Kayıt Etme
- Switch#copy running-config startup-config 		= running-config den startup config e kopyalama işlemi
- Switch#wr 


## SWİTCH Teknolojisi Kullanım:
- Switch# reload 					--- sw yeniden başlat
- Switch#reload --- cihazı yeniden başlatma
- Switch#end -- enable ekranına götürür
- Switch>exit veya Switch>logout --- cihazdan çıkış yapar


## SWİTCH SHOW Komutları:
- Switch# show clock 				        --- Cihaz Saatini görüyoruz
- Switch#show running-config               --- Running config görmek
- Switch#show startup-config             --- başlangıç dosyası görmek
- Switch#show ip interface brief --- Kısaca portların durumlarını gösteriyor.
- Switch#show mac-address-table --- iletişimde olduğu mac adres tablosunu görmek
- Switch#clear mac address-table --- temizleme
- DC-SW#show running-config | include username --- kullanıcıları görmek





