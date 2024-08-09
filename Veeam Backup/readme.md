# Yapılan İşlemler

1. **Kurulum:**
   - Lisanslama işlemlerini gerçekleştirdik.
   - Servisleri başlattık.
   - Eğer sanallaştırma mimarilerini kullanıyorsak "Virtual Infrastructure" bölümünden ekleme yaptık.
   - Tek bir makine eklemek için "Physical Infrastructure" olarak ekleme yapıyoruz.

   > **Not:** En düşük sistem gereksinimleri: 100GB SSD Disk Cache, 4 çekirdekli işlemci, 16GB RAM. Bu gereksinimlerin altındaki sistemlerde düzgün çalışmadı.

2. **Ortamın Eklenmesi (Fiziksel Makine veya vCenter):**
   - Ortamın eklenmesi için Ana menü üzerinden Inventory-> "Virtual Infrastructure" kısmında sağ tıklayarak `Add Server -> VMware vSphere` seçeneği ile vCenter ortamımızı ekleyebiliyoruz.
   - Veya `Physical Infrastructure -> Create Protection Group` oluşturarak:
     - **Individual Computers:** Sunucu, server veya PC'lerimizi tek tek ekleyebiliriz.
     - **Microsoft Active Directory Object:** Domainimizin Computer kısmını veya doğrudan domaini, server computers, domain controller olarak ekleyebiliriz. Sürekli güncellenmesini de sağlayabiliriz.
     - **Discovery İşlemi:**
   - Günlük veya belirlediğimiz saatlerde cihazlarımızı taramak için "Rescan" yapıyoruz. Bu işlem, offline olan cihazların tespit edilmesi ve bulunması için kullanılır.
   **Review:**
   - Yedekleme yapılacak cihazlara kurulacak servisleri görüntüleyebiliriz.

3. **Repository Ekleme**
    - Backup Infrastructure-> Backup Repositories -> Add backup repository
    altınan "Direct atached stroge" olarak direkt disklerimizi ekleyebiliyoruz veya "Network Atached stroge" olarak paylaşımlı uzak file dosya sistemlerini ekleyebiliyoruz.

    - "Backup Infrastructure" altında "Backup Repos" kısmından yedek alınacak yeri seçiyoruz (NAS cihazı, file server veya iSCSI olarak ekleyebiliyoruz).

    > **Not:** "Mount server" mount server SSD olan diskde olmalı cache bellek yani review ve apply de disklerimini configure ediyor.


4. **JOB Oluşturma**
    - Yedekleme işleri için yeni bir job oluşturuyoruz.

5. **Backup Restore**
    - Alınan yedeklerin geri yüklenmesi işlemi burada yapılır.

6. **Backup Restore İşlemleri**
    - asd
