# Ödev — 17. güne kadar (5) · kısa

Alıştırma sayfasıdır; resmi Audi sitesi değildir. Grid, medya sorgusu, form, konum yok. Stil `<style>` içinde. Dosya: `audi-satis.html`.

## Konu

**Audi Studio** — dört araç kartlı kısa satış sayfası.

## Palet

| Rol | Hex |
| --- | --- |
| Zemin | `#0b0b0b` |
| Kart | `#161616` |
| Üst / footer | `#000000` |
| Metin | `#f2f2f2` |
| Gri | `#8f8f8f` |
| Kenarlık | `#3d3d3d` |
| Kırmızı | `#c4001a` |
| Tablo çift | `#1f1f1f` |

## Kart görselleri (gradient)

Her modelin üst kutusuna kendi sınıfını ver. Örnek CSS:

```css
.gorsel {
  height: 6rem;
}

.a1 {
  background: linear-gradient(145deg, #222, #555);
}

.a6 {
  background: linear-gradient(145deg, #1a1a1a, #666);
}

.q7 {
  background: linear-gradient(145deg, #181818, #5a2028);
}

.rs6 {
  background: linear-gradient(145deg, #111, #c4001a 150%);
}
```

## Ne yapacaksın (4 parça)

1. **Üst** — solda `#logo` (`AUDI`), sağda 3 link: Modeller, Fiyatlar, İletişim. Flex, `space-between`, `align-items: center`. `:hover`.

2. **Kapak** — kısa başlık + “Modelleri gör” linki. Flex ile ortala.

3. **4 araç kartı** — A1, A6, Q7, RS 6. Flex + `gap` + `flex-wrap`. Her kartta: renkli kutu, ad (sınıf), 1 cümle, fiyat, “İncele” (`:hover`).

4. **Fiyat tablosu + footer** — tablo: model / fiyat (`border-collapse`, çift satır farklı). Footer’da `AUDI Studio` ortada (flex ile ortala).

## Kontrol

Kartlar alta iniyor mu? Hover var mı? Palet koyu + kırmızı mı?

Önizleme: [onizleme.html](onizleme.html)

[← 17. gün](ders.md) · [İçindekiler](../README.md)
