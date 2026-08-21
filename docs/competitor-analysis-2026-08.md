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

---

## Ek — Gerçek yorum verisi (21 Ağustos 2026 güncellemesi)

Ekip 5 uygulama için gerçek, tarihli, kategori ve duygu-durumu etiketli App Store yorum export'u paylaştı: **1.947 yorum, 20 Şubat – 18 Ağustos 2026, US mağaza**. Bu veri yukarıdaki arama-tabanlı tahminlerin yerini alıyor — artık gerçek yüzdeler var. Kapsam: NewsBreak (698), SmartNews (550), ATC – Live Air Traffic Radio (315), Ground News (244) ve **yeni bir rakip: FlightDeck – Flight Tracker (140)**.

**Önemli metodoloji notu:** bu export'taki ortalama rating'ler (1.9–3.1 arası) App Store'daki gerçek toplam rating'lerle (örn. NewsBreak halka açık 4.8) **uyuşmuyor**. Kategori/duygu etiketi taşıyan "detaylı" yorumlar sisteme muhtemelen içerik yazma eğilimi olan (çoğunlukla mutsuz) kullanıcılardan öncelikli giriyor. Yani buradaki oranları *mutlak memnuniyet* değil, **şikayet dağılımı ve göreli ağırlık** olarak okuyun — dört rakipteki hâlihazırdaki bulguları teyit/inceltme amaçlı.

### Uçuş takibi üçgeni artık iki değil üç oyunculu

FlightDeck – Flight Tracker (Attracts Inc.) daha önce incelemediğimiz bir rakip: ATC'nin AI-transkript + harita mekaniğine benzer ama farklı bir çekirdek özellikle giriyor — **ACARS** (uçak-yer veri linki mesajları, ham metin olarak). Yorumlarda "ACARS &amp; flight logs features are unique to this app... definitely worth the price" — bu gerçek bir farklılaşma sinyali, aviation idea'mıza eklenebilir bir katman.

Ama asıl bulgu **fiyatlama tepkisinin şiddeti, sayısallaştırılmış**:

| | ATC | FlightDeck |
|---|---|---|
| Negatif yorumların Monetization/Pricing içerme oranı | **%78.4** | **%73.5** |
| Örnek yorum | "$90/year, are to nuts? Forced to watch a demo... LiveATC.net is free." | "Why tf can i not enjoy a free flight tracker without a subscription... flightradar24 is free" |
| Aylık ortalama rating trendi | Şub 3.44 → Ağu 2.97 (**sürekli düşüş**, kullanıcı tabanı büyüdükçe hype-affiliate erken benimseyicilerin yerini fiyata duyarlı mainstream kullanıcı alıyor) | Şub'dan itibaren hep 1.9–2.6 bandı, hiç toparlanmadı |

Bu, önceki raporda "ATC $89.99/yıl'a rağmen top-5 grossing" diye övülen modelin **churn/rating maliyetini** gösteriyor: iki rakip de negatif yorumların ~4'te 3'ünü fiyatlamaya kaptırmış, ikisi de kıyaslamada hep FlightRadar24'ün (algısal olarak) ücretsiz olmasına çarpıyor. **Aviation Radio fikri için netleşen ders:** cömert bir ücretsiz katman (temel harita + gecikmeli/sınırlı ses) + makul fiyatlı derinlik, "$90/yıl hard paywall + 10 dakikalık atlanamaz onboarding video" modelinden çok daha az churn üretir — biz bu ikisinin bıraktığı memnuniyetsiz kullanıcı havuzuna doğrudan konumlanabiliriz.

**Yeni, isim-isim özellik talepleri (ATC yorumlarından):** iPad native versiyon yok ("major gap"), pil tüketimi şikayeti, **belirli havalimanı adlarıyla** kapsama talebi (KLAL, KSRQ, SAN, FLL), Avrupa havalimanı kapsaması talebi, AirShow frekansları için özel bölüm, ve bir kullanıcı doğrudan "ATC canlı yayının FlightDeck'e entegrasyonunu" istiyor — yani **ACARS + canlı ATC sesi + uçuş takibi tek üründe** birleşsin talebi zaten kullanıcıdan geliyor.

