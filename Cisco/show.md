## SWİTCH SHOW Komutları:
- Switch# show clock 				        --- Cihaz Saatini görüyoruz
- Switch#show running-config               --- Running config görmek
- Switch#show startup-config             --- başlangıç dosyası görmek
- Switch#show ip interface brief --- Kısaca portların durumlarını gösteriyor.
- Switch#show mac-address-table --- iletişimde olduğu mac adres tablosunu görmek
- Switch#clear mac address-table --- temizleme
- Switch#show interfaces vlan1 --- vlan bazlı bilgileri görmek
- DC-SW#show running-config | include username --- kullanıcıları görmek




## ROUTER Show Komutları:
- Router#show ip route --- route tablosunu görüyoruz.
R1# show ip interface brief
R1# show ipv6 interface brief
R1# show ip route
R1# show ipv6 route
R1# show interfaces gig0/0/0
R1# show ip interface g0/0/0
R1# show ipv6 interface g0/0/0



## WINDOWS Show Komutları
- arp -a --- arp tablosunu görüyoruz.
> Yani IP Adreslerine ilişkili MAC adreslerini görüyoruz.
- netstat -r
> router tablosu dışarı ile haberleşme hangi interface kartı kim nere ile konusur
- ipconfig /displaydns
> komutu yalnızca önceden çözümlenmiş DNS girişlerini görüntüler. 
- nslookup google.com --- bize google.com un ip adresini verir.
