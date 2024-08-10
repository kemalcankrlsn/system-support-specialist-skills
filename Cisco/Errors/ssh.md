------------------------------------
Merhabalar router a ssh yapmak istedik aşağıdaki hatayı aldık.

"Unable to negotiate with 192.168.1.15 port 22: no matching key exchange method found. Their offer: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1"

Çözüm 1: SSH İstemcisine Uyumlu Algoritmalar Eklemek

```
ssh -o KexAlgorithms=+diffie-hellman-group14-sha1 admin@192.168.1.15
```
ssh -o KexAlgorithms=+diffie-hellman-group-exchange-sha1 admin@192.168.1.15

Router Tarafında;
RouterName(config)# ip ssh server algorithm mac hmac-sha2-256 hmac-sha2-512
RouterName(config)# ip ssh server algorithm encryption aes256-ctr aes192-ctr aes128-ctr
------------------------------------


------------------------------------
SSH KOMUTLARI:
ssh kullanıcı_adı@sunucu_adresi
ssh -i /path/to/private_key kullanıcı_adı@sunucu_adresi ---- Özel Anahtar ile Bağlantı Kurma
ssh -p 22 admin@192.168.1.15 --- 22 portu ile bağlan
exit ----- bağlantıyı sonlandırma
ssh -v admin@192.168.1.15
------------------------------------


SHOW KOMUTLARI:
Router# show ip ssh

