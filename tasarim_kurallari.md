# Odyssey / Durak — Tasarım Kuralları (kilit)

Yeni ekran eklemeden önce burası. Renkler koda hard-code edilmez; token’lardan okunur.

## 1. Dil: Apple HIG

Clarity · Deference · Depth. Arayüz içeriğin önüne geçmez.

## 2. Renk

| Rol | Hex | Kullanım |
| --- | --- | --- |
| Primary | `#E05D34` | Birincil düğme, aktif sekme, ilerleme |
| Zemin | `#FFFFFF` | Ekran / tab bar |
| Metin | `#000000` / `#60646C` | Başlık / ikincil |
| Pasif | `#8E8E93` | Pasif sekme |
| Yüzey | `#F2F2F7` | Kart, MiniPlayer |
| Ayırıcı | `rgba(60,60,67,0.29)` | Hairline |

Tek vurgu rengi. Şimdilik yalnız **açık tema**.

## 3. Tipografi

SF Pro (iOS) / sistem (Android). Large Title 34 Bold → Caption 12. Dynamic Type’a uy.

## 4. Yerleşim

8 pt grid · kenar ≥16 · dokunma ≥44×44 · kart radius 12 · gölge yerine hairline.

## 5. Navigasyon (NİHAİ KARAR)

### Alt menü: EVET — tam 2 sekme (3. veya 4. sekme YASAK)

| Sekme | Ne | İkon |
| --- | --- | --- |
| **Keşfet** | Destinasyon kataloğu (ilk açılış) | `compass` |
| **Çantam** | İndirilen READY paketler, depolama | `briefcase` |

- Hesap: **yalnız avatar push** — sekme değil. Favoriler / Kategoriler / Harita sekmeleri yok.
- Push ekranlar (Destinasyon, POI, Görsel detay, Hesap, Tadım) ve Saha modunda **tab bar çizilmez**.
- Saha: READY sonrası tam ekran; ✕ ile çık.
- MiniPlayer tab’ın üstündedir; tab bar yerine geçmez.

### İlk açılış

1. Splash → **Keşfet** (il seçimi YOK, arama YOK v1).
2. Düzenleyici kapak kartları: gerçek destinasyonlar (örn. Efes, Hierapolis, Afrodisias).
3. Kullanıcı alandaysa + paket READY ise üstte «Sahadasın · Sahaya geç».
4. 8+ destinasyondan sonra: bölge başlıkları («Ege») — zorunlu il aşacı değil. Arama ancak o eşikte.

### Rota nedir?

Her destinasyon = **tek küratörlü yürüyüş rotası** (numaralı duraklar). Kullanıcı rota çizmez. Haritada polyline + pin’ler pakette gelir.

## 6. MiniPlayer

Ses çalarken **tab bar’ın hemen üstünde**, tüm Keşfet/Çantam ekranlarında. Saha modunda mini veya Live Activity. Yükseklik 56 · radius 12 · zemin `#F2F2F7` · primary ilerleme 2 pt.

## 7. Ses + görsel + metin (tek durak modeli)

**Kilit:** Bir durakta **tek anlatım sesi**. Görsellerin ayrı sesi / podcast’i **yok**.

1. **Dinle** — durağa ait tek ses (3–6 dk)  
2. **Ana görsel** — cephe/genel; üzerinde **numaralı görsel işaretler** ①②③ (max ~5)  
3. **İşarete dokun** — sheet: büyük görsel + müze metni (+ kanıt çipi). Ses MiniPlayer’da devam.  
4. **Örnek (Celsus):** ① heykel ② akantus ③ yazıt anlamı  
5. **Kaynakça** — sheet  

Buna **3D** demiyoruz; adı: numaralı görsel işaret.  
**Yapılmaz:** Unity şehir, AR, görsel başına ayrı ses, 3–4 sekmeli menü.

**v5 eklemeleri**
- İşaret sayısı durak başına 3–5 (Celsus: 4). Daire 36 pt, dokunma alanı 48 pt; beyaz dolgu + koyu rakam, aktifken saha turuncusu.
- `cueMs: [başla, bitir]`: ses aralığa girince işaret + lejant satırı + MiniPlayer bölüm adı birlikte değişir; biten işaret siyah. Haptik yok.
- Her kartta kanıt etiketi (Kanıtlı / Olası / Yorum) ve «Dayanak» satırı. Etiket kartın en zayıf iddiasını yansıtır.
- Duraklar metinle «Durak 11» diye yazılır; fotoğraftaki daireler çıplak 1–4.
- Saha: açık tema, ana metin ≥ 17 pt, birincil düğme 56 pt ve alt %35’te, saha turuncusu `#C2410C`.

## 8. Autoplay

Yok. Yakın kart → kullanıcı «Dinle».

## 9. İkon / hareket / a11y / dil

Ionicons · 200–350 ms · Reduce Motion · kontrast ≥4.5:1 · arayüz Türkçe.
