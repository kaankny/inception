# INCEPTION

## KERNEL

- işletim sistemi bilgisayar donanımı ile uygulamalar arasında köprü görevi gören temel yaazılımlardır.
- işletim sisteminin temel görevini KERNEL yapar.
- KERNEL işletim sisteminin kalbidir.
- BİOS devreye girer, donanımı test eder bootloader açılır. Bootloader, işletim sistemi çekirdeği (KERNEL) yüklenir. Yani KERNEL işletim sisteminin kendisidir diyebiliriz.
- Notepad'de diske kaydetme işlemini aslında KERNEL yapar.

## SANALLAŞTIRMA

- Sunucu sipariişi ver (6 - 8 Hafta) -> Sunucuyu fiziksel olaral kur (1-2 hafta) -> işletim sisteimi ve uygulamayı kır (1-3 gün) 3 aylık süreç. Bu durumun önüne geçmek için sanallaştırma icat edildi. Sanallaştırma yazılımı sayesinde bir fiziksel sunucuda birden fazla çalışan sanal makineler bulunur. Kaynaklar ortak kullanılır.

## CONTAINER

- Container sayesinde bir işletim sisteminde birden fazla process birbirinden bağımsız ve izole çalışır. 2013'e kadar bu yöntem kullanıldı.
- Namespaces sayesinde o sistem içerisindeki processleri birbirinden izole etmeyi sağladık. Birbirinden habersiz çalışırlar.

## DOCKER

- Makineye container yükleyen program olarak başladı.
- Doceker, bir cantainerlaştırma teknolojisi olarak adlandırılır. Containerlar, uygulamaları ve onların bağımlılıklarını bağımsız ve izole bir ortamda çalıştırmak için kullanılır. Bir Docket containeri, tüm uygulama kodunu, kütüphanelerini ve konfikürasyon dosyalarını içerir.
- Açık kaynak kodludur.

## IMAGE VE CONTAINER

- Bir java uygulaması için aşşağıdan yukarıya sırasıyla yüklenmesi gerekenler.
- Image içinde bulunduğu sistemin kernelini kullanır bu yüzden kernel a ihtiyacı yoktur. inage bir şablondur. yaratırsın. Conatainer ise bu şablonun çalışır halidir. İmage bir okunabilir anaşablondur. Container bu şablondan oluşturulmuş çalışan bir kopyadır.
 
## CONTAINER VE SANAL MAKINE ARASINDAKI FARK

- VM işetim sistemi izslashonu sağlar. Container uygualam izolosyanou sağlar.
- Container VM'e göre çok daha hızlı çalışır.
- Container VM'e göre daha taşınabilir. Image halinde taşınarak her yerde aynı şekilde çalışır.

## CONTAINER TEMELLERI

- Her container imajında, o imajdan bir container yarattığımız zaman varsayılan olarka çalışması için ayarlanmış bir uygulama vardır.
- Bu uygulama çalıştığı sürece container ayakta kalır.
- Uygulama çalışmayı bıraktığında Containerda kapatılır.
- Docker image'i dediğimiz şey ayrı ayrı katmanlardan oluşan, birleşince anlamlı bir objeye dönüşen şeydir.
- Image ile container oluşturduğumuzda, container içinde sadece okunabilir salt okunur ( CMD /myapp/hello.sh || /myapp/hello.sh || /bin /etc /lib /mnt / opt /root /sbin /sys /usr /dev /home /media /proc /run /srv /tmp /var) katmanlarını getirir. Bu image ile bir container oluşturunca bize yazılabilir bir katman verir ve biz bu katman üstünde değişiklikler yaparız. Container üstünde yaptığımız değişiklikler o container'a özeldir. Aynı image ile başka bir container oluşturunca az önce gösterdiğim katmanlar aynen gelir ve üstüne yine bir yazılabilri katman gelir. Yani bir container içinde üstünde değişiklik yaptığımızda, image dosyasında değişiklik yapıyoruz.
- UNION FILE SYSTEM ile container içerisindeki tüm katmanları aynı anda görmemize yarayan sistemdir.
- UNION FILE SYSTEM sayesinde hem hız hemde depolama tasarufu yapıyoruz.

## DOCKER CONTAINER YASAM SURECI

- Container tek bir uygulama çalıştırmak için oluşturulur.
- Containerlar bu tek uygulamanın çalışması için gerekli tüm gereksinimlerin önceden hazırlandığı içage dediğimiz objelerden yaratılır. Contanerla ilgili tüm gereksinimler imaj seviyesinde tamamlanmış olması beklenir.
