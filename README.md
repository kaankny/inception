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
  - İşetim sistemi, sistem kaynaklarını (CPU kulllanımı, bellek tüketimi, disk allanı kullanımı) izler ve performansı optimize eder
İşletim sistemleri, farklı türlerde (Windows, Linux, macOS gibi) ve farklı cihazlarda (bikgisayar, mobil cihazlar gömülü sistemler) kullanılır. temel olarak, bilgisayarın düzgün çalışmasını sağlayan ve kullanıcıların ve uygulamaların bilgisayar kaynaklarına erişimini düzenleyen bir yazılım tabakasıdır.
Özet olarak işletim sistemi uygulamalar ile donanımlar arasında köprü görevi gören bir yazılımdır.

### KERNEL

Çekirdek (kernel), bir işletim sisteminin temel bileşinidir ve donanım ile yazılım arasındaki iletişimi yönetir. İşletim sistemi çekirdeği, bilgisayar donanımına doğdurdan erişim sağlar ve uygulamaların bu donanım kaynaklarını kullanması yönetir. Çekirdek, işletim sisteminin kalbidir.

Her uygulama için teorik olarak bir adet sunucu kurmam gerekir ve bunun dezavantajı bu uygulamalar sunucunun tüm gücünü 7/24 kullanamadığı için ortaya atıl bir kapasite sorunu çıkıyor. Atıl kapasite sorunu, "bir sistemde veya organizasyonda mevcut olan kaynakların tam anlamıyla kullanılmaması durumunu ifade eder. Bu durum, kaynakların potansiyel olarak daha etkili bir şekilde kullanılaileceği anlamına gelir. Atıl kapasite sorunu genellikle verimlilik eksikliği, kaynak israfı veya maliyet etkinliğinin düşük olması şekilde ortaya çıkar.
Atıl kapasite sorununa örnekler şunları içerebilir:
- İşgücü Kapasitesi:
  - Bir organizasyonda personel kapasitesinin tam kullanmaması durumu. Bir durum, iş süreçlerinin etkin bir şekilde planlanmamıs veya işgücü kaynaklarının yönetilmemiş olabileceği gösterebilir.
- Üretim Kapasitesi:
  - Bir üretim tesisinin maksimum kapasitesini kullanmaması. Bu durum, üretim süreçlerinin etkli bir şekilde planlanmamış olabilir.
- Bilgi Teknolojileri Kapasitesi:
  - Bilgisayar sistemlerinin veya sunucuların tam kapasitesiyle çalışmaması. Bu durum, bilgi teknolojileri altyapısının etkili bir şekilde planlanmamıs olabileceğini gösterir.
- Taşıma Kapasitesi:
  - Taşıma şirketlerinde araç filosunun tam kapasiteyle kullanılmaması durumu. Bu durum, lojistik süreçlerin etkili bir şekilde planlanmamış olabilir.
- Finansal Kaynak Kapasitesi:
  - Bir şirketin finansal kaynaklarının tam kapasiteyle değerlendirilmemesi durumu. Bu durum, şirketin yatırım fırsatlarınını değerlendirmede veya sermaye kullanımında etkili bir şekilde hareket etmememsi anlamına gelebilir.
Atıl kapasite sorunu, bir organizasyonun veya sistemin potansiyel değerini tam anlamıyla kullanamadığı bir durumu ifade eder. Bu durumun giderilmesi için etkin planlama, kaynak yönetimi ve sürekli iyileiştirme stratejileri geliştirilebilir. Bu sayede mevcut kaynaklar daha etklili bir şekilde kullanılır ve organizasyonun veya sistemin performansı artırılabilir.

Sanallaştırma, aynı donanımları kullanan birden fazla sanal makineyi birbirinden izole bir biçimde kullanmamıza yarayan teknolojidir.

Sanallaştırma, bilgisayar sistemlerinde fiziksel donanım kaynaklarının sanal makineler, konteynerler veya sanal ağlar gibi soyutlamalar aracılığıyla sanal ortamlarda çalışan birden çok işletim sistemi veya uygulama tarafından kullanılabilir hale getirilmesini ifade eder. Temelde, bir bilgisayarın donanım kaynaklarının mantıksal olarak bölünmesi ve izole edilmesi sürecidir. Bu bir bilgisayar sistemini daha verimli, esnek ve yönetilebilir hale getirir. İşte sanallaştırma kavramının temel bileşenleri:

