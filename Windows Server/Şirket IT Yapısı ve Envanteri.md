# Şirket IT Yapısı ve Envanteri

## 1. Genel Yapı:
### İstanbul Lokasyonu:
- 150 çalışan
- Merkez ofis
- Ana veri merkezi

### Kocaeli Lokasyonu:
- 100 çalışan
- Yedek veri merkezi

## 2. Sunucu Yapısı:
### İstanbul Veri Merkezi:
#### Active Directory Sunucuları:
- **Primary Domain Controller (PDC)**
  - İşletim Sistemi: Windows Server 2022
  - Rol: AD DS, DNS, DHCP
- **Secondary Domain Controller (SDC)**
  - İşletim Sistemi: Windows Server 2022
  - Rol: AD DS, DNS

#### File Server:
- İşletim Sistemi: Windows Server 2022
- Rol: Dosya paylaşımı ve depolama

#### Application Server:
- İşletim Sistemi: Windows Server 2022
- Rol: Şirket içi uygulamalar (örneğin, ERP, CRM)

#### Exchange Server:
- İşletim Sistemi: Windows Server 2022
- Rol: E-posta hizmetleri

#### Backup Server:
- İşletim Sistemi: Windows Server 2022
- Rol: Yedekleme ve geri yükleme hizmetleri

### Kocaeli Veri Merkezi:
#### Active Directory Sunucuları:
- **Read-Only Domain Controller (RODC)**
  - İşletim Sistemi: Windows Server 2022
  - Rol: AD DS, DNS

#### File Server:
- İşletim Sistemi: Windows Server 2022
- Rol: Dosya paylaşımı ve depolama

#### Backup Server:
- İşletim Sistemi: Windows Server 2022
- Rol: Yedekleme ve geri yükleme hizmetleri

## 3. Çalışan Profilleri:
### Üst Yönetim:
- CEO
- CFO
- COO
- CIO

### Orta Yönetim:
- IT Müdürü
- Finans Müdürü
- İnsan Kaynakları Müdürü
- Satış Müdürü

### IT Ekibi:
- Sistem Yöneticileri (3 kişi)
- Ağ Yöneticileri (2 kişi)
- Yardım Masası Uzmanları (4 kişi)

### Diğer Çalışanlar:
- Finans Ekibi (20 kişi)
- İnsan Kaynakları Ekibi (10 kişi)
- Satış Ekibi (30 kişi)
- Üretim Ekibi (60 kişi)
- Pazarlama Ekibi (20 kişi)

## 4. IT Envanteri:
### Ağ Cihazları:
#### Router ve Switchler:
- Cisco ISR Router (İstanbul)
- Cisco Catalyst Switch (İstanbul ve Kocaeli)

#### Firewall:
- Fortinet FortiGate

#### VPN Cihazları:
- Cisco ASA VPN Cihazı

### Sunucu Donanımı:
#### İstanbul Veri Merkezi:
- Dell PowerEdge R740 (4 adet)
- Dell EMC Unity 300 (Storage)

#### Kocaeli Veri Merkezi:
- Dell PowerEdge R540 (2 adet)
- Dell EMC Unity 300 (Storage)

## 5. Windows Server Üzerinde Kullanıcı Oluşturma:
### Active Directory Kullanıcıları ve Grupları:
#### Organizational Units (OU):
- İstanbul
  - Users
  - Computers
- Kocaeli
  - Users
  - Computers

#### Kullanıcı Grupları:
- İstanbul Users
- Kocaeli Users
- IT Admins
- Finance
- HR
- Sales
- Marketing
- Production
