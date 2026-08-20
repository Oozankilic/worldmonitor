# Rakip Analizi ve Yeni Fikir Araştırması — Ağustos 2026

**Kapsam:** Productçının verdiği 7 rakip uygulama + kendi App Store uygulamamız (World Monitor: Real-Time Intel) yorum madenciliği; pazar trendi araştırması; kod tabanı yeniden-kullanım envanteri; 3 bağımsız eleştirmen lensiyle (farklılaşma / ürün canlılığı / fizibilite) fikir eleme.

**Yöntem notu:** Apple'ın App Store sayfaları ve yorum RSS API'si bu çalışma ortamının ağ politikası tarafından bloklu olduğundan, veriler App Store sayfalarını ve yorum sayfalarını indeksleyen arama sonuçları + üçüncü parti aynalar üzerinden toplandı (~150 yorum alıntısı, ağırlıkla 1–2 yıldız). Rating/fiyat rakamları ikincil kaynak; tema ve alıntılar gerçek yorum parçaları ama frekanslar yaklaşık. Karar vermeden önce kritik rakamları Sensor Tower/Appfigures'tan doğrulamak gerekir.

---

## 1. Rakip özet tablosu

| Uygulama | Rating (adet) | Fiyat | #1 şikayet | En çok istenen özellik |
|---|---|---|---|---|
| NewsBreak | 4.8 (~1.4M) | Ücretsiz + $5.99/ay reklamsız | Reklam + clickbait seli; "günde 200+ bildirim" | Ailenin yaşadığı şehri/ülkeyi takip edebilme; gerçek yerel yarıçap filtresi |
| CrimeRadar | 4.9 (~33K) | Ücretsiz + $79.99/yıl | Paywall creep + AI yanlış alarmları (BBC Verify skandalı) | Kronolojik sıralama, kalıcı filtreler, ~5 dk gecikmeli gerçek zamanlılık, transkript |
| Citizen | 4.7 (~430–510K) | Ücretsiz + $19.99/ay | Eski ücretsiz özelliklerin paywall'a alınması | Ücretsiz doğrulanmış uyarılar; mil bazlı yarıçap + olay türü filtresi |
| Ground News | 4.7 (~47K) | $9.99–99.99/yıl | Abonelik sürtünmesi; linklerin paywall'lu sayfalara çıkması | Sesli brief/TTS (erken beta), offline, US-dışı kapsama |
| Watch Duty | 4.9 (25–45K) | Ücretsiz + $25/yıl (uçak takibi) | İlçe (county) bazlı uyarının kaba kalması | Nokta+yarıçap bazlı uyarı; daha sık perimetre güncellemesi |
| SmartNews | 4.6 (~901K) | Ücretsiz + reklamsız abonelik | Reklam istilası, clickbait, pil/ısınma | Kaynak engelleme; tek seferlik reklam kaldırma; dark mode |
| Very Local | 4.7 (~4.6K) | Ücretsiz (FAST/reklam) | Atlanamayan, tekrarlayan reklamlar | Baştan izleme; şehri kaydetme; konuma göre bildirim |
| **World Monitor (biz)** | Yetersiz veri (yeni) | Ücretsiz + Pro | US-merkezli veri ("Çin kapsaması yok"); "kalabalık UI"; "Pro'daki içerik mainstream haber, para etmez" | Harita katmanları free kalsın (churn eden aboneler bile haritayı referans olarak tutmak istiyor) |

### Tüm rakiplerde tekrarlayan 4 sinyal

1. **Bildirim spam'i + kaba coğrafi hedefleme.** NewsBreak "günde 200+ push", Watch Duty ilçe bazlı uyarı, NewsBreak "100 mil öteden haber". Kullanıcıların istediği şey net: *kendi çizdiğim yarıçap + tür bazlı aç/kapa + önem eşiği*. Hiçbir rakip bunu tam veremiyor çünkü feed-first mimarileri buna uygun değil; harita bunun doğal UI'ı.
2. **Doğrulanmamış AI içerik = güven ölümü.** NewsBreak'in 40+ AI-uydurma haberi (Reuters soruşturması), CrimeRadar'ın sahte okul-silah alarmı (BBC Verify, kamuya özür). Watch Duty ise tam tersini marka yapmış: "not robots or AI" — 4.9 rating. Ders: AI'ı gizli içerik değirmeni olarak değil, **kaynak gösteren, çapraz doğrulayan** katman olarak konumlandırmak zorundayız.
3. **Paywall creep kızgınlığı.** Citizen $19.99/ay, CrimeRadar $79.99/yıl, hepsinde "eskiden ücretsizdi" öfkesi. Bizim kendi yorumlarımızda da aynısı: Pro'yu bırakan kullanıcı haritayı referans olarak tutmak istiyor. **Harita free, derinlik paralı** doğru yapı.
4. **Rakip haritaların hepsi negatif temalı.** NewsBreak'in tek haritası crime map, Citizen tamamen suç, Liveuamap savaş. Pozitif/nötr içeriği haritada gösteren büyük oyuncu yok — indie'ler (NewsMap, Nino!, Localize) tek şehirlik ve dağıtımsız. Reuters 2025: haber kaçınma %40 (rekor); nedenler: ruh hali %39, bunalma %31, savaş/çatışma fazlalığı %30. Türkiye %61 ile dünya 2.'si — bu bir "talep" kanıtı değil, ama *sakin, seçici, pozitif* ürün framing'inin tam desteği.