- Sanal Makineler (Virtual Machines - VMs):
  - Sanal makineler, fiziksel bir bilgisayar üzerinde çalışan ve kendie işletim sistemine ve uygulamalarına sahip olan sanal ortamlardır. Bu sanal makienler, bir hypervisor (sanallaştırma yöneticisi) tarafından oluşturulur ve yönetilir.
- Hypervisor (Sanallaştırma Yöneticisi):
  - Hypervisor, fiziksel donanım üzerinde samal makineler oluşturan ve yöneten bir yazılımdır. Bu yazılım, sanal makienerlin birbirinden izole olmasını sağlar ve kaynakları etkili bir şekilde paylaştırır.
- Container:
  - Containerlar, sanal makienerlden daha hafif bir soyutlama sağlar. Her bir container, kendi işletim sistemini ve uygulamalarını içerir. ancak bir host işletim sistemi çekirdeiği paylaşır. Containerlar, hızlı başlatma, düşük sistem kaynağı tüketimi ve daha hızlı dağıtım avantajları sunar.
- Sanal Ağlar:
  - Sanallaştırma, sanal ağlar oluşturarak fakrlı sanal makinelerin veya containerların birbiriyle iletişim kurmasını sağlar. Bu fiziksel ağ altyapısına benzer bir yapı sağlar ancak sanal ortamlarda gerçekleşir.
- Kaynak Yönetimi ve Bölümlendirme:
  - Sanallaştırma , bilgisayar kaynaklarını (CPU, bellek, disk alanı) bölümlendirme ve izole etme yeteneği sunar. Bu, bir uygulamanın diğerlerini etkilemeden belirli bir miktar kaynağı kullanmabilmesini sağlar.

Sanallaştırma özellikle büyük veri merkezleri, bulut hizmetleri ve şirket içi ağ altyapıları gibi ortamlarda yaygın olarak kullanılır. Bu teknoloji, donanım kaynaklarını daha etkili bir şekilde kullanma, esneklik sağlama, iş sirekliliğini artırma ve uygulamarların daha hızlı bir şekilde dağıtılmasını mümkün kılma avanjatları sunar.

#

Artık birden fazla uygulamayı birbirinden izole kullanailiyoruz. Faakat günümüzde bu kullanımında artık bazı sıkıntılar çıkmaya başlıyor.

## CONTAINER

Containerlar, bir yazılım uygulamasının ve onun bağımlılıklarının, işletim sistemi düzeyinde izole bir ortamda çalıştırılmasını sağlayan bir sanallaştırma teknolojisidir. Containerlar, uygulamaların taşınabilirliğini, hızlı dağıtımını ve çevik geliştirme süreçlerini destekleyen bir çözümüdür.
Containler teknolojisi, özellikle Docker gibi opüler araçlar tarafından yaygın olarak kullanılmamaktadır. Containerlar, aşşağıdaki temel özellikler sahiptir:
- İzolasyon:
  - Her bir container, kendi dosya sistemini, ağ bağlantısını ve süreçlerini çerir. Bu br containerin çalışma zamanında diğer containerlardan izole olmasını sağlar. Ancak tam izolasyon seviyesi sanal makineler kadar yüksek değildir.
- Hafif ve Hızlı:
  - Containerlar, işletim sistemi çekirdeğini paylaştıkları için daha fafi ve hızlıdır. Her bir container, uygulama ve bağımlılıkarlnı içeren bir görüntünden oluşur ve bu görüntü, tüm gereksinimleri içerdiği için hızlı bir şekilde başlatılabilir.
- Taşıabilirlik:
  - Containlar, uygulama ve bağımlılıklarını birleştiren bir "container görüntüsü" kullanır. Bu görüntü, bir uygulamının tüm gerekli bileşenleri içerir ve farklı ortamlarda (gelitşrme, test, üretim) aynı şekilde çalışabilir. Bu da uygulamaın kolayca yaşınabilir ve çevik bir şekilde geliştirilebilri olmasını sağlar.
 
