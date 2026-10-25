# Kobivira 3.6.52

Yalnız **3.6.51 üzerine** yüklenir. Canlı sunucu değiştirilmedi; kullanıcı yönetim panelinden yükler.

- Her HTML ve düz metin e-postanın altında marka/slogan tam olarak **Kobivira · İşinizin hesabı** olarak korunur. Üstte tek logo görseli bulunur; mevcut ortak renkler korunur.
- E-posta doğrulandı, mobil kayıt onayı ve hoş geldiniz bildirimleri, doğrulama işlemi tamamlanıp veritabanına kaydedildikten sonra zamanlayıcı beklemeden gönderilmeye çalışılır. İlk doğrulama bağlantısı gönderimi korunur.
- Geçici mobil kayıt onayı hoş geldiniz bildirimi için yeterlidir. Mobil onay e-postasında geçici onay olduğu açıkça belirtilir. Gerçek SMS doğrulama işaretleri ve şifre sıfırlama yetkileri değişmez. Yönetimdeki mevcut bildirim listesinde mobil kayıt onayı türü görünür.
- Giriş yapan, e-posta doğrulaması tamamlanmış kayıt sahibinin eksik kayıt bildirimleri benzersiz olay anahtarlarıyla tamamlanır. Daha önce SMTP kabul etmiş bildirim yeniden gönderilmez. Başarısız veya sonucu belirsiz iletiler otomatik tekrar gönderilmez; mevcut yönetim kontrolü korunur.
- Kalıcı kuyruk ve mevcut zamanlayıcı korunur; kayıt dışındaki ödeme, kontör ve süre bildirimlerini zamanlayıcı işler. SMTP kapalıysa gönderim bekler. İlk doğrulama mailinin ulaşması, zamanlayıcıdaki otomatik bildirimlerin işlendiğini tek başına kanıtlamaz.
- SMTP/Netgsm bilgileri, site ve panel tasarımı, menüler ve paket yetkileri değiştirilmez. Önceki 56 migration aynıdır; yeni migration yoktur.

Gerçek alıcıya veya canlı Netgsm hizmetine test gönderimi yapılmadı. SMTP kabulü, e-postanın gelen kutusuna ulaştığının garantisi değildir.