---

## 2. Mevcut 5 fikir için doğrulama notları

**1. Aviation Radio — doğrulandı, rakamlar netleşti.** ATC by Enhanced Radar: $6.99/hafta veya $89.99/yıl, haftalar içinde ABD Travel kategorisinde ~#4 grossing (UK ~#8), TikTok klipleriyle viral, günde ~1M transmisyon transkripti, $7M seed (Initialized + United Airlines Ventures + YC). Kritik detay: **feed lisansı riskinin cevabı donanım** — 70–80 havalimanına kendi alıcılarını kurmuşlar; LiveATC feed'leri gönüllü tabanlı ve rebroadcast'i TOS ile kısıtlı. US-dışı kapsama boşluğu doğru ve açık duruyor. Repo tarafında aviation RPC stack'i (delay/uçuş/NOTAM/OpenSky/Wingbits) hazır ama **ses altyapısı tamamen net-new**.

**2. Local Pulse — talep kanıtı güçlü.** SmartNews'ün en sevilen özelliği zip-code yerel kapsama ("Best Local News App 2024"), NewsBreak 1.4M rating'ini küçük kasaba kapsamasına borçlu — ama ikisi de feed, tek harita yüzeyleri crime. Ek öneri (öldürülen "Tonight Map" fikrinden salvage): AI ile yapılandırılmamış kaynaklardan (belediye takvimleri, mekan sayfaları) etkinlik çıkarımı Local Pulse'ın bir pin türü olsun; kullanıcıya gösterilmeden önce tek şehirde tarih/saat/mekan doğruluğu >%95 kapısından geçsin (halüsinasyonlu etkinlik = kilitli kapıya giden kullanıcı = terminal churn). Bilet affiliate geliri varsayma: Eventbrite'ın aktif nakit affiliate programı yok; Posh'un $95M'i platform GMV'si, aggregator'a transfer olmaz.

**3. World Pulse — Reuters verisi doğrulandı, Ground'un açığı netleşti.** %40 kaçınma teyitli (48 ülke, ~100K kişi). Ground News'un tek "haritası" $99/yıl Vantage tier'ında statik bir kapsama grafiği — canlı harita değil. Ground kullanıcılarının açık istekleri: sesli brief/TTS (Ground'da erken beta), offline, US-dışı kaynak kapsaması. Haritayı ücretsiz core deneyim yapmak Ground'un paywall yapısını tersine çevirir; 21 dilli RSS + çeviri zincirimiz tam da Ground'un en zayıf noktasına (US-dışı) oturuyor.

**4. News Bot — açı doğru, altyapı yarı hazır.** NewsBreak NBot var ama haritaya bağlı değil; boşluk duruyor. Headline Memory (RAG, yerel embeddings + IndexedDB) ve deduct-situation Q&A pattern'i repo'da mevcut — ama **client-side**; sunucu tarafı schedule'lı üretim yok. Paywall metriği için tek gelir kanalı iOS Pro.

**5. BlindSpot + The Last 24 — risk doğrulandı, coğrafi açı hâlâ boş.** Ground yorumları kaynak-etiket güvensizliğinin gerçek olduğunu gösteriyor: "Centre etiketli kaynaklar aslında sol eğilimli" şikayetleri, yayın-düzeyi (makale-düzeyi değil) etiketleme eleştirisi, US-dışı kaynakların hiç etiketlenmemesi. Yani politik hassasiyet riski teorik değil, kategorinin bilinen yarası. Coğrafi kaynak dağılımı ("bu olayı hangi ülkenin basını nasıl gördü") gerçekten kimsede yok ve GDELT'in tone alanı repo'da zaten mevcut (`src/services/gdelt-intel.ts`) — en ucuz farklılaşma burası.

