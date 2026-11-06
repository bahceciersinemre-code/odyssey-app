# Odyssey tasarım sistemi

Yürürlük: Kasım 2026. Yeni ekran bu belgeye uyar. Renk, yazı boyutu ve aralık kodun içine gömülmez; aşağıdaki belirteçlerden okunur.

Belge bir arayüz tarifidir. Anıt metinleri, ses kayıtları ve fotoğraflar burada yoktur. Örnekler davranış içindir, belirli bir yapının içeriği değildir.

## 1. Ürün ve bağlam

Odyssey, antik bir yerde yürüyen kişi için çevrimdışı sesli rehberdir. Aynı durak, daha sonra eğitimde de kullanılır. İki iş için iki uygulama yoktur.

Saha koşulları tasarımın girdisidir:

- Ağ kesilir. İndirme bitmeden saha modu açılmaz.
- Ekran güneştedir. Saha görünümü açık temadadır.
- Telefon çoğu zaman tek elde, başparmak menzilindedir.
- Ziyaretçi ayaktadır ve yürür. Arayüz uzun okumaya zorlamaz; uzun metin etiketin içindedir, isteyerek açılır.

Apple Human Interface Guidelines bu işin dilidir: açıklık, içeriğe yol verme, derinlik. Arayüz eserin ve sesin önüne geçmez.

## 2. İlkeler

1. **Bir durak, bir ses.** Fotoğrafın üzerindeki işaretlerin kendi anlatımı yoktur.
2. **Bir destinasyon, bir rota.** Ziyaretçi rota çizmez. Haritadaki çizgi ve pinler paketin içindedir.
3. **İki sekme.** Keşfet ve Çantam. Üçüncü sekme açılmaz.
4. **Kendiliğinden çalma yok.** Yakın olmak dinlemeye izin değildir.
5. **Kanıt görünür.** Her etiket iddiasının gücünü söyler. Etiket, karttaki en zayıf iddiaya göre seçilir.
6. **Çevrimdışı varsayılan.** Kataloga bakmak için ağ gerekebilir. Yürümek için gerekmez.
7. **Tek vurgu ailesi.** Kimlik rengi kiremit turuncusudur. Saha düğmesi, güneşte okunması gerektiği için daha koyu bir turuncudur. İkinci bir marka rengi yoktur.

## 3. Renk

### 3.1 Belirteçler

| Belirteç | Hex | Nerede |
| --- | --- | --- |
| `color.brand` | `#E05D34` | Kimlik, katalogdaki birincil düğme, aktif sekme, ilerleme, büyük işaret |
| `color.field` | `#C2410C` | Saha modundaki birincil düğme, aktif görsel işaret, küçük ama okunması gereken vurgu |
| `color.bg` | `#FFFFFF` | Ekran, sekme çubuğu |
| `color.surface` | `#F2F2F7` | Kart, MiniPlayer |
| `color.text` | `#000000` | Başlık ve gövde |
| `color.text.secondary` | `#60646C` | İkincil satır |
| `color.inactive` | `#8E8E93` | Pasif sekme |
| `color.separator` | `rgba(60,60,67,0.29)` | Saç teli ayırıcı |

Gölge kullanılmaz. Ayrım, zemin farkı ve saç teliyle kurulur.

### 3.2 Neden iki turuncu var

`#E05D34` beyaz üstünde yaklaşık 3,6:1 kontrast verir. Büyük başlıkta, sekme renklerinde ve geniş dokunma alanındaki ikonda yerindedir. Küçük yazıda ve güneşteki ince çizgide yetersiz kalır.

`#C2410C` beyaz üstünde yaklaşık 5,2:1 verir. Saha düğmesi, aktif işaret ve ziyaretçinin güneşin altında ayırt etmek zorunda olduğu her küçük vurgu bu renktir. Marka turuncusu logodan ve katalogdan eksilmez. Saha, okunmayı seçer.

Karanlık saha teması yoktur. Açık zemin, güneşte kaybolmaz. Karanlık tema ancak açık havada denendikten sonra konuşulur.

### 3.3 Kanıt etiketleri

Etiketler marka rengiyle boyanmaz. Anlam renkleridir ve kendi zeminlerinde en az 4,5:1 kontrast tutar.

