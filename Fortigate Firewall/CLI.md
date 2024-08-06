default şifreler
admin:boşluk


------------------------
Port Yapılandırmaları;
config system interface
edit port2
set mode static
set ip 192.168.18.1 255.255.255.0
set allowaccess ping http https
set status up --- portu up yapmak
end 
------------------------

ssh admin@<FortiGate_IP_Address> --- ssh çekme
get system status --- sistem bilgilerini görüntüleme
get system interface --- detaylı portları inceleme
show system interface --- detaysız port inceleme
get system interface physical ---- 1katman portları inceleme

execute backup config ftp <filename> <server_ip> <username> <password> Konfigürasyon Yedeği Alma:
execute restore config ftp <filename> <server_ip> <username> <password> Konfigürasyon Geri Yükleme:
execute ping <destination_ip> ping
execute traceroute <destination_ip> Traceroute

get system status | grep time --- sistem saatini göstermek
execute time  ---- sistem saatini görmek
show system ntp  ----- ntp durumunu görmek
diagnose sys ntp status ---- ntp serverları görmek 
-----------------------
ntp değiştirmek
config system ntp
    set ntpsync enable
    set type custom
    config ntpserver
        edit 1
            set server "0.pool.ntp.org"
        next
        edit 2
            set server "1.pool.ntp.org"
        next
    end
end
-----------------------




