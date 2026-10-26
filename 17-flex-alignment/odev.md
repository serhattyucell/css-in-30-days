# Ödev — 17. güne kadar (yeni)

Bu ödev, 1–17. günleri tek sayfada bir araya getirir. Önceki “dört kent kartı” ödevinden farklıdır. Grid, medya sorgusu, form ve konum yoktur. Çözüm dersin içinde yoktur.

Dosya adı: `nota-kafe.html`  
Stil, belgenin başındaki `<style>` içinde dursun.

## Konu

**Nota Kafe** — Serhat’ın hayali bir kafe sitesi. Mekân dört kentte şube açmış gibi dursun: İstanbul, İzmir, Trabzon, Van. Sayfa gerçek bir kafe ana sayfası gibi okunsun; kart galerisi gibi değil.

## Sayfada ne olacak

1. **Üst menü**  
   Solda kafe adı (`#logo` veya `.logo`), sağda 4 link: Menü, Şubeler, Saatler, İletişim. Hepsi tek satırda, dikey ortalı, `space-between`.

2. **Kapak şeridi (hero)**  
   Geniş bir bant. İçinde kafe adı, bir cümle ve “Menüye bak” linki. Flex ile yatay ve dikey ortala. Arka plan rengi veya görsel olsun.

3. **Öne çıkan**  
   Solda büyük bir görsel (`max-width: 100%`, `height: auto`), sağda başlık + kısa metin + “Detay” linki (`:hover`). İki sütun flex ile yan yana; `gap` ve `align-items` kullan.

4. **Üç ürün kartı**  
   Üç içecek veya tatlı. Flex satır, `gap`, `flex-wrap`. Her kartta görsel, ad (sınıf ile), kısa açıklama, fiyat, kenarlık + padding + margin.

5. **Şube listesi**  
   Dört kent işaretsiz listede. Flex ile yatay veya dikey dizilsin.

6. **Saatler tablosu**  
   İki sütun: gün ve saat. `border-collapse`, çift satırlar farklı zemin.

7. **Alt bilgi**  
   Ortada tek satır (adres veya “Nota Kafe — Serhat”). Footer flex ile ortala.

## Kullanılması gerekenler

| Gün | Ne kullanılsın |
| --- | --- |
| 02–04 | seçici, sınıf, en az bir kimlik |
| 05 | renk, arka plan |
| 06–07 | yazı tipi, metin özellikleri |
| 08 | `rem` veya `em` (px’e yaslanma) |
| 09–11 | padding, margin, border, boyut |
| 12 | `display` |
| 13 | bağlantı `:hover` |
| 14 | `list-style`, tablo (`border-collapse`, çift satır) |
| 15 | görsel sığdırma |
| 16–17 | `flex`, `gap`, `flex-wrap`, `justify-content`, `align-items` |

## Bitince kontrol

- Üstte logo solda, menü sağda mı?
- Kapak şeridi ortalanmış mı?
- Öne çıkan bölümde görsel ve metin yan yana mı?
- Kartlar dar pencerede alta iniyor mu?
- Tabloda çift satır ayrılıyor mu?
- Linke gelince görünüş değişiyor mu?

[← 17. gün](ders.md) · [İçindekiler](../README.md)
