# Ödev — 17. güne kadar (5) · Audi satış

Bu ödev, 1–17. günleri tek sayfada bir araya getirir. **Alıştırma sayfasıdır**; resmi Audi sitesi değildir. Grid, medya sorgusu, form ve konum yoktur. Çözüm dersin içinde yoktur.

Dosya adı: `audi-satis.html`  
Stil `<style>` içinde dursun.

## Konu

**Audi Studio** — Serhat’ın hayali satış + kısa servis stüdyosu. Hem araç vitrini hem servis paketleri olsun. Koyu zemin, gümüş kenarlık, kırmızı vurgu.

## Renk paleti

| Rol | Hex |
| --- | --- |
| Sayfa zemini | `#0b0b0b` |
| Kart / panel | `#161616` |
| Üst / footer | `#000000` |
| Ana metin | `#f2f2f2` |
| İkincil | `#8f8f8f` |
| Gümüş kenarlık | `#3d3d3d` |
| Gümüş yazı | `#b8b8b8` |
| Kırmızı vurgu | `#c4001a` |
| Tablo çift satır | `#1f1f1f` |
| “Yeni” rozeti zemini | `#c4001a` |

## Sayfada ne olacak

### 1. Üst bar (iki katman)
- Üst satır: solda `#logo` → `AUDI`, sağda kısa etiket `Studio · Serhat`.
- Alt satır: koyu menü şeridi — Modeller, Servis, Test, Fiyatlar (`flex` + `gap`).
- Link `:hover` ile gümüş veya beyaz olsun.

### 2. Kapak (ortalı, tam genişlik)
- Ortalanmış başlık + cümle + “Vitrine in” linki (kırmızı veya gümüş çerçeveli).
- Flex column + `justify-content: center` + `align-items: center`.
- Min. yükseklik ~14–16 rem. Yan yana CTA kutusu **kullanma** (önceki sürümden farklı).

### 3. Araç kartları (4 model — yeni liste)
Modeller (isimleri sabitle):
1. **A1** — şehir  
2. **A6 Avant** — aile / yol  
3. **Q7** — SUV  
4. **RS 6** — performans (birinde kırmızı **Yeni** rozeti olsun)

Dışarıda flex + `gap` + `flex-wrap`.  
Her kart: görsel alan, model adı (sınıf), 1 cümle, fiyat, “İncele” (`:hover`).  
Kart içi: `flex-direction: column`.

### 4. Öne çıkan (ters düzen)
**Solda metin**, **sağda görsel** (önceki “görsel solda” düzeninin tersi).  
Flex, `gap`, `align-items: center`, `flex-wrap`. Konu: RS 6 veya Q7.

### 5. Servis paketleri (3 kart)
Yeni bölüm. Üç paket kartı yan yana (`flex` + `wrap`):
- Bakım  
- Lastik  
- Detaylı iç temizlik  

Her birinde başlık, kısa not, fiyat.

### 6. Test sürüşü saatleri
İşaretsiz flex etiket listesi (en az 4): ör. `10:00`, `12:30`, `15:00`, `17:30`.

### 7. Fiyat tablosu
3 sütun: Model, Başlangıç, Tip.  
`border-collapse`, siyah başlık, çift satır `#1f1f1f`.

### 8. Footer
Üç parça (`space-between` + `flex-wrap`):  
`AUDI Studio` · kısa adres · `© Serhat`

## Kullanılması gerekenler

| Gün | Ne |
| --- | --- |
| 02–04 | sınıf, `#logo` |
| 05 | koyu palet + `#c4001a` |
| 06–07 | yazı, harf aralığı (logo’da `letter-spacing` dene) |
| 08 | `rem` / `em` |
| 09–11 | padding, margin, border |
| 12–13 | `display`, `:hover` |
| 14 | liste + 3 sütun tablo |
| 15 | görsel / gradient kutu |
| 16–17 | `flex`, `gap`, `flex-wrap`, `justify-content`, `align-items`, kartlarda `flex-direction: column` |

## Önizleme

[onizleme.html](onizleme.html)

## Bitince kontrol

- Üst iki katmanlı mı?
- Kapak ortalı mı (yan CTA yok)?
- RS 6’da “Yeni” rozeti var mı?
- Öne çıkan metin solda, görsel sağda mı?
- Servis’te 3 kart var mı?
- Footer üç parçalı mı?

[← 17. gün](ders.md) · [İçindekiler](../README.md)
