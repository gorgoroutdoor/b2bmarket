# Kobivira 3.6.51

Bu imzalı güncelleme yalnızca **3.6.50 üzerine** yüklenir. Canlı sunucuya otomatik kurulum yapılmadı; mevcut yönetim panelindeki güncelleme yükleme işlemini kullanın.

- Netgsm SMS modu kapalıyken e-posta onaylı kullanıcı için ekranda geçici kayıt kodu gösterilir. Mevcut canlı SMS modu ve servis bilgileri korunur. Mevcut SMS ayarları bölümündeki geçici kayıt seçeneğiyle kapatılabilir.
- Kod kullanıcıya ve oturuma özeldir; tek kullanımlık, 10 dakika geçerli, yeniden isteme aralığı 60 saniye, günlük sınır 8, deneme sınırı 5. Bu işlem gerçek telefon doğrulaması değildir ve telefonla şifre sıfırlama sağlamaz. Canlı SMS açıldığında gerçek doğrulama gerekir.
- “Kontör bakiyeniz 25 adedin altında” e-postası mobil kayıt onayından sonra gönderilir; geçici kayıt onayı bu bildirim için yeterlidir. Eski bekleyen bildirimler onaya kadar bekletilir.
- Doğrulama, doğrulama sonrası, üyelik, kontör ve diğer gönderimler ortak lacivert/turkuaz e-posta şablonunu kullanır. Üstte yalnızca bir görsel bulunur: mevcut Kobivira logosu. Başlık, içerik, bağlantı ve butonlar metindir. Düz metin alternatifi korunur.
- Logo mevcut herkese açık marka görseli adresinden yüklenir. E-posta istemcisinin görsel engelleme tercihleri geçerlidir. Görsel sayısını azaltmak tek başına spam klasörüne düşmeme garantisi sağlamaz.
- Site, yönetim ve firma panelinde tasarım yenilemesi yapılmadı. CSS dosyaları, site dosyaları, ana panel görünümleri, menü/yetki bileşenleri ve önceki 55 migration korunmuştur. İstenen geçici kayıt ve bildirim davranışları mevcut akışa eklenmiştir.

Canlı Netgsm ve gerçek alıcıya SMTP gönderimi denenmedi. Testler izole yerel veritabanı, tarayıcı ve SMTP test sunucusu üzerinde yapıldı.