| Etiket | Yazı | Zemin | Anlam |
| --- | --- | --- | --- |
| Kanıtlı | `#1B6E45` | `#E5F4EC` | Yazıt, kazı kaydı veya birincil yayınla taşınan iddia |
| Olası | `#7A4A00` | `#FFF1D1` | Kanıtın taşıdığı ama kilitlemediği yorum |
| Yorum | `#3640A0` | `#EAECFF` | Karşılaştırma, çağrışım, rehberin çerçevesi |

Bir kartta üç tür iddia birden varsa etiket en zayıf olanıdır. Kartın altında tek satırlık **Dayanak** vardır: neden bu etiket. Dayanak, kaynakça listesinin yerine geçmez. Kaynakça etiketin sonundadır.

## 4. Tipografi

Yazı tipi iOS'ta SF Pro, Android'de sistem yazısıdır. Dynamic Type desteklenir. Saha modunda gövde, ziyaretçinin ayarı ne olursa olsun 17 pt'nin altına inmez.

| Rol | Boyut | Ağırlık |
| --- | --- | --- |
| Large Title | 34 | Bold |
| Title 1 | 28 | Bold |
| Title 2 | 22 | Bold |
| Headline | 17 | Semibold |
| Body | 17 | Regular |
| Callout | 16 | Regular |
| Subhead | 15 | Regular |
| Footnote | 13 | Regular |
| Caption | 12 | Regular |

Uzun tüm-büyük-harf başlık yazılmaz. Türkçe ekler kırpılmaz. Bir satıra sığmayan özel ad, punto küçültülerek değil, ikinci satıra geçirilerek çözülür.

## 5. Yerleşim ve dokunma

Ölçü birimi 8 pt'dir. Ekran kenarı en az 16. Kart köşesi 12. Birincil dokunma alanı en az 44 × 44 pt.

| Öğe | Ölçü |
| --- | --- |
| Görsel işaret dairesi | 36 pt |
| İşaretin dokunma alanı | 48 pt |
| MiniPlayer yüksekliği | 56 |
| MiniPlayer ilerleme çizgisi | 2 pt |
| Saha birincil düğmesi | yükseklik 56, ekranın alt %35'inde |
| Sekme çubuğu | sistem yüksekliği, içeriğin üstüne binmez |

İşaret dairesi beyaz dolgu ve koyu rakamdır. Aktif işaret saha turuncusuna döner. Süresi geçmiş işaret siyaha çekilir ve yerinde kalır. Ziyaretçi, anlatının nerede olduğunu da, nereyi geçtiğini de görür.

Başparmak bölgesi saha ekranında çizilmez. Birincil eylem oraya konur. Kapatma, ses ve işaretler birbirinin üstüne binmez.

## 6. Gezinme

### 6.1 İki sekme

| Sekme | İş | İkon |
| --- | --- | --- |
| Keşfet | Destinasyon kataloğu. Uygulamanın ilk ekranı. | `compass` |
| Çantam | İndirilmiş paketler ve kapladıkları yer. | `briefcase` |

Hesap, sekme değildir. Sağ üstteki avatardan açılan bir sayfadır. Favoriler, kategoriler ve harita ayrı sekme olmaz. Harita, destinasyonun ve sahanın içindedir.

### 6.2 Sekme çubuğunun olmadığı yerler

Şu ekranlar tam sayfadır, sekme çubuğu çizilmez:

- Destinasyon
- Durak
- Görsel etiket
- Tadım (paketi indirmeden önceki kısa dinleme, varsa)
- Hesap
- Saha

Saha, paket hazır olduktan sonra açılır ve kapatma ile çıkılır. MiniPlayer bir sekme değildir. Keşfet ve Çantam'da sekme çubuğunun hemen üstünde durur. Sahada ya aynı şerit ya da kilit ekranındaki canlı etkinlik kullanılır. İkisi birden bağırmaz.

### 6.3 İlk açılış

1. Kısa açılış, sonra Keşfet.
2. Kapak kartları gerçek destinasyonlardır. Boş bir "yakında" ızgarası kataloğun yerine konmaz.
3. Ziyaretçi alandaysa ve paket hazırsa, kataloğun üstünde tek satır durur: «Sahadasın · Sahaya geç».
4. Sekiz destinasyondan önce arama ve il listesi yoktur. Sekizden sonra destinasyonlar bölge başlığı altında toplanabilir («Ege»). Bu bir idari ağaç değildir. Arama bu eşikte açılır.