### AI güveni: görünür yetenek sevilir, görünmez içerik değirmeni nefret edilir

Yorum metinlerinde "AI" geçen yorumların ortalama rating'i uygulama başına çarpıcı bir zıtlık gösteriyor:

- **ATC:** AI bahsi geçen yorumlar ortalama **5.0** — "The team at Enhanced Radar is using AI in a unique and novel way that truly stands out." AI burada *görünür, anlaşılır bir yetenek* (canlı transkript) olduğu için sevilior.
- **NewsBreak:** AI bahsi geçen yorumlar ortalama **1.95** — "Stop using ai slop and fake advertisement", "AI Trash: The whole apps video section is full of cheap AI ads." AI burada *görünmez bir içerik değirmeni* (insan gazeteciliğinin yerini alan otomatik üretim) olarak algılandığı için nefret ediliyor.
- **SmartNews:** benzer şekilde AI bahsi geçen yorumlar ortalama **1.25**.

Bu, mevcut raporun "AI'ı gizli içerik değirmeni değil, kaynak gösteren doğrulayan katman yap" tavsiyesini sayısal olarak doğruluyor ve keskinleştiriyor: **AI'ın kullanıcıya görünür ve anlaşılır bir iş yaparken gösterilmesi** (transkript, çeviri, özet — kaynağı belli) güven kazandırıyor; **AI'ın içerik üretimini gizlice devralması** güveni yok ediyor. News Bot ve Places fikirlerinde AI'ı her zaman "bunu senin için X kaynaktan yaptım" diye görünür kılmak gerekiyor.

### BlindSpot: önyargıyı göstermek sevilir, önyargılı *olduğunu düşünülmek* nefret edilir

Ground News'te "bias" geçen 63 yorum tam ikiye bölünüyor: **31 tanesi 5 yıldız** ("Now I Understand!! ...has shown me how rare it is for the 'other side' to even hear the important stories" gibi övgüler), **25 tanesi 1-2 yıldız** ("Amazing how the 'factual' ratings are slanted even here", "It does not fact check anything"). Aynı kelime, ürünün metodolojisine güvenip güvenmemeye göre en olumlu ve en olumsuz uçlara dağılıyor. Buna karşın NewsBreak ve SmartNews'te "bias" bahsi geçen yorumlar neredeyse tamamen olumsuz (ortalama ~2.0) — bu iki uygulama önyargıyı *göstermiyor*, sadece önyargılı *olmakla suçlanıyor*. **BlindSpot fikri için ders:** önyargıyı şeffaf gösterme konsepti gerçek ve kanıtlanmış talep — ama metodolojiye güven kırılgan, tek taraflı bir "yanlış etiketleme" şikayeti tüm ürünü "sahte tarafsızlık" kategorisine düşürebilir. Coğrafi kaynak dağılımı (hangi ülkenin basını nasıl gördü) muhtemelen "sol/sağ" ikili etiketlemeden daha az tartışmalı bir başlangıç noktası, çünkü politik taraf ataması değil, gözlemlenebilir bir coğrafi gerçek.

### Diğer evrensel sinyal: iptal sürtünmesi

"Cancel" kelimesi geçen yorumların ortalama rating'i her uygulamada 1.0–2.3 arası — istisnasız kötü. Ground News'te "Nearly impossible to cancel subscription... you need to talk to support to actually close your account, like a cable company" gibi doğrudan dark-pattern suçlamaları var. **Ders:** iOS Pro aboneliğimizin iptal akışı App Store'un standart (tek dokunuşla) akışından hiçbir şekilde saptırılmamalı — bu, rakiplerin en ucuz kaybettiği güven puanı.

