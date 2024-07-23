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
Container teknolojisi, bu isim alanları ve kontrol grupları sayesinde uygulamaların birbirinden izole bir şekilde çalışmasını, kaynakların etkili bir şekilde kullanılmasını ve taşınabilirliği artırarar hızlı dağıtımı sağlar. Docker, Kubernetes ve diğer container platformları, bu özellikleri kullanarak containerlarınyönetimini kolaylaştırır ve geliştiricilere operasyon ekiperine esneklik sunar.

## Docker

Docker bir container tabanlı sanallaştırma platformudur vek ullanıcıya bir uygulamanın bağımlıklıklarını ve çalışma ortamının hafif taşınabilir bir container içinde paketlenmesini ve izole edilmiş bir şekilde çalıştırılmasını sağlar. İşte docker'ın temel özelliklerini ve avantajlarını vugulayan birleiştirimiş açıklama:
Docker, diğer sanal kanelerden farklı olarak, linux çekirdeği paylaşarak bağısız containerlar oluşturur. bu sanal işletim sistemini sifiran oluşturmak yerine, daha hızlı ve verimli bir şekilde sistemlerin kullanılmasını sağlar. bu sayede docker oladam bir sistem oluşturmak için gereken zorlu ve zaman laıcı süreçler ortadan kalkar.
Docker wen sitelerinin kurulumları, teslteri ve dağıtımları gibi iişlemlşeri hızlı ve kolay bir şekilde gerçekleştirmek içi kullanılır. Özellikle webmaster'lar için "Mevcut bilgisayarda çalışıp, sunucuda çalışmama" gibi sorunları ortadan kaldırır. Docker'ınn sağladığı izolasyon, uygulamarın herhangi bir ortamda tutuarluı bir şekilde çalışmasını sağlar.
Docker'ın temel avantajlarından biri, daha az sistem kaynağı tüketmesi sağlamasıdır. Geleneklesel sanal makinelerden farlı olarak Docker, contaileri ayrı bir işerim sistemi katmanı içermez ve Docker engine üzeirnden bir işletim sistemine erğşim sağlar. buda fahif ve hızlı containerin olıştumrnasını mümkün kılar.
Sonuç olarak docker uygulama gelitlirme, test etme ve dağıtma süreçlerinini hızlandıran, taşınabilr ve izole etilmiş containerlar sunan bir sannallaştırma çözümüdür.

Docker engine, uygulamarı containerlara paketleme ve dağıtma konusunda oldukça popüler olan contailerlaştırma teknolojisi sunar. bu yazılım geliştirme süreçlerini hızlandırabilir, uygulama bağımlılıkalrını izole edebilir ve farklı ortamlarda sorunsuz bir şekilde uygulamalar oluşturmayı kolaylaştırabilir.

## 