### 6.4 Rota

Her destinasyon tek küratörlü yürüyüştür. Duraklar numaralıdır. Metin «Durak 4» diyebilir. Fotoğrafın üstündeki daireler ise yalnızca o fotoğrafın görsel indeksidir: 1, 2, 3, 4. Rota numarası ile fotoğraf işareti aynı sayı değildir ve aynı tipografide yazılmaz. Biri yerin sırasıdır, diğeri resmin içindeki bakış noktasıdır.

## 7. Durak

Durak ekranının üç katı vardır. Üçü de aynı anda bağırmak zorunda değildir.

### 7.1 Dinle

Durağın tek sesi. Süre çoğu durakta 3 ile 6 dakika arasındadır. Bu bir hedeftir, bir kesme aleti değildir: yazıt uzunsa anlatı uzar, avlu kısaysa kısalır. Düğmenin adı **Dinle**dir. Çalıyorsa düğme durumu gösterir, ikinci bir ses başlatmaz.

### 7.2 Ana görsel

Cephe ya da durağın bütününü veren tek fotoğraf. Üstünde 3 ile 5 arası numaralı işaret. Beşin üstü, o durağın ikinci bir durağa bölüneceğini gösterir. İşaret, fotoğrafın üzerinde sabit bir orana bağlıdır. Ekran boyu değişince işaret kaymaz.

### 7.3 Etiket

İşarete dokunulunca alttan bir sayfa açılır. İçinde:

- Büyük görsel
- Kısa başlık
- Müze etiketi uzunluğunda metin
- Kanıt çipi
- Dayanak satırı
- Kaynakça

Sayfada oynatma düğmesi yoktur. Ses, MiniPlayer'da sürer. Sayfayı kapatmak sesi kesmez. Görsel yüklenemezse kırık resim ikonu gösterilmez. Yerine, aynı kadrajda düz bir zemin ve etiketin başlığı gelir. Metin her durumda okunur.

### 7.4 Anlatı ile işaret

Her işaretin anlatı içinde bir aralığı vardır. O aralıkta üç şey birlikte değişir: fotoğrafın üstündeki aktif daire, lejant satırı, MiniPlayer'daki bölüm adı. Aralık bitince daire siyaha döner. Titreşim yoktur. Ziyaretçi cımbızla saniye aramaz. Anlatıyı sararsa aktif işaret, yeni konuma göre güncellenir.

## 8. MiniPlayer

Ses çalarken görünür. Yükseklik 56, köşe 12, zemin `color.surface`, ilerleme `color.brand` ve 2 pt.

Üzerinde durağın adı, bölüm adı ve oynat / duraklat vardır. İleri-geri on beş saniye, saha dışında ikincil eylemdir. MiniPlayer bir destinasyondan diğerine atlamaz. Ziyaretçi başka bir durağı seçerse geçiş açık olur: çalan durak durur, yeni durak kendiliğinden başlamaz.

## 9. Saha modu

Saha, paketin indirildiği ve doğrulandığı andan sonra vardır. Yarım inmiş paketle sahaya girilmez.

- Açık tema.
- Gövde en az 17 pt.
- Birincil düğme 56 pt ve alt bölgede, rengi `color.field`.
- «Yakında» bilgisi, varsa, bir durum satırıdır. Yaklaşmak sesi başlatmaz.
- Kapatma her zaman ulaşılır bir yerdedir.
- Sekme çubuğu yoktur.

Güneş altında kontrastı ancak masada ölçülmüş bir renk, saha rengi sayılmaz. Yeni bir saha rengi, açık havada okunmadan belgeye girmez.

## 10. Katalog, indirme, çanta

Keşfet kartında destinasyonun adı, bölge ve yürüyüşün kabaca süresi vardır. Fiyat ya da edinme durumu kartın ikincil satırındadır, kapağın üstüne basılmaz.

İndirme ilerlerken ziyaretçi kataloğa dönebilir. Çantam, inen paketi «indiriliyor» olarak gösterir. İndirme yarıda kesilirse kalan baytlar sürdürülür. Dosya bütünlüğü tutmazsa paket hazır sayılmaz ve saha açılmaz. Ziyaretçiye nedenini tek cümleyle söyleriz, hata koduyla değil.