### Öncelik önerisine etkisi

Bu gerçek veri, önceki önceliklendirmeyi değiştirmiyor ama **Aviation Radio'yu güçlendiriyor**: iki farklı rakip (ATC, FlightDeck) aynı fiyatlama hatasını yapıyor ve ikisinin de negatif yorumlarının ~%75'i bunu doğruluyor — bu, "cömert free tier + makul fiyat" ile girecek bir oyuncu için kanıtlanmış, büyük ve aktif olarak büyüyen bir memnuniyetsiz kullanıcı havuzu demek. ACARS özelliği ve isim-isim havalimanı talepleri, ilk ürün kapsamına eklenebilecek somut, ucuz kazanımlar.

---

## Ek 2 — Uygulama bazında negatif yorum raporu

Her uygulamanın 1–2 yıldızlı yorumlarını ayrı ayrı derinlemesine inceledik: en çok tekrar eden şikayet kategorileri (etiketlerin kendi içindeki gerçek yüzdeleri), aylık negatif-pay trendi (kötüleşiyor mu iyileşiyor mu) ve doğrudan alıntılar. Amaç: hangi rakipte hangi acı en taze ve en büyük, oradan başlayalım.

### NewsBreak — 366 / 698 negatif (%52.4) · trend: iyileşiyor (Şubat %64 → Ağustos %45)

**Şikayet dağılımı (negatif yorumların içinde):** Content %62.6 · Advertisements %31.7 · Performance And Bugs %15.6 · Notifications %15.0 · Monetization %11.7

- **Kritik olayı kaçırma:** *"A police chase literally went through my neighborhood last night and ended with dozens of police officers with guns out looking for suspects in our front yard and this app had ZERO mention of it."* — "yerel haber" iddiasının kendi kanıtladığı en ciddi güven kırılması: gerçek bir olay, sıfır kapsama.
- **Kullanıcının kendi ağzından pozitif talep:** *"I wish this App was more positive but it's mostly all negativity and I get like eight notifications a day that people have died... I'd rather see more positive stuff."* — Happy variant / Local Pulse pozitif-kategori tezimizi rakibin kendi kullanıcısı doğruluyor.
- **Moderasyon + spam:** *"Every single time i download it I get slammed with SPAM calls, Spoofs, SPAM Emails... The hateful racist rants in the comments are wild."*
- **Bildirim kontrolü yok:** *"i got this app for fast notification of NEWS... now i get 100 notifications a day about celebrity updates... to configure my push notifications i have to speak to..."* (destek akışına yönlendiriliyor, self-servis ayar yok)

**Bizim için:** En yüksek hacimli rakip (698 yorum) aynı zamanda kendi kullanıcısından en net "daha pozitif olsun" talebini alan rakip. Local Pulse + Verified Alerts ikilisi tam bu boşluğa oturuyor.

### SmartNews — 302 / 550 negatif (%54.9) · trend: **kötüleşiyor hızla** (Haziran %43 → Ağustos %74)

**Şikayet dağılımı:** Content %61.3 · Advertisements %36.8 · Performance And Bugs %16.2 · Comparative Feedback %15.2 · Feature Requests %10.6

- **Gamification tepkisi (rewards programı), kullanıcının kendi sözleriyle:** *"I've been a long-time user of SmartNews because it felt like a refreshing alternative to the algorithm-driven, attention-hijacking ecosystem... [now] Let us opt out of your points system."* / *"Reading the news isn't a game. And the way the developers have turned it into a game is frankly insulting."* — önceki raporumuzda "2026'da eklenen rewards programı" nötr bir özellik olarak listelenmişti; gerçek veri bunun ciddi bir geri tepme olduğunu gösteriyor ve Ağustos'taki keskin kötüleşmeyle zaman olarak örtüşüyor.
- **Aylarca çözülmeyen bug:** *"TURN OFF THE HOURLY REFRESH!!!"* — Nisan 2026'da yazılmış, kullanıcı kendi notunda önceki güncellemelerden beri (2025 sonundan) şikayet ettiğini belirtiyor; 6+ ay boyunca kapatılmamış.
- **Reklam istilası, tekrarlayan versiyonlarda aynı şikayet:** *"Advertising everywhere!... advertisements will pop into your feed and will move the headlines"* — Nisan ve Temmuz'da neredeyse birebir aynı yorum, aynı kullanıcı muhtemelen iki farklı sürümde tekrar denemiş.
- **Eski haber yeniden servis edilmiş:** *"today, the article that keeps popping up about [a celebrity's] health... you open it, and this happened in 2024."* — NewsBreak'teki "eski haberi taze başlıkla yeniden yayınlama" sorununun SmartNews'te de var olduğunu gösteriyor.

