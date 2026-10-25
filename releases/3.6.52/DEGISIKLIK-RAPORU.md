# Dosya bazlı değişiklik raporu

Karşılaştırma: teslim edilen 3.6.51 → 3.6.52. Canlı sunucu taraması değildir.

- `Mail3645.php`: Düz metin e-posta altına eksikse tam marka/slogan ekler.
- `Mail3650.php`: Mobil kayıt e-postası, geçici onayla hoş geldiniz ve ilgili kullanıcıya özel gönderim filtresi.
- `Mail3650Admin.php`: Mevcut bildirim ayarlarında yeni mobil kayıt türünün metin alanı ve geçici onayla hoş geldiniz koşulu.
- `MailDesign3651.php`: HTML e-posta altına tam marka/slogan geri konur; tek logo korunur.
- `Modules.php`: Yeni kayıt e-postası yardımcı modülünü yükler.
- `release_history.json`: 3.6.52 sürüm açıklaması eklenir; önceki kayıtlar korunur.
- `RegistrationMail3652.php`: İşlem sonrası, yalnız ilgili kullanıcının kayıt e-postalarını gönderir; eksik olayları tekilleştirerek tamamlar.

Silinen kaynak dosyası: **0**. Tüm CSS ve `site/` dosyaları aynıdır. Ana görünüm, menü/yetki, ödeme, EDM, yedek ve güncelleyici bileşenleri aynıdır. Önceki 56 migration aynıdır.

Önceki teslim 3.6.50 → 3.6.51: değişen dosyalar `Modules.php`, `Mail3650Admin.php`, `Mail3645.php`, `release_history.json`, `Phone3644.php`, `Mail3650.php`, `Delivery.php`; eklenenler `TemporaryPhone3651.php`, `MailDesign3651.php`, `migrations/056_temporary_phone.php`. Silinen dosya yoktur. Bu sürümde geçici kayıt kodu ekranı ve mevcut yönetim ayar alanındaki seçenek eklenmişti; site/CSS dosyaları değiştirilmemişti.