docker-compose.yml
```yml
version: "3.8" # versioyun 3.8 olarak ayarlıyoruz

services: # servislerimizi tanımlıyoruz
  mariadb: # mariadb servisimizi tanımlıyoruz
    container_name: mariadb # container ismini mariadb olarak belirliyoruz
    build: ./requirements/mariadb # build işlemi için gereken dosya yolunu belirliyoruz (mariadb klasörü içerisindeki Dockerfile dosyasını kullanacağız)
    env_file: # .env dosyasını kullanarak ortam değişkenlerini belirliyoruz
      - .env
    networks: # mariadb servisimizi inception adında bir ağa bağlıyoruz
      - inception
    volumes: # mariadb servisimizin verilerini saklamak için bir volume oluşturuyoruz (mariadb adındaki volume'u /var/lib/mysql dizinine bağlıyoruz)
      - mariadb:/var/lib/mysql
    restart: unless-stopped # mariadb servisimiz herhangi bir hata durumunda yeniden başlatılacak
  wordpress: # wordpress servisimizi tanımlıyoruz
    container_name: wordpress # container ismini wordpress olarak belirliyoruz
    build: ./requirements/wordpress # build işlemi için gereken dosya yolunu belirliyoruz (wordpress klasörü içerisindeki Dockerfile dosyasını kullanacağız)
    env_file: # .env dosyasını kullanarak ortam değişkenlerini belirliyoruz
      - .env
    networks: # wordpress servisimizi inception adında bir ağa bağlıyoruz
      - inception
    volumes: # wordpress servisimizin verilerini saklamak için bir volume oluşturuyoruz (wordpress adındaki volume'u /var/www/html dizinine bağlıyoruz)
      - wordpress:/var/www/html
    depends_on: # wordpress servisimizin çalışabilmesi için mariadb servisine bağlı olduğunu belirtiyoruz
      - mariadb
    restart: unless-stopped # wordpress servisimiz herhangi bir hata durumunda yeniden başlatılacak
  nginx: # nginx servisimizi tanımlıyoruz
    container_name: nginx # container ismini nginx olarak belirliyoruz
    build: ./requirements/nginx # build işlemi için gereken dosya yolunu belirliyoruz (nginx klasörü içerisindeki Dockerfile dosyasını kullanacağız)
    env_file: # .env dosyasını kullanarak ortam değişkenlerini belirliyoruz
      - .env
    ports:
      - "443:443" # nginx servisimizi dış ağa açmak için 443 portunu kullanacağız
    networks: # nginx servisimizi inception adında bir ağa bağlıyoruz
      - inception
    volumes: # nginx servisimizin konfigürasyon dosyalarını saklamak için bir volume oluşturuyoruz (nginx adındaki volume'u /etc/nginx/conf.d dizinine bağlıyoruz)
      - wordpress:/var/www/html
    depends_on: # nginx servisimizin çalışabilmesi için wordpress servisine bağlı olduğunu belirtiyoruz
      - wordpress
    restart: unless-stopped # nginx servisimiz herhangi bir hata durumunda yeniden başlatılacak

networks: # inception adında bir ağ oluşturuyoruz
  inception: # inception adındaki ağımızı tanımlıyoruz
    name: inception # ağımızın adını inception olarak belirliyoruz
    driver: bridge # ağımızın tipini bridge olarak belirliyoruz (bridge ağ tipi, container'ların birbirleriyle iletişim kurabilmesi için kullanılan bir ağ tipidir)

volumes: # mariadb ve wordpress servislerimizin verilerini saklamak için iki adet volume oluşturuyoruz
  wordpress: # wordpress adındaki volume'u tanımlıyoruz
    name: wordpress # volume'un adını wordpress olarak belirliyoruz
    driver: local # volume'un tipini local olarak belirliyoruz (local volume'lar, host makinemizde saklanan verileri container'larımızla paylaşmamızı sağlar)
    driver_opts: # volume'un bağlı olduğu dizini belirliyoruz
      type: none # volume'un tipini none olarak belirliyoruz (volume'un tipi none olursa, volume'un bağlı olduğu dizin host makinemizde olmalıdır)
      o: bind # volume'un bağlı olduğu dizin host makinemizde olmalıdır (bind tipi, volume'un bağlı olduğu dizini host makinemizde oluşturur)
      device: /home/kkanyilm/data/wordpress # volume'un bağlı olduğu dizini belirliyoruz
  mariadb: # mariadb adındaki volume'u tanımlıyoruz
    name: mariadb # volume'un adını mariadb olarak belirliyoruz
    driver: local # volume'un tipini local olarak belirliyoruz (local volume'lar, host makinemizde saklanan verileri container'larımızla paylaşmamızı sağlar)
    driver_opts: # volume'un bağlı olduğu dizini belirliyoruz
      type: none # volume'un tipini none olarak belirliyoruz (volume'un tipi none olursa, volume'un bağlı olduğu dizin host makinemizde olmalıdır)
      o: bind # volume'un bağlı olduğu dizin host makinemizde olmalıdır (bind tipi, volume'un bağlı olduğu dizini host makinemizde oluşturur)
      device: /home/kkanyilm/data/mariadb # volume'un bağlı olduğu dizini belirliyoruz
```

## MARIADB

### 50-server.cnf
```cnf
[mysqld]

user                    = mysql # user to run as
socket                  = /run/mysqld/mysqld.sock # socket file (for local connections)
port                    = 3306 # port to listen on
basedir                 = /usr # base directory (where the binaries are)
datadir                 = /var/lib/mysql # data directory (where the databases are)
log_error               = /var/log/mysql/error.log # error log file (where errors are logged)
expire_logs_days        = 10 # days to keep logs
character-set-server    = utf8mb4 # character set
bind-address            = 0.0.0.0 # bind address
```

### dtstart.sh
```sh
#!/bin/bash

service mariadb start # Mariadb servisini başlatıyoruz

sleep 3 # 3 saniye bekliyoruz (Mariadb servisinin başlaması için 3 saniye beklemek yeterli herhalde)

mariadb -e "CREATE DATABASE IF NOT EXISTS $MYSQL_DATABASE_NAME;" # Eğer veritabanı yoksa oluşturuyoruz
mariadb -e "CREATE USER IF NOT EXISTS '$MYSQL_USER'@'%' IDENTIFIED BY '$MYSQL_PASSWORD';" # Eğer kullanıcı yoksa oluşturuyoruz
mariadb -e "GRANT ALL PRIVILEGES ON $MYSQL_DATABASE_NAME.* TO '$MYSQL_USER'@'%';" # Kullanıcıya veritabanı üzerindeki tüm yetkileri veriyoruz
mariadb -e "FLUSH PRIVILEGES;" # Yetkileri güncelliyoruz
mariadb -e "SHUTDOWN;" # Mariadb servisini kapatıyoruz (Çünkü Mariadb servisi başlamış oluyor)

exec "$@" # Gelen komutları çalıştırıyoruz (bu durumda CMD ["mariadb"] olacak)
```