Çantam, hazır paketleri ve kapladıkları yeri gösterir. Silmek, iki adımlıdır. Silinen paketin anlatı konumu da cihazdan gider. Bunu silme onayında söyleriz.

Tadım, paketin kısa bir ön dinlemesidir. Tadım sahayı açmaz ve işaretlerin tam metnini dağıtmaz.

## 11. Boş, meşgul, bozuk

| Durum | Davranış |
| --- | --- |
| Katalog boş | Uydurma destinasyon konmaz. Kısa açıklama ve yeniden deneme. |
| Katalog eskidi, ağ yok | Son başarılı katalog gösterilir. Tarih, ikincil satırdadır. |
| İndirme sürüyor | İlerleme ve iptal. Ekran kilitlenebilir. |
| Doğrulama bozuk | Hazır işaretlenmez. Yeniden indir. |
| Fotoğraf yok | Düz zemin ve başlık. Kırık ikon yok. |
| Ses dosyası yok | Dinle düğmesi pasif. Etiketler açılabilir. Durak, sessiz bir etikete düşer, çökmez. |
| Hesap yok | Yürümek hesap istemez. Hesap, indirme hakkı ve cihazlar arası geri yükleme için vardır. |

## 12. Hareket, ikon, erişilebilirlik

Süre 200 ile 350 ms arasındadır. Easing sistem varsayılanıdır. Reduce Motion açıksa sayfa kayması ve işaret geçişi kesilir, durum anında değişir. Bilgi kaybı hareketin içinde gizlenmez.

İkonlar Ionicons çizgisindedir. Anlamı yalnızca renkle taşıyan bir kontrol yoktur. Kanıt çipinin metni her zaman yazılır.

Erişilebilirlik tabanı:

- Gövde metni ve çip yazısı en az 4,5:1.
- Büyük başlık ve geniş ikon en az 3:1. Marka turuncusu bu sınıftadır.
- Saha düğmesi ve aktif işaret en az 4,5:1. Bu yüzden `color.field`.
- Her düğmenin erişilebilir adı vardır. «1» diye bir işaret, sesli okuyucuda «işaret 1, başlık» olarak okunur.
- Odak sırası görsel sıradır: kapat, başlık, dinle, işaretler, etiket.

## 13. Dil ve üslup

Arayüz Türkçedir. Ses kayıtları da Türkçedir. Başka bir dil, ayrı bir paket sürümüdür, aynı ekranda karışık yazılmaz.

Üslup müze etiketidir. Coşku sıfatı, ünlem ve «eşsiz» yoktur. Özel adlar ilk geçtiği yerde tam yazılır. Ziyaretçiye «sen» denmez. Düğmeler emirdir ve kısadır: Dinle, İndir, Sahaya geç, Kapat, Sil.

Hata metni özür dilemez ve suçu ziyaretçiye atmaz. Ne olduğu ve tek bir sonraki adım yazılır.

## 14. Kapsam dışı

Aşağıdakiler sonraki bir sürümün fikri olarak belgede beklemez. Bilinçli olarak yapılmaz.

- Artırılmış gerçeklik ve cihaz kamerasıyla «yerleştirilmiş» model
- Üretilmiş üç boyutlu kent
- İşaret başına ayrı ses veya kısa podcast
- Üçüncü ve dördüncü sekme
- Ziyaretçinin çizdiği rota
- Yakınlıkla başlayan ses
- Saha için karanlık tema
- Kırık görselin yerine dekoratif illüstrasyon

Numaralı görsel işaret bir üç boyut teknolojisi değildir. Fotoğrafın üzerinde, anlatıyla eşleşen bir indekstir. Belgede ve arayüzde adı budur.

## 15. Uygulayıcıya not

Yeni bir ekran açmadan önce üç soru sorulur:

1. Bu iş Keşfet, Çantam, Saha veya bir itme sayfasından hangisine aittir? Yeni bir sekme cevabı kabul edilmez.
2. Bu ekran ağ kesikken açılabiliyor mu? Sahadaysa cevap evet olmak zorundadır.
3. Bu ekrandaki en küçük turuncu iz, güneşte 4,5:1 tutuyor mu? Tutmuyorsa renk `color.brand` değil `color.field` olur.

Üçüne de cevap veremeyen ekran çizilmez.
