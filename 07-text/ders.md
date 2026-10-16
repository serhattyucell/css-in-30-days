# 7. Gün — Metin (Text)

Bu gün, harfin ailesi dururken satırın hizasını ve süslü çizgiyi değiştirir. 6. günde punto ve kalınlık vardı. Bir başlığı kutunun ortasına almak başka bir özelliktir. `text-align` satırdaki harfleri sola, ortaya veya sağa iter. `text-decoration` alt çizgi, üst çizgi ve üzeri çizili satır ekler. Kutunun kendisini sayfanın ortasına çekmek bu özellik değildir. O, kenar boşluğunun işidir ve 9. günde gelir.

## Satır sola, ortaya veya sağa yaslanır

`text-align` öğenin içindeki satırları hizalar. Öğenin kutusunu sayfada taşımaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Hiza</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 18px;
      }

      h1 {
        color: #0e4d5c;
        text-align: center;
      }

      .tarih {
        text-align: right;
        color: #5e6670;
      }
    </style>
  </head>
  <body>
    <h1>Serhat'ın kent notları</h1>
    <p class="tarih">1 Ekim 2026</p>
    <p>İstanbul, İzmir, Trabzon ve Van aynı defterde durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Serhat'ın kent notları” satırı, sayfanın yatay ortasında durur. Başlık hâlâ kendi satırındadır ve yeşildir. “1 Ekim 2026” sağ kenara yaslı, soluk gri-mavidir. Son paragraf sola yaslıdır. `text-align` yazılmayan blok, sola yaslanır. Sağdaki tarih, başlığın ortalanmış kutusuyla aynı genişliktedir. İkisi de sayfa genişliğindedir. Ortada duran, başlığın harfleridir. Başlığın görünmez kutusu hâlâ soldan sağa bütün satırı kaplar.

`text-align: justify` her iki kenarı da doldurur. Son satır kısa kalabilir. Kısa bir kent notunda iki kenar yaslama, kelimeler arasında geniş boşluklar açar. Bu rehberdeki paragraflar solda kalır.

## Alt çizgi bağlantıda kalır

Bağlantı varsayılan olarak altı çizili ve mavidir. `text-decoration: none` çizgiyi kaldırır. `underline` geri getirir. Çizgi, rengin yanına konan ikinci işarettir. Yalnızca renk değişen bir bağlantı, renk görmeyen bir bakışta kaybolabilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Çizgi</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
      }

      a {
        color: #0c5c8a;
        text-decoration: underline;
      }

      nav a {
        text-decoration: none;
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <nav>
      <ul>
        <li><a href="#van">Van</a></li>
      </ul>
    </nav>
    <p>
      Ayrıntı
      <a href="https://example.com">Example Domain</a>
      sayfasındadır.
    </p>
    <h2 id="van">Van</h2>
  </body>
</html>
```

Tarayıcıda görünen:
Gezintideki “Van” koyu deniz yeşilidir ve altı çizili değildir. Paragraftaki “Example Domain” bağlantı mavisindedir ve altı çizilidir. İkisi de bağlantıdır. Çizgi, cümle içindeki bağlantıyı çevresindeki siyah kelimelerden ayırır. Gezintideki ad, zaten bir listenin içindedir. Çizgi orada kalkabilir. Fare ile üzerine gelince rengin değişmesi 13. günün konusudur. Bugün duran hâl, tıklamadan önceki görüntüdür.

`text-decoration: line-through` harfin üzerinden çizgi çeker. Eski bir notu silinmiş gibi göstermek için kullanılır. Okunacak bir başlığa konmaz.

## Harf aralığı ve biçim (Letter Spacing)

`letter-spacing` harflerin arasını açar veya daraltır. `text-transform` harfleri büyük veya küçüğe çevirir. Görünüş değişir. HTML’deki metin aynı kalır. Ekran okuyucu çoğu zaman kaynak metni okur. Başlık bağırıyorsa dönüşüm, bağırıyı büyütmemek için bütün sayfaya konmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Harf aralığı</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
      }

      h1 {
        color: #0e4d5c;
        letter-spacing: 0.12em;
        text-transform: uppercase;
        text-align: center;
      }

      .dar {
        letter-spacing: -0.04em;
      }
    </style>
  </head>
  <body>
    <h1>Van gölü</h1>
    <p class="dar">Harfler kaynağında küçük ve büyük karışık durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“VAN GÖLÜ” satırı sayfanın ortasında, koyu deniz yeşili ve harfleri seyrek durur. Kaynak `Van gölü` diye yazmıştır. `uppercase` görünen harfleri büyütür. `0.12em` aralığı, o satırın yazı boyutunun 0.12 katı kadar açar. “Harfler kaynağında küçük ve büyük karışık durur.” sola yaslıdır ve harfleri normalden biraz sıkışıktır. Eksi değer aralığı daraltır. Çok büyük eksi değer harfleri üst üste bindirir. Kent adında 0.12 em yeter. Paragrafta aralık sıfırda bırakılır. Uzun okuma metni seyrek harfle yorulur.

`text-transform: lowercase` hepsini küçültür. `capitalize` her kelimenin ilk harfini büyütür. Türkçe `i` harfi `uppercase` ile bazı tarayıcılarda `I` olur, `İ` olmaz. Belgenin dili `lang="tr"` ise güncel tarayıcılar `i` harfini `İ` yapar. Dil özelliği 2. günün HTML iskeletinde durduğu için bu sayfada korunur.

## Sık yapılan hata

`text-align: center` ile kutunun kendisinin sayfa ortasına geldiğini sanmaktır. Kısa bir kutu yine solda durur. İçindeki yazı ortalanır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yazı ortada</title>
    <style>
      h1 {
        color: #0e4d5c;
        text-align: center;
        width: 200px;
        background-color: #e7e2d8;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
  </body>
</html>
```

Tarayıcıda görünen:
Açık bej bir şerit, soldan başlar ve yaklaşık 200 piksel genişler. “Van” kelimesi o şeridin içinde ortalanır. Şerit sayfanın ortasına kaymaz. Sağ tarafta uzun bir kâğıt boşluğu kalır. `width` 10. günde, kutuyu ortaya alma 9. günde açılır. Bugün görülen sınır şudur: hiza, kutunun içinde kalır.

Doğru beklenti, yazının kutu içinde ortalanmasıdır. Kutu sola yapışıksa sonuç da soldadır. Geniş başlıkta kutu zaten sayfanın tamamıdır. “Van” o zaman gözle sayfanın ortasında durur. Daraltılmış kutuda fark ortaya çıkar.

İkinci hata, paragrafın içindeki bütün bağlantıların çizgisini `a { text-decoration: none; }` ile silmektir. “Example Domain” çevresindeki cümleyle aynı renkte ve çizgisiz kalırsa bağlantı olduğu güç okunur. Cümle içindeki bağlantıda çizgi kalır.

## Egzersizler

1. “Serhat'ın kent notları” sayfanın yatay ortasında dursun. Altındaki tarih sağa yaslansın ve soluk gri-mavi olsun. Gövde paragrafı solda kalsın.
2. Gezintideki bir bağlantının alt çizgisini kaldırın. Aynı sayfada paragrafın içindeki bağlantı mavi ve altı çizili kalsın.
3. Başlığa 200 piksel genişlik ve açık bej zemin verip `text-align: center` yazın. Kelime şeridin içinde ortalansın. Şerit solda kalsın. Sayfanın ortasına kaymasın.

[← Önceki gün](../06-fonts/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../08-units/ders.md)
