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

## Ek 2 — Uygulama bazında negatif yorum raporu (fiyat/ödeme hariç, ürün odaklı — 21 Ağustos revizyonu)

**Neden yeniden yaptık:** ilk versiyonda her uygulamanın negatif yorumlarını olduğu gibi analiz etmiştik, ama fiyatlama şikayetleri — özellikle iki uçuş takibi uygulamasında (ATC, FlightDeck) — hacim olarak her şeyi gölgede bırakıyordu (negatif yorumların ~%75'i). Fiyatlamanın sorun olduğunu zaten biliyoruz; asıl soru "fiyat bir kenara, ürünün kendisinde ne bozuk" sorusu. Bu yüzden her uygulama için **Monetization/Pricing/Payment etiketlerinden hiçbirini taşımayan** 1–2 yıldızlı yorumları ayrı bir havuzda topladık ve analizi o havuz üzerinden tekrarladık. (Bir review'da fiyat + ürün şikayeti birlikte geçiyorsa da havuz dışında tutuldu — amaç "saf ürün" sinyali.)

**Ürün-odaklı negatif havuzun boyutu, tüm örneklem içinde:**

| Uygulama | Toplam yorum | Fiyat hariç negatif | Payı |
|---|---|---|---|
| SmartNews | 550 | 269 | %48.9 |
| NewsBreak | 698 | 315 | %45.1 |
| Ground News | 244 | 65 | %26.6 |
| FlightDeck | 140 | 21 | %15.0 |
| ATC | 315 | 25 | %7.9 |

Bu tablo tek başına çarpıcı: **ATC ve FlightDeck'in negatif yorumlarının ezici çoğunluğu SADECE fiyatla ilgili** — ürünle ilgili saf şikayet payı sırasıyla %7.9 ve %15.0'a düşüyor. Yani konsept (canlı ATC + AI transkript + harita, ya da ACARS + uçuş takibi) aslında iyi karşılanıyor; asıl dert fiyatlandırma ve satın alma akışı. Haber uygulamalarında ise tam tersi: fiyatlama zaten küçük bir paydı, ürün şikayetleri değişmeden kaldı.

### NewsBreak — 315 saf ürün şikayeti / 698 toplam (%45.1)

**Şikayet dağılımı (bu havuzun içinde):** Content %66.7 · Advertisements %29.8 · Performance And Bugs %17.1 · Notifications %16.5 · Design %10.2

- **Kritik olayı kaçırma:** *"A police chase literally went through my neighborhood last night and ended with dozens of police officers with guns out looking for suspects in our front yard and this app had ZERO mention of it."* — "yerel haber" iddiasının kendi kanıtladığı en ciddi güven kırılması: gerçek bir olay, sıfır kapsama.
- **Kullanıcının kendi ağzından pozitif talep:** *"I wish this App was more positive but it's mostly all negativity and I get like eight notifications a day that people have died... I'd rather see more positive stuff."* — Happy variant / Local Pulse pozitif-kategori tezimizi rakibin kendi kullanıcısı doğruluyor.
- **Teknik güvenilirlik:** *"Story never comes up... I get a notification and click on it to open it, the app comes up with just a blank screen and it stays that way."*
- **Bildirim kontrolü yok:** *"i got this app for fast notification of NEWS... now i get 100 notifications a day about celebrity updates... to configure my push notifications i have to speak to..."* (destek akışına yönlendiriliyor, self-servis ayar yok)

**Bizim için:** En yüksek hacimli rakip (698 yorum) aynı zamanda kendi kullanıcısından en net "daha pozitif olsun" talebini alan rakip. Local Pulse + Verified Alerts ikilisi tam bu boşluğa oturuyor.

### SmartNews — 269 saf ürün şikayeti / 550 toplam (%48.9, en yüksek pay)

**Şikayet dağılımı:** Content %65.4 · Advertisements %35.3 · Performance And Bugs %17.8 · Comparative Feedback %17.1 · Feature Requests %9.3

- **Gamification tepkisi (rewards programı), kullanıcının kendi sözleriyle:** *"I've been a long-time user of SmartNews because it felt like a refreshing alternative to the algorithm-driven, attention-hijacking ecosystem... [now] Let us opt out of your points system."* / *"Reading the news isn't a game. And the way the developers have turned it into a game is frankly insulting."* — önceki raporumuzda "2026'da eklenen rewards programı" nötr bir özellik olarak listelenmişti; gerçek veri bunun ciddi bir geri tepme olduğunu gösteriyor.
- **Aylarca çözülmeyen bug:** *"TURN OFF THE HOURLY REFRESH!!!"* — kullanıcı önceki güncellemelerden (2025 sonundan) beri şikayet ettiğini belirtiyor; 6+ ay boyunca kapatılmamış.
- **Bildirim → içerik kopukluğu:** *"Clicking the notification doesn't always take you to the article... instead it just opens the app to the main feed. At that point the story is essentially [lost in the feed]."*
- **Performans:** *"Slows down iPad & freezes... the longer I read articles, the slower it gets scrolling and closing. Soon the whole thing freezes up... The only remedy is to shut down the iPad and reboot it."*