**Bizim için:** SmartNews'ün en hızlı kötüleşen rakip olması (6 ayda +31 puan negatif pay artışı) özellikle önemli — gamification/rewards gibi "kullanıcıyı daha çok tutacak" sanılan özelliklerin ters tepebileceğinin somut kanıtı. Kendi ürünümüzde gamification eklerken (Sky Pulse'ın "gördüm" rozetleri gibi) bu riski göz önünde bulundurmalıyız: ödül/puan sistemi haber okumayı bir oyuna çevirdiğinde güven kaybı riski var.

### Ground News — 114 / 244 negatif (%46.7) · trend: **kötüleşiyor hızla** (Haziran %41 → Ağustos %68)

**Şikayet dağılımı:** Content %48.2 · Comparative Feedback %26.3 · Monetization %25.4 · Pricing %24.6 · Customer Support %15.8

- **Metodolojiye somut, detaylı güvensizlik:** *"Because ground news only relies on two rating sources for bias determination, they do a poor job on their bias ratings. There is a high tendency to list left leaning sources as having mixed or low factuality."* / *"Oversimplified one-dimensional political spectrum that doesn't make sense for many countries... Unreliable detection of 'same story'... Dark patterns that make you jump through extra hoops to share links."* — bu son alıntı özellikle önemli: **kendi "aynı olayı tekilleştirme" (clustering) özelliğinin güvenilmez olduğunu** kullanıcı fark etmiş. World Pulse fikrimizin çekirdek mekaniği (20 kaynağı tek karta indirme) tam bu noktada — Ground News'in başarısız olduğu yerde iyi yapmak gerçek bir kazanım ama aynı zamanda ne kadar zor olduğunun kanıtı.
- **Paywall dark pattern:** *"Rudely designed setup screens... the design of that screen where it prompts you to accept a free trial is aggressive and clearly designed in a way that makes it difficult to realize [it's optional]."*
- **Talep görmezden geliniyor:** *"the most negative thing about this company is they flat out ignore [requests to stop sending emails]."*
- **AI brief kalitesi zayıf, klişeye kaçıyor:** *"The email summaries are particularly poor, relying on shallow regional stereotypes like 'East Coast Elite' and 'West Coast Innovator'. Basically, you get dumber from reading their [summaries]."* — BlindSpot/World Pulse'ta AI brief yazarken kaçınılması gereken somut bir tuzak: bölgesel/politik klişelerle "özetlemek" gerçek sentez değil, gerçek sentezin karikatürü.

**Bizim için:** Ground News §5 raporunda "risk doğrulandı" dediğimiz şey burada isim isim somutlaşıyor. Coğrafi kaynak dağılımı yaklaşımımız hâlâ doğru bir farklılaşma ama "same story" tekilleştirmesini Ground News'ten daha güvenilir yapmadan bu alana girmek aynı güven krizini miras alır demek.

### ATC – Live Air Traffic Radio — 134 / 315 negatif (%42.5) · trend: hafif kötüleşiyor, dalgalı (Şubat %31 → Haziran zirve %57 → Ağustos %43)

