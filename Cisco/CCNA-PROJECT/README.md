## BASIC CONFIGURATIONS[https://github.com/kemalcankrlsn/system-support-specialist-skills/blob/main/Cisco/CCNA-PROJECT/Basic-Configuration/SW-BASIC-CONFIG.md]
1. Navigating User Levels --- EN-CONFT User modları
2. Hostname --- cihaz adı router switch adı
3. Banner motd/message --- ilk giriş mesajı
4. Enable Password --- "en" parolası
5. Line console password --- telnet hattı 
6. Line VTY password --- telnet hattı parolası
7. Exec timeout --- işlemsizlik zamanı logout süresi
8. Logging Synchronous --- komut yazarken ekrana bilgi komutları gelmesi
9. Disabling ip domain lookup --- switch üzerinden dns search kaldırma normalde ctrl shift 6 ile kapatılıyor
10. IP domain name ---- ssh için sw router a ip domain name girilmesi
11. Username and password --- kullanıcı ve parolası oluşturma
12. Encrypting all passwords ---- şifrelerin config dosyalarına şifrelenerek kayıt edilmesi
13. Set Current Clock Time ---- sw router zaman girilmesi
14. Set management IP Address-SW ---- svı yapılandırılması router de loopback 0
15. Prevent Brute-force Attack-Router ---- bu sanırım ssh telneti kapatmak
16. Viewing Running & Startup Configs ---- sh run komutu
17. Saving running into startup configs ---- wr komutu

## SWITCHING TECHNOLOGIES
VLANs
VLAN Trunking Protocol- VTP
Trunk- Allowed/Denied VLANs
Configure Native VLAN
Remote Access- Telnet
Remote Access- SSH
L2 EtherChannel- PAGP/LACP
L2 EtherChannel- ON Mode
Secure All Unused Switchports
STP Attack Prevention
Disable CDP on the Devices
VLAN Hoping Attack Pevention
DHCP Snooping 
Dynamic ARP Inspection
IP Source Guard
Port Security
ACL for VTY interfaces