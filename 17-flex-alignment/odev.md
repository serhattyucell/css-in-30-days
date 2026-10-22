# Ödev — 17. güne kadar

Bu ödev, 1–17. günlerdeki kuralları tek sayfada kullanır. Grid, medya sorgusu, form ve konum yoktur. Çözüm dersin içinde yoktur.

Dosya adı: `dort-kent.html`  
Stil, belgenin başındaki `<style>` içinde dursun.

## Konu

Dört kent: İstanbul, İzmir, Trabzon, Van. Sayfa Serhat’ın kısa bir tanıtım sitesidir.

## Sayfada ne olacak

1. **Üst şerit (header)**  
   Solda site adı, sağda menü. Menü maddeleri yatay dursun. Başlık ve menü şeridin dikey ortasında olsun. Boşluk `space-between` ile dağılsın.

2. **Giriş**  
   Kısa bir başlık ve bir paragraf. Yazı tipi, renk, satır aralığı ve hizalama seçilsin.

3. **Dört kart**  
   Her kart bir kent olsun. Kartlar flex satırında dursun, aralarında `gap` olsun, sığmayan alta insin. Her kartta:
   - bir görsel (`max-width: 100%`, `height: auto`)
   - kent adı (sınıf veya kimlik ile seçilsin)
   - kısa metin
   - “Detay” bağlantısı (`:hover` ile renk veya alt çizgi değişsin)
   - kenarlık, iç boşluk, dış boşluk

4. **Durak listesi**  
   Dört kentin adını madde işaretsiz bir listede göster. Liste flex ile yatay veya dikey dizilsin.

5. **Küçük tablo**  
   İki sütun: kent ve kısa not. Kenarlık birleşsin, çift satırlar farklı zeminde olsun.

6. **Alt bilgi (footer)**  
   Ortada tek satır metin. Flex ile yatay ve dikey ortala.

## Kullanılması gerekenler

| Gün | Ne kullanılsın |
| --- | --- |
| 02–04 | seçici, sınıf, kimlik |
| 05 | renk, arka plan |
| 06–07 | yazı tipi, metin özellikleri |
| 08 | `rem` veya `em` |
| 09–11 | padding, margin, border, boyut |
| 12 | `display` |
| 13 | bağlantı `:hover` (isteğe bağlı `:visited`) |
| 14 | liste (`list-style`) ve tablo (`border-collapse`, çift satır) |
| 15 | görsel sığdırma |
| 16–17 | `flex`, `gap`, `flex-wrap`, `justify-content`, `align-items` |

## Bitince kontrol

- Menü sağda, başlık solda mı?
- Kartlar dar pencerede alta iniyor mu?
- Görseller kutuyu taşırıyor mu?
- Tablo çizgileri tek hatta mı?
- Linke gelince görünüş değişiyor mu?

[← 17. gün](ders.md) · [İçindekiler](../README.md)
