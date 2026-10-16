# 18. Gün — Izgara (Grid)

Bu gün, satırı ve sütunu birlikte kurar. Esnek kutu bir eksende dizer, sığmayınca kaydırır. Izgara, kaç sütun olacağını baştan söyler. `display: grid` üst öğeye yazılır. `grid-template-columns` sütunların payını kurar. `1fr` kalan genişliğin bir payıdır. `gap` satır ve sütun aralığını birlikte verebilir. `grid-column: span 2` bir çocuğun iki sütun kaplamasını sağlar.

## İki eşit sütun

`1fr 1fr` iki sütunu eşit böler. Dört kart, iki satıra kendiliğinden iner. Satır sayısı ayrıca yazılmasa da çocuklar alt alta dolar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki sütun</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      ul {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1rem;
        list-style: none;
        padding: 0;
        margin: 0;
      }

      li {
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        border-radius: 0.5rem;
        padding: 1rem;
      }
    </style>
  </head>
  <body>
    <h1>Dört kent</h1>
    <ul>
      <li>İstanbul, Boğaz</li>
      <li>İzmir, körfez</li>
      <li>Trabzon, kıyı</li>
      <li>Van, göl</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Başlığın altında iki sütun vardır. Solda İstanbul, sağda İzmir aynı hizadadır. Alt satırda solda Trabzon, sağda Van durur. Dört kutu beyaz, yeşil çerçeveli ve yuvarlak köşelidir. Sütunların arasında ve satırların arasında 1 rem kâğıt vardır. Madde işareti yoktur. Pencere daralsa da bu belgede hep iki sütun kalır. Dar pencerede kartlar incelir. Tek sütuna inmek 19. günün medya sorgusudur. Izgara, sütun sayısını kendiliğinden bir yapmaz.

`repeat(2, 1fr)` ile `1fr 1fr` aynı işi görür. Üç sütun `repeat(3, 1fr)` olur. Dört kart üç sütuna konursa son satırda bir kart kalır ve o kart yalnızca bir pay genişler. Satırın tamamına yayılmaz. Yayılması için `span` gerekir.

## Bir çocuk iki sütun kaplar

`grid-column: span 2` çocuğu bulunduğu yerden itibaren iki sütun genişletir. Satırdaki başka bir çocukla çakışırsa ızgara onu sonraki boşluğa kaydırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Geniş kart</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      section {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1rem;
      }

      article {
        background-color: #ffffff;
        border: 2px solid #cfc8bc;
        padding: 1rem;
      }

      .genis {
        grid-column: span 2;
        border-color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Notun sırası</h1>
    <section>
      <article class="genis">
        <h2>Okuma sırası</h2>
        <p>İstanbul, Trabzon, Van, İzmir. Bu bir karayolu değildir.</p>
      </article>
      <article>
        <h2>İstanbul</h2>
        <p>Boğaz.</p>
      </article>
      <article>
        <h2>Van</h2>
        <p>Göl.</p>
      </article>
    </section>
  </body>
</html>
```

Tarayıcıda görünen:
“Okuma sırası” kartı iki sütunun birden üzerinde durur. Çerçevesi yeşildir. Altında iki dar kart yan yanadır. Solda İstanbul, sağda Van, açık gri çerçevelidir. Geniş kart kendi satırını tek başına tutar. Alttaki iki kart bir paydan fazla yer kapmaz. Başlıklar kartın içinde, gövdeden küçük düzeydedir. Sayfanın `h1` değeri en büyüktür.

Izgara da esnek kutu gibi üst öğeye yazılır. `display: grid` bir `article` üzerindeyse kardeş kartlar ızgaraya girmez. Izgara, kartların kabıdır.

## Kendiliğinden sığan sütun (Auto-fit)

`repeat(auto-fit, minmax(12rem, 1fr))` sütun sayısını pencereye bırakır. Her sütun en az 12 rem, en çok bir paydır. Sığmayan kart alt satıra iner. Medya sorgusu yazmadan daralan bir ızgara kurulur. Sorgu, renk veya yön değişecekse yine kullanılır. Yalnızca sütun sayısı değişecekse `minmax` yeter.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sığan ızgara</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      ul {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(12rem, 1fr));
        gap: 1rem;
        list-style: none;
        padding: 0;
      }

      li {
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        border-radius: 0.5rem;
        padding: 1rem;
      }
    </style>
  </head>
  <body>
    <h1>Dört kart</h1>
    <ul>
      <li>İstanbul</li>
      <li>İzmir</li>
      <li>Trabzon</li>
      <li>Van</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Pencere genişken dört beyaz kart yan yana sığabilir. Her biri en az 12 remdir. Aralık 1 remdir. Pencere daralınca önce üç, sonra iki, en sonda tek sütun kalır. Kartlar 12 remden ince bir şeride ezilmez. Alt satıra inen kart, satırdaki boş payı `1fr` ile doldurur. Tek kart kalınca satırın genişliğini alır. `auto-fill` boş sütunları da yerinde tutabilir. `auto-fit` boş sütunları kapatıp dolu kartları yayar. Dört kentin dördü de dolu olduğu için ikisi bu sayfada benzer görünür. Boş bir beşinci iz bırakmak istenmiyorsa `auto-fit` kullanılır.

## Sık yapılan hata

Dört öğeyi `1fr 1fr` sanıp esnek kutunun kaydırmasına güvenmek, dar pencerede iki sütunu ezerek tutar. Izgara satır kaydırmaz. Sütun sayısı sabittir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ezilen sütun</title>
    <style>
      ul {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1rem;
        padding: 0;
        list-style: none;
      }
    </style>
  </head>
  <body>
    <ul>
      <li>İstanbul Boğaz kıyısı notu uzundur</li>
      <li>Van Gölü kıyısı notu da uzundur</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Pencere çok daralınca iki sütun yan yana kalır. Kelimeler dar kutunun içinde kırılır. Üçüncü bir satıra, tek sütun halinde inmezler. Taşma, kelime uzun ve bölünemezse yatay kaydırma da çıkarabilir.

Doğru kullanım, ızgaranın sütun sayısını bilerek tutmaktır. Dar ekranda tek sütun, sonraki günün sorgusuyla yazılır. Bugün geniş pencerede iki sütun eşit payla durur. Ezilme, dar pencerede bu kuralın sınırı olarak görülür.

İkinci hata, `span 2` ile üç sütunlu bir ızgarada dördüncü bir pay beklemektir. İki sütunluk ızgarada `span 2` satırın tamamıdır. `span 3` üçüncü sütun olmadığı için taşabilir veya satırı zorlar. Sayı, gerçekten var olan sütunu geçmez.

## Egzersizler

1. Dört kent iki eşit sütunda, iki satır olsun. Aralık 1 rem, kartlar beyaz ve yeşil çerçeveli görünsün. Pencere genişken İstanbul ile İzmir aynı satırda dursun.
2. Üstte iki sütun kaplayan bir “Okuma sırası” kartı, altında İstanbul ve Van yan yana görünsün. Geniş kartın çerçevesi yeşil, dar kartların çerçevesi açık gri olsun.
3. Izgara kuralını çocukların üzerine alın. Sütunlar kaybolsun. Kuralı yeniden kabın üzerine koyun. İki sütun geri gelsin.

[← Önceki gün](../17-flex-alignment/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../19-media/ders.md)