### FARKLARI
Containerlar ve sanal makineler benzer temel amaca sahip olmalarına rağmen, çalışma prensipleri ve tasarımları açısından önemleri farklara sahiptirler. İşte bu iki sanallaştırma teknolojisi arasındaki temel fakrlar:
- İzolasyon Seviyesi:
  - Sanal makineler: Sanal makineler, her bir kendi işletim sistemini içeren tam bir sanal ortam sağlar. bu her sanal makinenin kendi çekirdeği ve belleği ve dosya sistemine sahip olması anlamına gelir.
  - Containerlar: Containerlar, işletim sistemi çekrdeiği paylaşan gafif ve izole edilmiş ortamlardır. Her bir container, kendi dosya sistemini, kullanıcı alanını ve süreçlerini içerir, ancak işletim sistemi çekirdeği paylaşıldığı içi daha hafif ve hızlıdr.
- Performans:
  - Sanal Makineler: Sanal makineler, daha ağır oldukları için daha fazla kaynağa ihtiyaç duyarlar. Tam bir işletim sistemi içerdiği için başlatılması daha uzun sürebilir ve daha fazla bellek kullanabilir.
  - Containerlar: Containerlar daha hafif ve daha hızlıdr. İşletim sistemi çekirdeği paylaşıldığı için daha az bellek tüketirler ve çok daha hızlı başlatılıp durdurulabilirler.
- Birbirinden İzole Edilmesi:
  - Sanal makineler: Sanal makineler, daha güçlü bir ozalosyon sağlar ve bir sanal makinedeki güvenlij açığı, gider sanal makienleri etkilemez.
  - Containerlar: Containerlar, daha hafif izolasyon sağlar. İşletim sistemi çekirdeği paylaşıldığı için bir containerdaki bi sorun diğerlerini etkileyebilir.
- Yedekleme ve Dağıtım:
  - Sanal makineler: Sanal makineler yedeklenmesi ve taşınması genellikle karmalıktır. Tam bir işletim sistemi içerdiği için dosya boyutlarıda büyüktür.
  - Containerlar: Containerlar, hızlı ve kolay şekilde yedeklenebilir ve taşınabilir. Dosya boyutu küçüktür.
Sonuç olarak her teknoloji kendi avantajları ve kullanım seneryolarına sahiptir. Sanal makineler, daha kapsamlı izolasyon ve bağımsızlık sağlamak için kullanılırken, containerlar daha fafif ve hızlı dağıtım için tercih edilmektedir.

#

Artık tek bir işletim sistemi üzerinde birbirinden izole birden fazla uygulama var bu şekilde processleri koyduk ve çalışması için tüm ek paketler var ama işletim sisteminin kaynakları, özellikleri yok. artık bu 2 paket izole bir process olarak çalışıyor.

- Namespaces (isim alanları):
  - isim alanları, işletim sistemi içindeki farklı türde kaynakları özole etmek ve her bir containeri kendi sanal ortamında oluşturmak için kullanılır. Bu bir containerın diğer containerdan ve ana işletim sisteminde özole olasını sağlar. Başlıca namespcaes şunları içerir:
    - PID: Süreç izolasyonu sağlar
    - Network: Ağ kaynakları izolasyonu sağlar
    - Mount: Dosya sistemi izolasyonu sağlar
    - IPC: Süreç iletişim izolasyonu sağlar
    - UTS: Sistem adı izolasyonu sağlar
    - User: Kullanıcı alanı izolasyonu sağlar.

- Control Groups (Kontrol Grupları):
  - Kontrol grupları, bir grup sürecin kullanılabileceği kaynakları sınırlamak, izlemek ve önceliklendirmek için kullanılır. Bu bellek, CPU, ağ bant genişliği gibi kaynakların etkin bir şekilde yönetilmesini sağlar.
  - Kontrol grupları, kaynakların adil bir şekilde paylaşılamsını ve aşırı taleperlin diğer süreçleri etkilememsini sağlar.


