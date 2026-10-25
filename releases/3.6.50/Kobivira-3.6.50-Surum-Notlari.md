# Kobivira 3.6.50 — Otomatik e-postalar

Yalnız 3.6.49 üzerine yönetimden yüklenen imzalı güncellemedir. 3.6.49'un canlıda kurulu olduğu varsayılmamıştır; kurulu sürümü önce kontrol edin. Mevcut tam sistem/hosting yedeğini koruyun. ZIP açılmadan Sistem > Sürüm güncellemeleri alanından yüklenir. Yeni kurulum, dosya taşıma veya SMTP şifresi değişikliği gerekmez.

## Yönetim
Mevcut Sistem > E-posta / SMS gönderimleri sayfasına Otomatik hesap e-postaları, konu/metinler, mevcut firmaya başlangıç bildirimi ve son otomatik gönderimler bölümleri eklendi. Mevcut SMTP/Netgsm ve doğrulama alanları yerinde kaldı. Genel ve tür bazlı aç/kapat, düşük kontör günlük hatırlatma seçeneği vardır. Konu/metin alanlarında listelenen değişkenler kullanılabilir; zorunlu olay bilgileri çıkarılamaz. Metin HTML kodu olarak çalıştırılmaz. Gerçek düğme bağlantıları sistem tarafından eklenir.

Varsayılan: otomatik e-postalar ve türler açık, düşük kontör günlük hatırlatma kapalı. Geçmiş kayıtlar otomatik hoş geldiniz e-postasına dönüştürülmez. Doğrulanmış firma yöneticisine yönetimden bir kez başlangıç bildirimi oluşturulabilir. Telefon bekliyorsa E-posta doğrulandı bildirimi; gerçek telefon doğrulaması tamamlandıysa Hoş geldiniz seçilir. Test telefon bayrağı gerçek doğrulama değildir. Bu işlemler eski üyelerin erişim haklarını değiştirmez.

## İşleyiş
İşlem sonuçları ve olay kaydı aynı veritabanı transaction'ında tutulur. SMTP çağrısı bu transaction'da yapılmaz. Ödeme hatası veya rollback olmuş kayıt e-posta üretmez. Doğrulanmış ve halen etkin firma yöneticisi e-postası kullanılır; adres değiştiyse eski kuyruk iptal edilir. Firma silinmesi, askı ve devam eden firma silme süreci gönderimi engeller.

PayTR paket e-postası yalnız mevcut imza/tutar/test-canlı doğrulamasından geçmiş gerçek aktivasyonda oluşur. Başarılı dönüş sayfası tek başına e-posta veya aktivasyon üretmez. Tekrarlanan callback aynı olay e-postasını çoğaltmaz. Havale bildirimi onay bekliyor e-postası oluşturur; gerçek yönetici onayı ayrı aktivasyon olayıdır. Kontör kart satışı veya yeni EDM akışı açılmamıştır. Kontör e-postası, gerçekten credit_ledger'a kaydedilen pozitif yerel hareketten oluşur; EDM yüklemesi olarak sunulmaz. Aynı aktivasyon/kontör olayı için eski genel e-posta uyarısının ikinci ileti oluşturması önlenir; panel/SMS bildirimleri korunur.

Düşük bakiye eşiği 25'in altıdır: 25'te uyarı yoktur, 24 ve 0 dahildir. Günlük kapalıysa her yeni eşik altına düşüşte bir kez; açıksa Türkiye takvim gününe göre günde bir kez. Bakiye 25'e çıkınca bekleyen düşük uyarılar iptal edilir. Tekrar düşüş ayrı olaydır. E-postada mevcut kontör bilgi ekranına bağlantı vardır; çalışmayan kart satın alma vaadi yoktur.

Ücretli paket sonuna 7 gün ve altında günde bir bildirim; sona ermede aynı bitiş için bir olay. Yenileme/paket değişikliği veya günün değişmesi eski bekleyen uyarıyı geçersiz kılar. Göndermeden hemen önce yeniden kontrol edilir. Süresi değişmiş eski aktivasyon e-postası da gönderilmez.

## Zamanlayıcı
3.6.49 sabit komutu korunur:
/usr/local/bin/php '/home/kobiviracom/kobivira-private/saas/KobiviraCron.php' --run

Komut güncel sürümü current.json'dan seçer. Yedekleme kapalı veya henüz zamanı gelmemiş olsa bile kilit bırakıldıktan sonra e-posta işçisi çalışır. --tasks da işçiyi çağırır. Yeni cron satırı gerekmez. Kuyruk için en fazla 8 gönderim ve sırayla en fazla 40 firma taramasıyla bounded çalışma vardır; sonraki firmalar kayıtlı cursor ile ilerler. Bakım/uygulama kilidi meşgulse sonraki çalışmayı bekler. Var olan retention, eski sürüm ve yedek temizleme mekanizmaları değiştirilmez.

## SMTP sonuçları
Kuyrukta / SMTP ayarı bekliyor / gönderiliyor / SMTP kabul etti / gönderilemedi / sonuç belirsiz / iptal durumları ayrıdır. SMTP kabulü gelen kutusuna teslim garantisi değildir; Yandex spam veya SPF/DKIM yönetimi bu sürümün kapsamı değildir. SMTP kapalıysa olay bekler, başarılı ödeme/doğrulama korunur. Hatalı gönderim otomatik tekrarlanmaz; yönetici mevcut parola ve CSRF ile yeniden kuyruğa alabilir. Belirsiz sonuçta ikinci e-posta riski ayrıca onaylanmalıdır. İşçi DATA sonrasında durursa sonuç belirsiz olabilir; stale sending kaydı 10 dakika sonra unknown olur, otomatik tekrar yoktur. SMTP ile veritabanı arasında dağıtık transaction olmadığı için kesin tek teslim garantisi verilmez; mükerrer otomatik tekrar önlenir.

HTML ve düz metin alternatifleri birlikte iletilir. Lacivert/turkuaz kimlik yalnız e-posta şablonuna uygulanır. Mevcut tüm CSS, site kaynakları, menüler ve önceki 54 migration korunur. Yeni 055_automatic_email.php, şirket bazlı iki kuyruk/durum tablosu ekler; firma silme ve yedekten şirket ayıklama bu tablolara uyumludur. Mevcut sırlar pakete gömülmez.

## Kurulum sonrası
Sürümü 3.6.50 olarak doğrulayın. E-posta / SMS gönderimleri alanında yeni bölümleri ve son zamanlayıcı kontrolünü inceleyin. Kendi doğrulanmış test firmanıza başlangıç bildirimi oluşturun; cron çalıştıktan sonra sonucu kontrol edin. Gelen kutusu ve spam klasörünü ayrıca denetleyin. Canlı ödeme/EDM göndermeden önce mevcut hizmet prosedürlerinizi izleyin. Bu teslimin testleri izole ortam ve yerel SMTP içindir; canlı SMTP/PayTR/GİB işlemi yapılmamıştır.