**Şikayet dağılımı:** Monetization %62.7 · Pricing %57.5 · Payment %18.7 · Feature Requests %16.4 · Design %16.4

- **Fiyat matematiği kullanıcı tarafından çözülmüş:** *"7days free then $89/year: You can't even try this app without selecting a payment option... you can choose to pay $6/week right away. That comes out to over $300/year if you stayed for a whole [year]."*
- **Ciddi faturalama hataları (tek şikayet değil, tekrarlayan desen):** *"Billing is a nightmare... Apple Store attempted a $99 charge that declined"* / *"Not cool at all... I got a charge of $111 from this app. That would make sense if I was paying for the annual subscription, but I wasn't."* — plan değiştirme akışında gerçek bir bug var gibi görünüyor, tek kullanıcının yanlış anlaması değil.
- **Atlanamaz onboarding, tekrar eden tema:** *"Annoying intro that is in-mutable and more importantly unskippable. Second, quit asking me survey questions at the beginning."* / *"Not an app it's a five minute advertisement."*
- **Konsept sevilen ama fiyat kızdıran, en net özeti:** *"Really awesome, Absurd Pricing: The app is extremely clean and simple to use... Just how clean the app is and how good it could be is the reason it is getting more than one star. The price is absurd. Not everything needs to be a subscription."*

**Bizim için:** ATC negatif yorumlarının çoğunluğu ürünü değil fiyatı ve satın alma akışını hedefliyor — konsept (canlı ATC + AI transkript + harita) neredeyse hiç eleştirilmiyor. Aviation Radio'yu hayata geçirirsek en ucuz kazanım muhtemelen "aynı konsept, dürüst fiyatlama akışı" olur; ürün kalitesiyle rekabet etmemize bile gerek kalmayabilir.

### FlightDeck – Flight Tracker — 98 / 140 negatif (%70.0, en yüksek oran) · trend: iyileşiyor ama hâlâ kötü (Nisan %100 → Ağustos %56)

**Şikayet dağılımı:** Monetization %52.0 · Pricing %51.0 · Performance And Bugs %22.4 · Payment %21.4 · Feature Requests %16.3

- **Ürünün kendi vaadini bozan performans sorunu:** *"Every [time it] loads incredibly slow, if at all... I'll regularly open the app to identify a plane, wait 30 seconds while nothing loads, open flightradar, watch an ad and then identify the flight on flightradar before [coming back]."* — kullanıcı, ücretli uygulamayı terk edip ücretsiz rakibi (FlightRadar24, reklamlı) workaround olarak kullanıyor. Bu tek yorum, "ücretli olmak yetmiyor, işe yaramak lazım" ilkesinin en net kanıtı.
- **Deneme süresi bittiğinde değil, başlarken ücretlendirme:** *"Subscription was canceled within the free trial on the first day that I began it. I was still charged the full price three days later and Apple was unable to refund the charge because of misleading terms within the app itself."* / *"Apple billed me for the subscription after i forgot to cancel, immediately tried to refund and even though I had not even touched the app since i started the free trial was denied a refund."*
- **Atlanamaz onboarding + free trial yok (ATC'nin aynı hatası, daha kötü versiyonu):** *"Here's a 10 minute, unskippable tutorial, in case you've never used a touch screen in your life. At the end, there's no free trial just a mandatory pay wall to see if you like it, all for giving you information that's readily available [elsewhere]."*

**Bizim için:** FlightDeck, ATC'nin yaptığı her hatayı (atlanamaz onboarding, agresif faturalama) tekrarlamış ve üstüne performans sorunları eklemiş — negatif oranı %70 ile örneklemdeki en yüksek uygulama. ACARS özelliği gerçek bir farklılaşma olsa da, temel işlevi (uçuş arama, harita) güvenilir çalıştırmadan hiçbir özellik kurtarmıyor. Aviation Radio'ya başlarken önceliğin "yeni özellik" değil "temel akışın kesintisiz çalışması" olduğunun kanıtı.

