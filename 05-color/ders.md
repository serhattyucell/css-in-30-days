# 5. Gün — Renk ve arka plan (Color and Background)

Bu gün, yazının rengini ve o yazının arkasındaki zemini ayırır. 4. günde renk hep `color` idi ve zemin beyaz kalıyordu. `color` harfin kendisidir. `background-color` harfin durduğu kutunun zeminidir. İkisi ayrı özelliktir. Biri yazılınca öteki değişmez.

## Yazı bir renk, zemin başka bir renk alır

Okunur bir sayfada koyu yazı, açık zeminin üstünde durur. Zemin bütün sayfaya verilecekse kural `body` seçicisine yazılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kâğıt ve mürekkep</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
      }

      h1 {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>Kent Karadeniz kıyısındadır. Kıyıdan çarşıya inilir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfanın boşlukları dahil zemini sıcak, açık bir kâğıt tonundadır. Saf beyaz değildir. “Trabzon” koyu deniz yeşili ve büyüktür. Paragraf koyu mürekkeptir. Paragrafın zemini ayrıca boyanmamıştır. Kâğıt rengi gövdeden görünür. Başlığın yeşili, gövdeye verilen mürekkep renginin üstüne yazılmıştır. Aynı öğede sonradan gelen daha özel bir kural, o öğenin yazı rengini değiştirir. Gövdenin mürekkebi paragrafta kalır. Başlık kendi `color` değerini kullanır.

`#f4f1ea` bir hex değerdir. Kare işaretinden sonra altı basamak gelir. İki basamak kırmızı, iki basamak yeşil, iki basamak mavidir. `teal` veya `gray` gibi renk adları da çalışır. Ad, seçilebilecek tonların kısa listesidir. Hex, listenin dışındaki tonu da kurar. Bu rehberdeki kâğıt, mürekkep ve deniz tonları hex ile yazılır. Böylece her dosyada aynı altı basamak aynı rengi verir.

## Zemin, yazının kutusunu boyar

`background-color` bir paragrafın kendi kutusuna verilirse yalnızca o kutunun arkası değişir. Sayfanın geri kalanı gövdenin renginde kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Şerit</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
      }

      .serit {
        background-color: #0e4d5c;
        color: #ffffff;
      }
    </style>
  </head>
  <body>
    <h1 class="serit">Van</h1>
    <p>Gölün kıyısı kâğıt zeminde durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” beyaz harflerle, koyu deniz yeşili bir şeridin içinde durur. Şerit, başlığın kendi satır kutusu kadardır. Sayfanın tamamı yeşil olmaz. Şeridin çevresindeki boşluk kâğıt rengindedir. Altındaki paragraf koyu mürekkeptir ve arkası kâğıttır. Yeşil zeminle beyaz yazı birbirinden ayrılır. Açık sarı yazı aynı yeşilin üstüne konsaydı satır zor okunurdu. Zemin koyulaşınca yazı açık renge çekilir. Yazı açık zemindeyse koyu kalır.

Renk körlüğü ve güneşli ekran düşünülünce anlam, yalnız renge bırakılmaz. “Bu satır önemli” demek için tek işaret soluk bir sarı olmamalıdır. Önem, HTML’de `<strong>` ile de durur. Sarı zemin ona ek olabilir. Bu sayfada şerit, bir başlığın adını taşır. Sarı bir uyarı kutusu kurulmaz.

## Saydamlık (Opacity)

`opacity` öğenin tamamını saydamlaştırır. Yazı, zemin ve çerçeve birlikte solar. `background-color` içindeki `rgb` ve alfa kanalı yalnızca zemini saydamlaştırır. Yazı koyu kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Saydam zemin</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      .tum {
        background-color: #0e4d5c;
        color: #ffffff;
        opacity: 0.45;
        padding: 1rem;
      }

      .zemin {
        background-color: rgb(14 77 92 / 0.45);
        color: #1e2430;
        padding: 1rem;
        margin-top: 1rem;
      }
    </style>
  </head>
  <body>
    <p class="tum">Van. Bu satırda yazı da zemin de solar.</p>
    <p class="zemin">İzmir. Bu satırda yalnız zemin solar.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Birinci şerit koyu deniz yeşilidir ama sayfa kâğıdı alttan görünür. “Van. Bu satırda yazı da zemin de solar.” beyazı da solar. Harfler grileşmiş gibi durur. İkinci şerit de yeşilin açık bir karışımıdır. “İzmir. Bu satırda yalnız zemin solar.” koyu mürekkeptir ve solmaz. İki şeridin arası kâğıttır. `0.45` yüzde 45 görünürlük demektir. `1` tam örtücüdür. `0` öğeyi görünmez yapar ama yerini tutar. `opacity: 0` ile `display: none` aynı sonuç değildir. İkincisi 12. günde yerini de kapatır.

`rgb(14 77 92 / 0.45)` kırmızı, yeşil ve mavi kanallarını 0 ile 255 arasında verir. `#0e4d5c` ile aynı üç kanaldır. On altılık `0e` ondalık 14, `4d` 77, `5c` 92 eder. Alfa, sondaki `0.45` değeridir. Eski biçim `rgba(14, 77, 92, 0.45)` de aynı rengi üretir. Bu rehber boşluklu yeni biçimi kullanır.

## Sık yapılan hata

`color` ile zemini boyamaya çalışmak, yalnızca harfleri değiştirir. Kutunun arkası eski renginde kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yanlış zemin</title>
    <style>
      body {
        color: #f4f1ea;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Kâğıt rengi harfe verilmiş.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Zemin beyaz veya tarayıcının varsayılan açık rengidir. “İzmir” ve paragraf, açık kâğıt tonunda harflerle durur. Açık harf, açık zeminin üzerinde solar. Sayfa boşalmış gibi görünebilir. `color` zemini boyamaz.

Doğru belgede zemin ve yazı ayrı özelliklerdir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ayrı renkler</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
      }

      h1 {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Kâğıt zeminde, koyu harfle durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Zemin açık kâğıttır. “İzmir” koyu deniz yeşilidir. Paragraf koyu mürekkeptir. Harfler zeminden ayrılır.

İkinci hata, altı basamağı eksik yazmaktır. `#0e4d` dört basamaklı bir renk değildir. Üç basamaklı kısa biçim `#0e4` gibi ayrı bir kuraldadır. Bu rehber altı basamak kullanır. Eksik değer, kuralın o bildirimini düşürebilir. Başlık siyaha döner.

## Egzersizler

1. Gövdenin zeminini açık kâğıt, yazısını koyu mürekkep yapın. “Trabzon” başlığı koyu deniz yeşili kalsın. Paragraf mürekkep renginde, kâğıdın üstünde okunsun.
2. Yalnızca başlığa koyu deniz yeşili zemin ve beyaz yazı verin. Sayfanın geri kalanı kâğıt kalsın. Beyaz yazı yeşil şeridin içinde dursun.
3. Zemini `color` ile boyamayı deneyin. Zemin açık kalıp harfler solar. Sonra `background-color` kullanın. Zemin kâğıt, harfler koyu olsun.

[← Önceki gün](../04-class-id/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../06-fonts/ders.md)
