# Ödev — 17. güne kadar (4) · zor + şık

Bu ödev, 1–17. günleri zorlar. Grid, medya sorgusu, form ve konum **yasak**. Çözüm dersin içinde yoktur.

Dosya adı: `rota-bilet.html`  
Stil `<style>` içinde dursun.

## Konu

**Rota Bilet** — Serhat’ın dört kent arası bilet ofisi. İstanbul, İzmir, Trabzon ve Van seferleri tek sayfada satılır gibi dursun. Şaka yok; düzenli, gerçek bir bilet sitesi gibi okunsun.

## Renk paleti

| Rol | Hex |
| --- | --- |
| Sayfa zemini | `#f2f5f8` |
| Kart / üst zemini | `#ffffff` |
| Ana renk | `#0f3d5c` |
| Koyu şerit / footer | `#0a2436` |
| Vurgu | `#d4a017` |
| Metin | `#142029` |
| İkincil | `#5a6b78` |
| Kenarlık | `#c8d2db` |
| Tablo çift satır | `#e6edf3` |
| Sefer — İstanbul | `#0f3d5c` |
| Sefer — İzmir | `#b86e18` |
| Sefer — Trabzon | `#1f6b4f` |
| Sefer — Van | `#4a5d8a` |

## Zorunlu bölümler

### 1. Üst bar
- Solda ofis adı (istersen `#logo`).
- Ortada/sağda menü: Seferler, Saatler, Tarifeler, İletişim (`flex` + `gap`).
- Sağda altın “Online” rozeti.
- Satır: `justify-content: space-between`, `align-items: center`.

### 2. Kapak şeridi (ters düzen)
- **Sol:** altın kutu — “Bilet al” + kısa not (ör. “Tek yön · 450 TL’den”).
- **Sağ:** büyük başlık + bir cümle.
- `space-between`, `flex-wrap`, `align-items: center`. Önceki ödev kapaklarını kopyalama.

### 3. Sefer kartları (iç içe flex)
Dört kart: İstanbul, İzmir, Trabzon, Van. Dışarıda flex + `gap` + `flex-wrap`.

Her kartın içinde `flex-direction: column`:
1. Üstte kent rengi şerit
2. Güzergâh adı (sınıf ile)
3. Kısa açıklama (kalkış / varış hissi)
4. Alt satır flex: solda süre veya fiyat, sağda “Seç” (`space-between`)

**Ek:** Van kartında `align-self: flex-end`.

### 4. Bugünün planı (oranlı yan yana)
- Sol `flex: 2` — görsel/kutu + kısa ofis metni.
- Sağ `flex: 1` — “Bugün” listesi (işaretsiz, column flex): 3 kalkış saati.
- `gap`, `align-items: stretch`.

### 5. Hat etiketleri
Yatay flex, `flex-wrap`, işaretsiz. En az 5 etiket (Tek yön, Gidiş-dönüş, Gece, Hızlı, Öğrenci…).

### 6. Tarife tablosu
Üç sütun: bilet türü, fiyat, not.  
`border-collapse`, koyu başlık, çift satır farklı zemin. En az 4 satır.

### 7. Footer (üç parça)
`space-between` + `align-items: center` + `flex-wrap`:
- sol: Rota Bilet  
- orta: kısa adres  
- sağ: © Serhat  

## Kullanılması gerekenler

| Gün | Zorunlu |
| --- | --- |
| 02–04 | sınıf + en az bir kimlik |
| 05 | palet |
| 06–07 | yazı tipi, metin |
| 08 | `rem` / `em` |
| 09–11 | padding, margin, border |
| 12 | `display` |
| 13 | `:hover` |
| 14 | liste + 3 sütunlu tablo |
| 15 | görsel sığdırma veya renkli kutu |
| 16–17 | `flex`, `gap`, `flex-wrap`, `justify-content`, `align-items`, `flex-direction: column`, `align-self`, `flex: 1` / `flex: 2` |

## Önizleme

[onizleme.html](onizleme.html)

## Bitince kontrol

- Altın kutu kapakta **solda** mı?
- Kartlarda column flex + alt satır `space-between` var mı?
- Van `align-self` ile ayrışıyor mu?
- Planda `flex: 2` / `flex: 1` belli mi?
- Tablo 3 sütun + şeritli mi?
- Footer üç parçalı mı?

[← 17. gün](ders.md) · [İçindekiler](../README.md)
