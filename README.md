# KaanKny-INCEPTION

Tarayıcınızdan web sitesine erişmek istediğinizde, NGINX dışarıdan gelen isteği kabul eder ve ilgili web sayfasını sunmak için Wordpress servisine yönlendirir. Wordpress, gerekli içeriği MariaDB veritabanından alır ve dinamik olaral web sayfasını oluşturarark tarayıcınıza gönderir. Sonuç olarak, web sitesinin ön yüzü tarayıcınızda görüntülenir.

## TEMEL KAVRAMLAR

### İŞLETİM SİSTEMİ
İşletim sistemi (OS), bilgisayar donanımını yöneten ve bilgisayar kaynaklarını (CPU, bellek, disk sürücüleri, ağ bağlantıları vb.) kontrol eden temek bir yazılım sistemidir. İşletim sistemi, kullanıcılar ve uygulamalar arasında bir arayüz görevi görür, kaynakları etkili bir şekilde yönetir ve bilgisayarın genel performansını artırır.
İşetim sisteminin temek görevleri şunları içerir:
- Kaynak Yönetimi:
  - CPU, bellek, disk alanı gibi donanım kaynaklarını uygulamalar arasında adil bir şekilde paylaştırır.
  - İşletim sistemi, birden çok uygulama arasında geçiş yapma ve aynı anda çalışabilme yeteneği sağlar.
- Dosya Sistemi Yönetimi:
  - Verilerin depolanması ve organizasyonunu sağlar
  - Dosya sistemi, dosya ve klasörleri düzenler ve kullanıcıların verilere erişimini yönetir.
-İletişim ve Arabirim:
  - Bilgisayar kullanıcısı ile sistem arasındaki etkileişimi sağlar
  - Grafiksel veya komut satırı arabirimleri gibi kullanıcı arayüzleri sağlar.
- Güvenlik ve Erişim Kontrolü:
  - Bilgisayar sistemine güvenli bir şekilde erişim sağlar.
  - Kullanıcıların ve uygulamaların belirli kaynaklara erişimini kontrol eder.
- Hata Tespiti ve Hata Ayıklama:
  - İşletim sistemi, sistemde meydana gelen hataları tespit eder ve kullanıcılara veya sistem yöneticilerine bilgi verir.
  - Hata ayıklama ve kayıt tutma yetenekleri sunar.
- Ağ Yönetimi:
  - Bilgisayarın ağ iletişimini yönetir.
  - Veri iletimi, bağlantı yönetimi ve diğer ağ görevlerini yerine getirir.
- Sistem Kaynaklarının Kullanım ve İzlenmesi:
  - Bilgisayarın ağ iletişimini yönetir.
  - Veri iletimi, bağlantı yönetimi ve diğer ağ görevlerini yerine getirir.
  