**Bizim için:** Saf ürün şikayeti payı en yüksek uygulama (%48.9) — gamification/rewards gibi "kullanıcıyı daha çok tutacak" sanılan özelliklerin ters tepebileceğinin somut kanıtı. Kendi ürünümüzde gamification eklerken (Sky Pulse'ın "gördüm" rozetleri gibi) bu riski göz önünde bulundurmalıyız.

### Ground News — 65 saf ürün şikayeti / 244 toplam (%26.6)

**Şikayet dağılımı:** Content %61.5 · Comparative Feedback %38.5 · Performance And Bugs %18.5 · Customer Support %12.3 · Accessibility %9.2

- **Metodolojiye somut, detaylı güvensizlik:** *"Because ground news only relies on two rating sources for bias determination, they do a poor job on their bias ratings. There is a high tendency to list left leaning sources as having mixed or low factuality."* / *"Oversimplified one-dimensional political spectrum that doesn't make sense for many countries... Unreliable detection of 'same story'... Dark patterns that make you jump through extra hoops to share links."* — bu son alıntı özellikle önemli: **kendi "aynı olayı tekilleştirme" (clustering) özelliğinin güvenilmez olduğunu** kullanıcı fark etmiş. World Pulse fikrimizin çekirdek mekaniği tam bu noktada.
- **Gerçek-zamanlılık iddiasıyla çelişen performans:** *"Lags realtime events... it lags breaking news by hours if not days in most cases... X is where to go for breaking news."*
- **Erişilebilirlik, yıllardır çözülmemiş ve ciddiye alınmıyor:** *"Have attempted to get Ground News to fix screenreader issues for years. They do not care about blind users. If this company gets big enough to pass the ADA minimum, then I will see them in court."* / *"Inadequate accessibility support... I was told to use Apple's accessibility options... it's annoyingly awkward to use."* — ATC'deki VoiceOver talebiyle aynı boşluk, farklı kategoride.
- **AI brief kalitesi zayıf, klişeye kaçıyor:** *"The email summaries are particularly poor, relying on shallow regional stereotypes like 'East Coast Elite' and 'West Coast Innovator'. Basically, you get dumber from reading their [summaries]."*

**Bizim için:** Fiyat bir kenara bırakıldığında Ground News'in gerçek ürün zaafları netleşiyor: tekilleştirme güvenilmez, "real-time" iddiası gerçek değil (saatler/günler gecikme), erişilebilirlik yıllardır ihmal edilmiş — üçü de World Pulse ve BlindSpot'ta doğrudan rekabet edebileceğimiz, ölçülebilir açık.

### ATC – Live Air Traffic Radio — sadece 25 saf ürün şikayeti / 315 toplam (%7.9, en düşük pay)

**Şikayet dağılımı (küçük örneklem, dikkatli okuyun):** Feature Requests %40.0 · Design %36.0 · Service %32.0 · Content %24.0 · Installation And Setup %20.0

- **Atlanamaz onboarding, en sık tekrarlanan tema:** *"Every time this app updates, you have to go through a 5+ minute, in-skippable, ridiculous intro."* / *"Annoying intro that is in-mutable... quit asking me survey questions at the beginning."* / *"Not an app it's a five minute advertisement."* — fiyatı hariç tutunca bile ürünle ilgili #1 şikayet hâlâ onboarding.
- **Erişilebilirlik, tek ama net bir talep:** *"I use voiceover, which is designed by Apple for blind and visually impaired users. Is it possible that you could make this app accessible for those of us who rely upon voiceover?"*
- **Kapsama boşlukları, isim isim:** *"Did not have my local airport RDU available."* / *"ATL was the nearest airport to Chattanooga. I want to listen to the ATC traffic for flights I see from my back porch."* / *"Limited to very few airports."*
- **Eksik özellik, uçuş takibinin sektör değişiminde kopması:** *"Can a flight be followed in its entirety? It seems to drop once the flight is handed off to a second departure or to center."*

**Bizim için:** Fiyatı devre dışı bırakınca ATC'nin ürününde neredeyse hiç şikayet kalmıyor (%7.9) — konsept gerçekten seviliyor. Kalan tek büyük şikayet **bizim de kolayca tekrarlayabileceğimiz bir hata**: atlanamaz/uzun onboarding. Aviation Radio'yu kurarken en ucuz ve en yüksek etkili karar muhtemelen "onboarding'i baştan atlanabilir yap" olacak — rakip bunu hâlâ çözmedi.

### FlightDeck – Flight Tracker — sadece 21 saf ürün şikayeti / 140 toplam (%15.0)

**Şikayet dağılımı (küçük örneklem):** Performance And Bugs %71.4 · Feature Requests %28.6 · Design %28.6 · Comparative Feedback %19.0 · Content %19.0

- **Temel işlev bozuk, yön bile yanlış:** *"Trying the 3 day trial and every flight I click on on the map shows wrong flight info. Plane obviously just left ORD and the info shows it inbound to ORD from Savannah."* — uçuş takibi uygulamasının en temel vaadi (nereye gittiğini doğru göstermek) çalışmıyor.
- **Ürün terk edilip ücretsiz rakibe geçiliyor:** *"I'll regularly open the app to identify a plane, wait 30 seconds while nothing loads, open flightradar, watch an ad and then identify the flight on flightradar before switching back."*
- **Kullanıcının kendi teşhisi, gerçek bir uyarı:** *"This app is a nice idea but it has strong AI code energy... I think a developer with better taste should take this idea and build a more user-friendly and less buggy app."* — ACARS konsepti seviliyor, uygulama güvenilmiyor.
- **Aynı onboarding hatası:** *"Endless intro to app... just let me use the app instead."*

**Bizim için:** FlightDeck'te fiyat hariç kalan tek büyük tema performans/güvenilirlik (%71.4) — ACARS gibi gerçek bir farklılaşma özelliği, temel harita ve arama çalışmadığı için değerini kaybediyor. Aviation Radio'da öncelik sırası netleşiyor: (1) temel akış hatasız çalışsın, (2) onboarding atlanabilir olsun, (3) ancak ondan sonra ACARS/ATC gibi farklılaştırıcı katmanlar. Fiyatlama stratejisi bu üçünden sonra gelir — rakiplerin ikisi de fiyatı düzeltmeden önce ürünü düzeltmesi gerekirken tam tersini yapmış.

