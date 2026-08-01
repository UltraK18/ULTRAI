# ULTRAI

Sürekli devam eden yapay zeka işleri için bir Windows masaüstü uygulaması. Tek pencerede dört mod — konuşun, gerçek bir proje klasöründe geliştirin, bir tuval üzerinde tasarlayın, görsel ve video üretin — buna ek olarak zamanlama, çoklu ajan çalıştırmaları ve telefonunuzu ikinci ekran olarak kullanma.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> Bu depo yalnızca **sürüm dağıtımı** içindir. Kaynak kodu burada yayımlanmaz.

---

## İndirme

Windows 10 / 11 (x64). Çoğu Windows kurulumunda zaten bulunan WebView2 çalışma zamanını gerektirir.

**[En son sürümü indirin](https://github.com/UltraK18/ULTRAI/releases/latest)** — `ULTRAI_x.y.z_x64_en-US.msi` dosyasını alın ve çalıştırın.

Bundan sonra uygulama kendi bakımını üstlenir: açılışta ve düzenli aralıklarla yeni sürümleri denetler, bir güncelleme olduğunda haber verir ve onu yerinde kurar.

## Dört mod, tek pencere

Her mod, kendi araçlarına ve kendi ajanlarına sahip, amaca özel bir ekrandır — ama uygulama tek, ayarlar tek, geçmişinizin yaşadığı yer tek.

| Mode | The screen | What you do there |
| :--- | :--- | :--- |
| **Chat** | Konuşma | Herhangi bir sağlayıcı ve model, mesaj başına akıl yürütme çabası, alıntılı derin araştırma, dosya ve görsel girişi |
| **Code** | Gerçek bir proje klasörü | Dosya ağacı, inceleme panelinde diff'ler, sohbetin yanında bir terminal, diske herhangi bir şey dokunmadan önce izin istemleri |
| **Design** | Canlı tuval + tasarımcı ajan | Ekranlar oluşturuldukça sohbetin yanında render edilir; tamamlanan iş gerçek dosyalar olarak Code'a devredilir |
| **Studio** | Serbest biçimli tuval + sohbet | Görsel ve video üretin, bunları yerleştirip yeniden düzenleyin, kendi dosyalarınızı ekleyin, oradakiler üzerinde yinelemeye devam edin |

Mod değiştirmek hiçbir şeyi yeniden başlatmaz — her mod kendi konuşmalarını saklar ve kenar çubuğu bulunduğunuz moda ait olanları gösterir.

## Arayüz, asıl mesele

Bu alandaki araçların çoğu bir terminal ya da bir sarmalayıcı içine konmuş bir web sayfasıdır. ULTRAI ise
bir araya getirilmiş değil, tasarlanmış bir masaüstü uygulamasıdır.

- **Gerçekten cam olan cam** — yüzen yüzeyler bir bulanıklaştırma filtresi değil, küçük bir render motoru
  çalıştırır. Çerçeve için bir normal harita pişirir, bundan speküler vurgular çizer ve yüzeyin arkasındakini
  yer değiştirerek kenarların kırılmasını sağlar. Anahtar ve kaydırıcı gibi kontroller daha da ileri gidip
  bir kırılma indisi ve kalınlıkla Snell kırılmasını çözer, böylece tutamaç altındaki izi büker. Bir CSS
  frost efekti bunu yapamaz ve fark her kenarda görülür.
- **Squircle köşeler** — paneller dairesel bir yay değil, bir süperelips kullanır; böylece eğri,
  `border-radius`'tan elde ettiğiniz düz noktayı oluşturmadan dümdüz kenara girer.
- **İki tema, ikisi de özenle tasarlandı** — açık ve koyu tema, hafif soğuk tonlu tek bir beton renk
  paletinin üzerine kurulu ve hiçbir uçta göz alıcı bir şey olmayacak şekilde ayarlanmış. Her yüzey bir
  token'dır, bu yüzden bütün uygulama ekrandan ekrana savrulmak yerine birlikte hareket eder.
- **Bilinçli ölçülülük** — üründe hiçbir yerde emoji, ünlem işareti ya da abartılı teşvik dili yok. Her
  panel tek bir yüzey taşır; ayrım, kutu içine çizilmiş kutulardan değil, kenar ışığından ve gölgeden gelir.
- **Dikişsiz pencere** — uygulamanın arka planını paylaşan, Windows 11 ölçülerinde 32 piksellik bir başlık
  çubuğu; böylece çerçeve, içeriğin üzerinde ayrı bir şerit gibi algılanmaz.
- **Mobil, küçültülmüş değil farklı bir düzendir** — alt sayfalar, tam genişlikte kontroller ve dokunmaya
  uygun boyutta hedef alanlar; pencere genişliğine değil cihaza göre belirlenir.

## Gerçek modellerle üretim

Studio tek bir görsel uç noktası değildir. Her iş için bir katalogdan seçim yapar ve hangi modeli neden kullandığını size söyler.

- **Video** — Veo 3.1 ve Veo 3.0 (ayrıca hızlı varyantları), Sora 2 ve Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Görsel** — GPT Image 2 ve 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (ve Flash Lite), Grok Imagine Image
- **Video girdi, video çıktı** — girdi olarak yalnızca bir istem değil, mevcut bir klip de verebilirsiniz
- **Kendi işini kontrol eder** — ürettiği şeyden kareler çıkarır, onlara bakar ve yeniden denemesi gerekip gerekmediğine karar verir
- **Süre, en-boy oranı ve kalite sizin elinizde** — 30 saniye istediyseniz üretilen de tam olarak 30 saniyedir, istediğiniz biçimde

Hangi modellere ulaşabileceğiniz, bağladığınız sağlayıcı hesaplarına bağlıdır (Vertex AI, OpenAI, xAI).

## ULTRA modu — çok sayıda ajan, tek bir iş

Tek bir bağlam için fazla büyük işler içindir. ULTRA, işi görevlere böler, bunları aşama aşama ajanlar arasında çalıştırır ve sonuçların **birleştirilmeden önce bağımsız biçimde doğrulanmasını** sağlar — kendi kendini notlandıran aynı ajan değil, bir eleştirmen ve çekişmeli kontroller. Çalıştırmayı izler, istediğiniz noktada araya girebilirsiniz. Model ve akıl yürütme çabası rol başına ayarlanır, böylece ucuz bir işçi ile pahalı bir doğrulayıcı kasıtlı olarak farklı sağlayıcılar olabilir.

## Randevularına sadık kalır

"her hafta içi saat 9'da" ya da "iki saat sonra" deyin, bu bir nota değil gerçek bir işe dönüşür. Zamanı geldiğinde görev o konuşmada bir tur olarak gelir ve yapay zeka üzerinde çalışmaya başlar.

- Bir takvim ve bir liste kayıtlı olan her şeyi gösterir; bir sonraki çalıştırma kenar çubuğunun altında yer alır
- Bir şeyin zamanı geldiğinde uygulama kapalıysa? Neyi kaçırdığını hesaplar ve bunu tek bir telafi çalıştırmasında birleştirir
- `/loop`, belirlediğiniz kadar tur boyunca bir görevi tekrarlar

## Yapay zekanın tamamlandı diyemeyeceği hedefler

Bir konuşma için bir hedef belirleyin, tamamlanmayı bağımsız bir değerlendirme kapıdan geçirir. İşi yapan ajan işin bittiğine kendi kendine karar veremez.

## Derinlemesine araştırma ve işten önce sorular

**Deep research**, önce açıları planlar, ardından alt ajanlar arasında paralel olarak arama yapıp okur ve bulduklarına atıfta bulunur. Günlük arama da olağandışı derecede sıkıdır: modelin tahmin etmek yerine arama yapması, eğitimden kalma bir yıl yerine bugünün tarihini kullanması ve şimdiki zamanla ifade edilen iddiaları yanıtlamadan önce doğrulaması istenir. Bulgular, kaynaklar metin içinde belirtilerek tarafsız biçimde sunulur.

**Deep interview** — bir istek yeterince net tanımlanmadığında, konuşmayı yapılandırılmış bir görüşmeye dönüştürür ve herhangi bir iş başlamadan önce gerçekte ne istediğinizi netleştirir.

## Siz başka bir şey yaparken çalışan işler

Uzun süren işler pencereyi rehin almaz.

- **Arka plan çalıştırmaları** — bir görevi devredin, konuşmanın bir çatalı ya da bir alt ajan olarak izole
  biçimde çalışır ve bir engelle karşılaşırsa çalışma sırasında ek izin isteyebilir.
- **Canlı bir izleyici** — alttaki bir çubuk o an sürmekte olan her şeyi aynı anda gösterir: kendi arka plan
  görevleriniz, başka yerde başlatılanlar, çalışan alt ajan çağrıları, ULTRA çalıştırmaları ve bir süredir
  devam eden herhangi bir kabuk komutu. İzlemek istediğiniz herhangi birine tıklayıp geçebilirsiniz.
- **Bir konuşmayı çatallayın** — özgün olanı kaybetmeden bir şey denemek için herhangi bir noktadan
  dallanın ve mesaj dizininden dallar arasında geçiş yapın.

## Modlar arası devir

İş, başladığı modda sıkışıp kalmaz. Design, tamamlanan ekranları diskte gerçek dosyalar olarak Code'a
devreder. Code oturumları birbirlerine sorular ve sonuçlar iletir. Studio, bir ajanın ürettiğini doğrudan
tuvale yerleştirir. Her devir, kopyalanmış bir metin bloğunu değil, gerçek dosyaları ya da gerçek turları
taşır.

## Yapay zekanın dosyalarınıza dokunmadan kullanabileceği bir çalışma alanı

Chat modu diskte kendi taslak alanına sahiptir. Yapay zeka orada — taslaklar, betikler, ara dosyalar — her
adımda sizden izin istemeden ve kendi klasörlerinize uzanmadan serbestçe yazabilir, okuyabilir,
çalıştırabilir ve gözden geçirebilir. Bunun nerede olduğunu hiç düşünmenize gerek kalmaz; yalnızca sonucu
alırsınız ve siz işaret etmedikçe kendi dizinleriniz dokunulmamış kalır.

## Birbiriyle konuşan oturumlar

Code modunda bir oturum, bir soruyu ya da sonucu bir başkasına devredebilir — backend üzerinde çalışan oturum, frontend'i bilen oturuma soru sorabilir. Mesajlar diğer konuşmada gerçek bir tur olarak gelir. Kanalı siz açarsınız; hiçbir şey kendiliğinden bağlanmaz.

## Telefonunuz ikinci bir ekran

Sunucuyu açın ve aynı ağdaki bir telefon tarayıcısından ULTRAI'yi açın. Mobil düzen, küçültülmüş bir masaüstü değil, dokunma için tasarlanmıştır — alt sayfalar ve tam genişlikte kontroller. Konuşmalar, modeller ve ayarlar paylaşılır, böylece tam olarak kaldığınız yerden devam edersiniz.

## Kendinize göre şekillendirin

Aşağıdakilerin tümü, diskinizde okuyabileceğiniz, düzenleyebileceğiniz ve sürümleyebileceğiniz sıradan dosyalardır.

- **Agents** — `~/.ultrai/agents/*.md`. Her şeye frontmatter karar verir: hangi modlarda görüneceği, hangi
  araçları kullanabileceği, hangi istem bölümlerini alacağı, hangi özelliklere (araştırma, hedefler,
  görüşme) izinli olduğu. Settings üzerinden düzenleyin; yerleşik ajanlar istediğiniz zaman özgün hâline
  geri döndürülebilir.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Modelin çekip kullanabileceği ya da sizin bir eğik çizgi
  komutu olarak çağırabileceğiniz yeniden kullanılabilir talimatlar. Her birini ayrı ayrı açıp
  kapatabilirsiniz.
- **Prompt modules** — sistem istemi bir katalogdan derlenir ve her ajanın frontmatter'ı hangi bölümleri
  alacağını seçer. Hiçbir şey bildirmezseniz ajanın istemi varsayılanla bayt bayt aynı kalır; düşünme
  biçimini değiştirmek için katılım sağlarsınız. Her mod, her şeye zorla uydurulmuş tek bir istem yerine,
  o tür iş için inşa edilmiş kendi istemiyle gelir.
- **MCP servers** — `ultrai.jsonc` içinde tanımlanır. Yerel ya da uzak, gerektiğinde kimlik doğrulamalı,
  sunucu başına açılıp kapatılabilir.
- **Memory** — üç kovada tutulur (sizinle ilgili, konular, alanlar); özetler enjekte edilir, ayrıntılar
  talep üzerine getirilir ve yinelenenlerle çelişkileri birleştiren periyodik bir temizleme geçişi
  bulunur. Yalnızca Chat modunda, ve her girdiyi Settings üzerinden görüp silebilirsiniz.
- **Providers** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter ve kendi anahtarlarınızla
  özel uç noktalar.

## Verileriniz kendi bilgisayarınızda kalır

Konuşmalar ve ayarlar **yalnızca kendi makinenizde** saklanır. Bir ULTRAI sunucusu yoktur — konuşmalarınız yalnızca kendi bağladığınız yapay zeka sağlayıcısına, kendi anahtarınızla gider.

Hiçbir şey toplanmaz ve telemetri bulunmaz.

## Hızlı Başlangıç

1. **Bir sağlayıcı bağlayın** — Settings → Providers altına API anahtarınızı ekleyin.
2. **Bir model seçin** — model ve akıl yürütme çabası, giriş çubuğunun sağında yer alır.
3. **Bir mod seçin** — kenar çubuğunun üstündeki sekmeler.
4. **Çalışmaya başlayın** — Code modunda bir klasör açın; diğer modlarda yalnızca konuşmaya başlayın.
5. **Bir işi devredin** — "her gece günümü özetle" deyin, uygulama bunu kendiliğinden üstlenir.

## Teknoloji Yığını

Tauri 2 üzerine kurulu yerel bir Windows uygulaması. Arayüz SolidJS ile yazılmıştır; backend, uygulamayla birlikte paketlenmiş tek bir ikili dosya olarak çalışır.

## Geri Bildirim

Hatalar ve özellik istekleri için [Issues](https://github.com/UltraK18/ULTRAI/issues) sayfasını kullanın.

## Lisans

ULTRAI freeware'dir. Kişisel ve ticari kullanım için ücretsizdir. Kaynak kodu kamuya açık değildir.

ULTRAI, [opencode](https://github.com/sst/opencode)'un bir fork'u olarak başladı ve onun çok ötesinde
yeniden inşa edildi, ancak hâlâ MIT lisanslı opencode kodunu içeriyor — Telif Hakkı (c) 2025 opencode.
MIT lisansı, uygulamayla birlikte gelen bildirimlerde tam metin olarak yer alır.
