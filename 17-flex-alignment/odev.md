# Ödev — 17. güne kadar (3)

Bu ödev, 1–17. günleri tek sayfada bir araya getirir. Kafe ve pansiyon ödevlerinden farklıdır. Grid, medya sorgusu, form ve konum yoktur. Çözüm dersin içinde yoktur.

Dosya adı: `bahce-kitap.html`  
Stil, belgenin başındaki `<style>` içinde dursun.

## Konu

**Bahçe Kitap** — Serhat’ın bağımsız kitapçısı. Vitrinde dört kitap durur; her kitap bir kente bağlıdır (İstanbul, İzmir, Trabzon, Van). Sayfa gerçek bir kitapçı ana sayfası gibi okunsun.

## Sayfada ne olacak

1. **Üst (iki katman)**  
   Üst satır: solda `#logo`, sağda kısa bir etiket (ör. “Bağımsız kitapçı”).  
   Alt satır: koyu zeminli menü — Vitrin, Kategoriler, Saatler, İletişim. Flex + `gap`.

2. **Kapak (yan yana)**  
   Sol: büyük başlık + cümle. Sağ: sarı/vurgu kutusu içinde “Vitrine bak” linki.  
   `justify-content: space-between`, `align-items: center`, `flex-wrap`. Ortaya yığma.

3. **Vitrin kartları (yatay kart)**  
   Dört kitap. Her kartın içinde sol şerit (kapak rengi) + sağda metin.  
   Dışarıda flex + `gap` + `flex-wrap`. İçeride de flex.  
   Kartta: kent etiketi, kitap adı (sınıf), cümle, fiyat, “Sepete bak” (`:hover`).

4. **Dükkân hakkında**  
   Sol görsel, sağ metin. Solunda kalın renkli kenarlık olabilir. Flex + `gap` + `align-items`.

5. **Kategoriler**  
   İşaretsiz flex liste; maddeler dolu zeminli etiket gibi dursun.

6. **Saatler tablosu**  
   Tam genişlik. `border-collapse`. Başlık satırı koyu. Çift satırlar farklı zemin. İnce alt çizgi yeter; çift çerçeve olmasın.

7. **Footer**  
   Solda marka, sağda kısa not — `space-between` ile. Flex + `align-items: center`.

## Kullanılması gerekenler

| Gün | Ne kullanılsın |
| --- | --- |
| 02–04 | seçici, sınıf, `#logo` |
| 05 | renk, arka plan (kafe/pansiyon paletini kopyalama) |
| 06–07 | yazı tipi, metin |
| 08 | `rem` / `em` |
| 09–11 | padding, margin, border |
| 12 | `display` |
| 13 | `:hover` |
| 14 | liste + tablo |
| 15 | görsel sığdırma |
| 16–17 | `flex`, `gap`, `flex-wrap`, `justify-content`, `align-items` |

## Önizleme

[onizleme.html](onizleme.html) — yalnızca hedef. Asıl iş kendi yazmak.

## Bitince kontrol

- Kitap kartları vitrin gibi mi?
- Dar ekranda alta iniyorlar mı?
- Renkler önceki ödevlerden farklı mı?
- Hover ve tablo şeritleri var mı?

[← 17. gün](ders.md) · [İçindekiler](../README.md)
