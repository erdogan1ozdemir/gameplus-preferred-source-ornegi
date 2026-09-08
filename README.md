# Game+ · Tercih edilen kaynak butonu

Google'ın site sahiplerine açtığı **tercih edilen kaynak** yetkisi için hazırlanan Game+ kartı ve kartın blog yazısı içindeki örneği.

| Sayfa | İçerik |
|---|---|
| `index.html` / `kart.html` | Kartın yalın gösterimi |
| `yazi.html` | Kartın gerçek yerinde durduğu örnek blog yazısı |
| `kart-kodu.html` | Blog şablonuna yapıştırılacak kod (stil + işaretleme) |

## Kart

Kart ve buton yayıncınındır. Google'ın gömme butonu kullanılmaz; buton, Google'ın tercihler ekranına giden kendi bağlantımızdır ve yeni sekmede açılır. Gerekçe ölçüm: gömme butonu cross-origin bir iframe olduğu için tıklaması ölçülemez, kendi bağlantımızda tıklama GA4'e doğrudan yazılır.

Görsel değerler Game+ blogunun canlı ölçümünden alındı: kart zemini `#0D0D0D`, kenarlık `#29292B`, başlık New Science 600 20/28 beyaz, açıklama GreycliffCF 16/24 `#B2B2B2`, buton şeffaf zemin + `#FFC900` kenarlık ve metin. Metin kontrastlarının tümü WCAG AA eşiğinin üzerinde (en düşük 9.17:1).

## Yerleştirme

Kart, yazı akışının içinde bir bölüm başlığından hemen önce durur; örnek yazıda "Brawlhalla®" başlığının öncesindedir. Kolon genişliğini aşmaz, 640px altında buton tam genişliğe açılır.

Kod tek parçadır: `kart-kodu.html` içeriği blog şablonuna olduğu gibi yapıştırılır. Şablonda tek bir `<style>` bloğu tutuluyorsa kartın stil kuralları o bloğa taşınabilir.

## Ölçüm

Şablona ölçüm kodu eklenmez. Buton alan adı dışına gittiği için GA4 Gelişmiş Ölçüm'ün giden bağlantı tıklamaları özelliği tıklamayı `click` olayı olarak kaydeder. Butondaki `id="preferred-source-link"` değeri GA4'e `link_id` olarak gelir; raporlama bu değerle filtrelenir.

Tek kontrol: GA4 veri akışında Gelişmiş Ölçüm altındaki giden bağlantı tıklamaları açık olmalıdır.

## Ön koşul

**Butonun çalışması için gameplus.com.tr'nin Google'ın tercih edilen kaynaklar listesinde bulunması gerekir. `google.com/preferences/source?q=gameplus.com.tr` adresi Google hesabıyla giriş gerektirir; doğrulama yapılıp aksiyona öyle devam edilmelidir.**

Google yalnız domain ve subdomain seviyesini kabul eder; alt dizin (`site.com/blog`) uygun değildir.

## Sınırlar

Okuyucunun Google ekranında seçimi tamamlayıp tamamlamadığı ölçülemez. Raporda "kaç kişi tıkladı" denir, "kaç kişi ekledi" denmez.

Sayfalardaki yazı tipleri gameplus.com.tr üzerinden çağrılır; bu depoda font dosyası bulunmaz.
