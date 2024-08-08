CD ile başlatıyoruz ve cmd konsolunu açıyoruz
disk de harf yok ise "DISK-HARF-ARAMA.md"

d:
cd Windows
cd System32
move utilman.exe utilman.exe.bak
copy cmd.exe utilman.exe
net user administrator /active:yes
shutdown -r -t 0
restartdan sonra sağ alt erişilebilirlere tıklıyoruz consol açılıyor
net user administrator "newpassword"
