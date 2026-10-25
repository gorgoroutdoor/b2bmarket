# Kobivira 3.6.50 — Teslim ve test raporu

## Kurulum
Yalnız 3.6.49 üzerine yüklenir. Canlıda kurulu sürüm bu çalışma sırasında doğrulanmadı. Önce yönetimde mevcut sürümü kontrol edin ve tam sistem/hosting yedeğinizi koruyun. ZIP'i açmadan Sistem > Sürüm güncellemeleri alanından yükleyin. Yeni kurulum veya SMTP parolası girmek gerekmez. Paket 3.4.0 tam kurulumdaki güvenilen açık anahtarla doğrulandı. Özel imzalama anahtarı pakete/rapora konulmadı.

## Yapılanlar
- E-posta doğrulandı, gerçek telefon doğrulaması sonrası hoş geldiniz, paket aktivasyonu, havale bildirimi ve gerçek yerel kontör hareketleri için olay kuyruğu.
- 25 altı düşük kontör: günlük isteğe bağlı, günlük kapalıysa her yeni eşik düşüşünde bir kez.
- Ücretli paket bitimine 7 gün kala günlük ve süresi dolunca bir kez bildirim; yenilenmiş firmanın eski kuyruk kaydı gönderilmez.
- Mevcut E-posta / SMS gönderimleri sayfasında genel/tür bazlı ayarlar, konu/metin düzenleme, firma adı/e-posta ile başlangıç bildirimi, durum ve kontrollü tekrar.
- HTML/düz metin alternatifleri, gerçek rehber/paket/panel bağlantıları ve güvenli metin kaçışı.
- Eşzamanlı kuyruk kaydında firma satırı kilidi ve benzersiz olay anahtarı; SMTP transaction dışında.
- SMTP belirsizliğinde otomatik tekrar yok; yönetici açık risk onayıyla yeniden kuyruğa alabilir.
- Mevcut sabit cron --run ve --tasks üzerinden işleme; otomatik tam sistem yedeği kapalıyken de çalışır.
- Yeni tablolar firma silme ve yedekten şirket ayıklama ile uyumlu.

## Korunanlar
22 mevcut CSS dosyası, tüm site kaynakları, menü/ana panel kaynakları, paket yetki tanımları ve önceki 54 migration değişmedi. PayTR imza/tutar/callback doğrulaması, EDM modülleri, sabit cron başlatıcısı, retention ve yedekleme motoru korunur. Checkout3624.php dosyasına yalnız başarılı gerçek aktivasyon için kuyruk çağrısı eklendi; ödeme algoritması değiştirilmedi. SMTP bilgilerinin tamamı mevcut settings kayıtlarından alınır.

Yeni kaynaklar: Mail3650.php, Mail3650Admin.php, migrations/055_automatic_email.php ve sürüm notu. Çağrı noktaları: Email3643.php, Phone3644.php, Billing.php, Checkout3624.php, Delivery.php, Notice.php, Purge.php, Modules.php ve release_history.json. Notice.php değişikliği aynı olay için ikinci genel e-postayı önler; panel/SMS bildirimlerini korur.

## Doğrulama
Toplam 157 başarılı kontrol:
- events: 37
- reminders: 22
- smtp: 16
- http: 22
- worker: 5
- browser: 7
- cron: 6
- update: 42

- Gerçek tek kullanımlık e-posta ve mobil kod tüketimi; test telefon bayrağının gerçek doğrulama sayılmaması.
- Üç pakette yerel imzalı PayTR callback fixture'ı ve tekrarının ikinci aktivasyon/süre/e-posta üretmemesi. Gerçek kart tahsilatı yapılmadı.
- Gerçek HTTP havale bildirimi ve yönetici onayı; konu metni kaydı; CSRF, rol ve parola korumaları; belirsiz yeniden gönderimde açık onay.
- 26/25/24/0 bakiye, günlük tekillik, yeni düşüş, bakiye/üyelik yenilenmesinde eski olayın geçersizliği.
- Yerel SMTP soket sunucusu: kabul, kesin ret ve DATA sonrası bağlantı kesilmesi. Multipart HTML/plain ve UTF-8 konu doğrulandı. SMTP kapalıyken ödemeler ve doğrulamalar korundu.
- Kuyruk ve durum kayıtları varken mevcut aşamalı firma silme işlemi HTTP üzerinden tamamlandı.
- Eşzamanlı altı işlemde tek olay. Ek teşhis turunda 12 grup/72 paralel ekleme denemesi hatasız ve grup başına tek olayla tamamlandı.
- Gerçek sabit cron --run/--tasks, yedek kapalıyken e-posta heartbeat'i, aynı gün tekrarında yeni olay oluşmaması.
- Chromium 1440/390 piksel: yeni yönetim bölümleri, metin editörü, yatay taşma ve betik hata kontrolleri.
- Orijinal 3.6.49 Updater ile imzalı kurulum, kurcalanmış içeriğin reddi, fiyat/kota/abonelik/kontör ve mevcut ayarların korunması; gerçek recover ile 3.6.49 ve 54 migration'a dönüş.
- 198 PHP dosyası sözdizimi ve bütün JSON dosyalarının ayrıştırılması; imza ve SHA-256 dosya özetleri doğrulandı.

## Kurulumdan sonra
Sistem > E-posta / SMS gönderimleri içinde Otomatik hesap e-postaları bölümünü kontrol edin. Varsayılan genel/tür ayarları açık, düşük kontör günlük tekrar kapalıdır. Son zamanlayıcı kontrolünü inceleyin; mevcut sabit cron satırı korunur. Kendi doğrulanmış test firmanız için başlangıç bildirimi oluşturun. Kuyrukta/SMTP ayarı bekliyor/SMTP kabul etti/başarısız/belirsiz/iptal ayrımını kontrol edin. SMTP kabulü gelen kutusuna teslim kanıtı değildir; spam klasörü ve alıcı teslimi ayrıca incelenmelidir.

## Sınırlar
Canlı SMTP hesabı, gerçek telefon SMS'i, canlı PayTR tahsilatı veya EDM/GİB işlemi bu çalışmada denenmedi. Yandex spam sorunu çözülmüş sayılmaz. Ağ sonucu belirsizken kesin tek teslim garantisi verilemez; otomatik tekrar önlenir. Firma adresi/üyeliği değişmiş veya silme süreci başlamışsa eski olay gönderilmez. Kontör e-postası yerel Kobivira hareketidir; EDM bakiyesi satın alımı değildir. Kontör kart satışı açılmadı. Önceki üyeliklere toplu hoş geldiniz gönderimi yapılmaz; yönetimden açıkça oluşturulur.

SHA-256: e174260b2c2c6436ffefb9a39b9a3c1334e3dead28c6f6a6526c030c70cf7434
