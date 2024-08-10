Konular gelicek.
Firewall lar aslında UTM cihazları "Unified Threat Management" bunlar firewall dan gelişmiş cihazlar

Güvenlik
1-Virüs Koruması
2-Anti Spam
3-Data Loss Prevention -DLS
4-IPS/IDS Intrusion Prevention System
5-Intrusion Detection System
Neler Yapabiliyoruz;
VPN Yapabiliyoruz.
Bandwich management bant genişliğini düzenliyor.
Internet Load Balance - 
Web Filtering - Web sitelerini kategorize olarak yasaklama.
Log Raporlama - client bazlı loglama yapabiliyoruz.


Virüs Koruması (Antivirus):

Açıklama: Virüs koruması, ağ trafiğinde zararlı yazılımları (virüsler, solucanlar, trojanlar, vb.) tespit eden ve engelleyen bir güvenlik hizmetidir.

Nasıl Çalışır: Fortigate, gelen ve giden trafiği tarar ve bilinen zararlı yazılımları tespit etmek için imza tabanlı tarama tekniklerini kullanır. Ayrıca, bilinmeyen tehditleri tanımlamak için davranış analizi ve diğer gelişmiş teknikler de kullanılabilir.

Anti Spam:
Açıklama: Anti spam, istenmeyen ve zararlı e-postaların (spam) kullanıcıların posta kutularına ulaşmasını engelleyen bir güvenlik önlemidir.
Nasıl Çalışır: Fortigate, e-posta trafiğini analiz eder ve spam e-postaları tespit etmek için çeşitli filtreleme yöntemleri kullanır. Bu yöntemler arasında kara liste kontrolü, içerik analizi, ve gönderici doğrulama gibi teknikler yer alır.

Data Loss Prevention (DLP):
Açıklama: Veri kaybı önleme (DLP), hassas verilerin izinsiz şekilde ağdan çıkmasını engelleyen bir güvenlik stratejisidir.
Nasıl Çalışır: Fortigate, belirlenen veri türlerini (örneğin kredi kartı numaraları, kişisel bilgiler) tanımlar ve bu verilerin ağ dışına çıkışını engellemek için trafiği izler. Kural bazlı politikalar kullanılarak bu tür verilerin gönderilmesi engellenir veya raporlanır.

Intrusion Prevention System (IPS):
Açıklama: Saldırı önleme sistemi (IPS), ağdaki zararlı aktiviteleri tespit eden ve engelleyen bir güvenlik mekanizmasıdır.
Nasıl Çalışır: Fortigate, ağ trafiğini gerçek zamanlı olarak analiz eder ve zararlı etkinlikleri (örneğin, ağ saldırıları, kötü amaçlı trafik) tespit etmek için imza tabanlı ve anomali tabanlı algılama yöntemlerini kullanır. Tespit edilen tehditler otomatik olarak engellenir.

Intrusion Detection System (IDS):
Açıklama: Saldırı tespit sistemi (IDS), ağdaki zararlı aktiviteleri tespit eden ancak otomatik olarak engellemeyen bir güvenlik mekanizmasıdır.
Nasıl Çalışır: Fortigate, ağ trafiğini izler ve zararlı etkinlikleri tespit etmek için imza tabanlı ve anomali tabanlı algılama yöntemlerini kullanır. Tespit edilen tehditler hakkında uyarılar ve raporlar oluşturulur, ancak IDS bu tehditleri engellemez; bu görev, yöneticilerin müdahalesine bırakılır.