---

## 3. Yeni fikirler

Üç taslak fikir 3 bağımsız eleştirmen lensinden geçirildi; biri öldü, biri revize edilerek hayatta kaldı, biri güçlenerek çıktı. Panelin taslaklarda olmayıp kendi bulduğu dördüncü (yatay) fikir de eklendi.

### 6. Places — "Uzak Yerlerim" (panel: 7.5 / 7.5 / 6.5 — en güçlü yeni fikir)

* **Kategori ve mekanik:** Kişisel coğrafya / uzaktan-yerel takip. Kullanıcı haritaya yaşadığı şehri + memleketini + ailesinin şehirlerini pinler; her yer için kendi çizdiği yarıçap, kendi dilinde günlük AI brief ve sadece önem eşiğini aşan uyarılar. "Ev + memleket + annemin kasabası" tek haritada.
* **AI'ın rolü (core):** Yerel dildeki kaynakları tarayıp kullanıcının diline çevirme (Almanya'daki kasabayı Türkçe brief'le takip etmek AI'sız imkânsız — ürünün kendisi bu), çok-kaynak doğrulama rozeti ("3 kaynak doğruladı" / dürüstçe "tek kaynak" etiketi), önem skorlaması (spam'i öldüren şey), yer başına brief üretimi.
* **Rakipler:** NewsBreak (yorumlarda birebir bu özellik dileniyor: "ülke/şehir arama alanı olsun, ailelerinden ayrı yaşayanlar var" — ama US-only ve feed-first), Citizen Alert Zones ($19.99/ay, sadece ABD metroları), Watch Duty (ilçe bazlı, US, yangın+sel), Very Local ("taşındım, memleket haberi" use-case'ini pazarlıyor ama 27 Hearst marketiyle sınırlı), Google News (şehir takibi var, harita/yarıçap/brief yok).
* **Açık:** Küresel çok-yer takibi + çevrilmiş yer-başına AI brief hiçbir yerde yok. Diaspora kaması: Avrupa'nın en büyük diaspora koridoru Türkiye↔Almanya — bizim ekip için doğal ilk pazar.
* **İlk adım (panel revizyonlu):** Şehir değil **koridor** ile başla: Türkiye↔Almanya. 2 pilot şehir için şehir-scoped GDELT GEO + yerel RSS crawl (Railway relay'deki mevcut crawler yeniden hedeflenebilir), günlük brief'i **e-posta ile** gönder (push altyapısı gerektirmez; Nice News 3 yılda 1M abone, Patch ~30K topluluk newsletter'ıyla kârlı — kanal kanıtlı). İlk gün değeri için zaten ingest ettiğimiz doğa katmanlarını (USGS/GDACS/FIRMS/Open-Meteo) yarıçapa bağla: "ailenin bölgesinde deprem/sel var mı, 3 kaynaktan teyitli" — haber crawl'ı kendini kanıtlamadan önce ürün çalışır durumda olur. Ölçüm: brief açılma oranı vs mevcut World Brief. Free'de 1 yer, fazlası iOS Pro.
* **Risk:** Küçük kasabalarda kaynak derinliği (tek kaynaklı yerde "3 kaynak rozeti" matematiksel olarak imkânsız — dürüst "tek kaynak" etiketi şart, yoksa NewsBreak'in uydurma-haber tuzağına düşeriz); önem modeli iki yönlü ölümcül (gevşek = kaçtıkları spam, sıkı = ailenin kasabasındaki seli kaçırmak); sessiz-tasarımlı ürünün doğal re-open tetikleyicisi zayıf (e-posta ritüeli bunu kısmen çözer); brief üretim maliyeti kullanıcı başına ölçeklenir (obscure kasaba = cache paylaşımı yok).

### 7. Sky Pulse — "Gökyüzü Takvimi" (panel: 6 / 6 / 6 — standalone değil, katman/varyant olarak)

* **Kategori ve mekanik:** Pozitif doğa/gökyüzü fenomenleri. Tek canlı haritada: roket fırlatmaları (yörünge + görüş konisi), meteor yağmurları, tutulmalar, süperay, aurora ovali, kuyruklu yıldız geçişleri, çiçeklenme/yaprak cepheleri. Fenomene dokun → *senin konumundan* ne zaman/nereden/nasıl görülür.
* **AI'ın rolü (core):** Uzay havası tahmini + bulut örtüsü (Open-Meteo zaten entegre) + ışık kirliliği + zamanlamayı tek cevaba indirme: "bu gece 21:40–22:10 arası, %70 ihtimalle görürsün." Not — panel dürüstlüğü: bu skorun kendisi deterministik veri füzyonu, LLM'in işi anlatım + "bu gece gökyüzünde" brief'i + ilginç olay tespiti. AI-core iddiasını taşıyan şey çapraz-fenomen sentezi ve kişisel brief.
* **Rakipler:** My Aurora Forecast (ücretsiz tier'ı bile oval+bulut+konum görünürlük skoru veriyor — **aurora dikeyinde boşluk yok**, bunu bilerek girelim), Hello Aurora, Star Walk/Sky Guide (AR planetaryum, canlı olay haritası değil), Sakura Navi (Ocak 2026'da 11 ülkede #1 paralı Travel — ama moat'ı tescilli fenoloji verisi, harita değil), launch-tracker'lar (tek dikey). Astrospheric/Clear Outside prosumer astronomi nişini zaten birleştiriyor.
* **Açık:** Çapraz-fenomen kompoziti + konum-bazlı görünürlük tek haritada kimsede yok. Ama tek gerçek moat şansı: **"gördüm" doğrulama topluluğu** — fenomen başına crowdsourced gerçek-görüş teyidi + skor doğruluğu geri beslemesi. Windy bir sprint'te aurora katmanı kopyalayabilir (forumlarında yıllardır istek var); görüş-teyit grafiğini kopyalayamaz.
* **İlk adım:** World Monitor içinde katman olarak başla (standalone app değil). Kadansı nadir fırtınalara değil **haftalık ritme** bağla: fırlatmalar (~haftalık) + meteor takvimi + ISS geçişleri. Viral döngü: mevcut share-card renderer'la (`happy-share-renderer.ts` pattern'i) "bu gece görülebilir" kartları — aurora/fırlatma kartı TikTok-native (ATC kanıtı). Uyarılar mevcut iOS uygulamasının push/Live Activity kanalından; web'de e-posta digest.
* **Risk:** Epizodik retention (fırtınalar arası "bu gece bir şey yok" diyen brief uninstall ettirir → kadans çeşitliliği şart); Güneş döngüsü 25 maksimumu 2024–25'te geçti, orta-enlem aurora olayları ~2030'a kadar azalacak — aurora'yı manşet değil yan katman yap; yanlış "görürsün" skoru = benzin parası yakmış 1-yıldızlı kullanıcı; ışık kirliliği atlası (Falchi) CC BY-NC ve Open-Meteo free tier'ı ticari kullanımda lisans gerektirir — monetize etmeden önce lisans kontrolü.

### 8. Verified Alerts — "Doğrulanmış Uyarı Motoru" (panelin bulduğu yatay fikir)

* **Kategori ve mekanik:** Ürün değil omurga — ama en yüksek kaldıraçlı yatırım. Dört büyük şikayet sinyali (bildirim spam'i, kaba coğrafi hedefleme, doğrulanmamış AI, paywall'lu güvenlik) tek bir motora işaret ediyor: **kullanıcı çizimi yarıçap + tür bazlı aç/kapa + AI önem eşiği + çok-kaynak doğrulama rozeti**. Citizen doğrulanmış uyarıyı $19.99/ay'a satıyor; biz "doğrulanmış uyarılar, ücretsiz" diye konumlanırız.
* **AI'ın rolü (core):** Önem skorlaması (hangi olay push'u hak ediyor) + çapraz kaynak eşleştirme (aynı olayın 21 dilde N bağımsız kaynakta teyidi) + tek-kaynak dürüstlük etiketi. Bu, CrimeRadar/NewsBreak'in yapısal olarak yapamadığı şey: onların pipeline'ı tek kaynaklı (scanner sesi / scrape), bizimki çok kaynaklı.
* **Rakipler:** Doğrudan kimse — Citizen (paralı, US, suç), Watch Duty (insan küratörlü, dar kapsam). Bu bir kategori değil, Local Pulse / Places / News Bot / BlindSpot'un hepsinin altına giren güven katmanı.
* **Açık:** Uyarı kalitesi hiçbir rakipte ürünleşmemiş; hepsinde şikayet konusu. "Corroborated by N sources" rozetini marka yapan ilk oyuncu güven moat'ını alır (Watch Duty'nin "not AI" moat'ının AI'lı simetriği: "AI ama kaynaklı ve teyitli").
* **İlk adım:** Önce push altyapısı — web repo'da hiç yok (service worker cache-only, PushManager/VAPID yok); iOS tarafında Live Activities mevcut. Sonra mevcut breaking-news-alerts.ts önem/soğuma mantığını çok-kaynak teyit sayacıyla genişlet; ilk yüzey olarak Places pilotunun doğa uyarılarında test et. Sözleşmeyi marka yap: "haftada en fazla N uyarı; her uyarı ya teyitli ya 'tek kaynak' etiketli."
* **Risk:** Önem modeli kalibrasyonu (yukarıda); doğrulama gecikme maliyeti — teyit beklerken Citizen'ın "saniyeler içinde" hızını kaybetmemek için iki aşamalı uyarı gerekebilir ("ilk sinyal / teyitlendi").

### Öldürülen fikir — Tonight Map (etkinlik keşfi + biletleme; panel: 3 / 3 / 3)

Şeffaflık için: harita-first etkinlik keşfi fikri üç lensin üçünde de öldü. (a) Gerçek rakip Partiful/Posh değil Google — Maps/Search zaten mekan sayfalarından ve belediye takvimlerinden etkinlik çıkarıyor, uzun kuyruk onların ev sahası; (b) Partiful/Posh haritasız kazandı, Facebook Local ve IRL mezarlığı harita-first etkinlik keşfinin denenip öldüğünü gösteriyor; (c) affiliate ekonomisi yok (Posh'un $95M'i kendi biletleme rayları), AI'ın çıkarabildiği uzun kuyruk tam da para ödemeyen envanter; (d) halüsinasyonlu etkinlik = kullanıcıyı fiziksel olarak kapalı kapıya göndermek; (e) kendi Local Pulse fikrimizle bariz çakışma. Salvage: AI etkinlik-çıkarım pipeline'ı Local Pulse'ın bir pin türü olarak, %95 doğruluk kapısıyla (yukarıda, §2/2).

---

## 4. Altyapı gerçekleri (fikir seçiminden bağımsız ön koşullar)

Kod envanterinden çıkan, hangi fikri seçersek seçelim geçerli üç gerçek:

1. **Push bildirimi web'de sıfır.** Service worker cache-only; PushManager/VAPID/abonelik deposu yok. Rakip yorumlarındaki en büyük şikayet kategorisi (bildirim kalitesi) bizim en büyük altyapı boşluğumuz. iOS uygulamasında Live Activities var — kısa vadede uyarı kanalı iOS, web'de **e-posta** (Convex + register-interest endpoint'i hazır lead-gen çekirdeği; Nice News/Patch kanalın kârlılık kanıtı).
2. **Web'de ödeme altyapısı yok.** Monetizasyon kısa vadede yalnızca iOS Pro üzerinden. Kendi yorumlarımızın dersiyle birleşince net fiyat mimarisi: **harita ve katmanlar free** (churn eden bile referans olarak tutmak istiyor), derinlik paralı (Windy 80K indirmeyle ~$600K/ay — prosumer derinlik, kitle genişliğinden iyi para kazanıyor; Flighty $49/yıl ile ~$1M/ay).
3. **AI zinciri client-side.** `summarization.ts` tarayıcıda koşuyor; "kullanıcı yokken günlük brief üret ve gönder" her fikirde sunucu tarafı schedule'lı üretim gerektiriyor (Railway relay + seed-script pattern'i genişletilebilir ama net-new iş).

## 5. Öncelik önerisi

1. **Places (Fikir 6) — e-posta pilotu, Türkiye↔Almanya koridoru.** En güçlü ve en transfer edilebilir talep kanıtı (rakip yorumlarında birebir dilenen mekanik), mevcut varlıkların en yüksek yeniden kullanımı, push beklemeden test edilebilir.
2. **Verified Alerts motoru (Fikir 8) + push altyapısı.** Tüm fikirlerin (PM'in 5'i dahil) ortak ön koşulu ve tek başına konumlandırma silahı ("Citizen'ın $19.99/ay sattığını ücretsiz ver").
3. **Sky Pulse (Fikir 7) — katman olarak.** Düşük maliyetli (veri kaynaklarının çoğu entegre), share-card viral döngüsüne en uygun içerik, bir sonraki büyük gök olayından *önce* hazır olmak koşuluyla.

Aviation Radio (PM'in 1 no'lu fikri) doğrulanmış en güçlü ödeme-istekliliği kanıtına sahip olmaya devam ediyor; bu üçü onun alternatifi değil, portföy tamamlayıcısı. Seçim "hangisi tek başına" değil "hangi sıra ile" sorusu.
