# 25. Gün — Küçük sayfa: durak listesi (Stop List)

Bu gün, okuma sırasını numaralı bir liste olarak biçimlendirir. 24. gündeki kapak sırasızdı. Burada numara kalır, iç liste daireli kalır ve her durak bir satır kutusu olur. Yeni bir özellik yoktur. Esnek gezinti, kenarlık, iç boşluk ve dar pencere sorgusu durakların okunması için kullanılır.

## Numara durağın kutusuyla birlikte durur

Belge `duraklar.html` adıyla kaydedilir. Dış liste numaralıdır. İç liste, durağın içinde, soldan biraz daha içeride daire alır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Durak listesi</title>
    <style>
      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        line-height: 1.5;
      }

      header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 1rem;
        padding: 1rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }

      h1 {
        margin: 0;
        font-size: 1.5rem;
      }

      nav ul {
        display: flex;
        gap: 1rem;
        list-style: none;
        margin: 0;
        padding: 0;
      }

      header a {
        color: #ffffff;
        text-decoration: none;
      }

      header a:focus {
        outline: 3px solid #c47b00;
      }

      main {
        max-width: 40rem;
        margin: 0 auto;
        padding: 1.5rem 1rem 3rem;
      }

      ol {
        margin: 0;
        padding-left: 1.4rem;
      }

      ol > li {
        background-color: #ffffff;
        border: 2px solid #cfc8bc;
        border-radius: 0.5rem;
        padding: 0.8rem 1rem 0.8rem 0.4rem;
        margin-bottom: 1rem;
      }

      ol ul {
        margin: 0.4rem 0 0;
      }

      @media (max-width: 36rem) {
        header {
          flex-direction: column;
          align-items: flex-start;
        }
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Durak listesi</h1>
      <nav>
        <ul>
          <li><a href="#istanbul">İstanbul</a></li>
          <li><a href="#van">Van</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <p>Okuma sırası bir karayolu değildir.</p>
      <ol>
        <li id="istanbul">
          İstanbul
          <ul>
            <li>Galata Kulesi</li>
            <li>Kapalıçarşı</li>
          </ul>
        </li>
        <li>
          Trabzon
          <ul>
            <li>Kıyı</li>
            <li>Çarşı</li>
          </ul>
        </li>
        <li id="van">
          Van
          <ul>
            <li>Van Gölü</li>
            <li>Van Kalesi</li>
          </ul>
        </li>
        <li>
          İzmir
          <ul>
            <li>Saat Kulesi</li>
            <li>Kordon</li>
          </ul>
        </li>
      </ol>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şeritte “Durak listesi” solda, İstanbul ve Van bağlantıları sağda beyaz durur. Dar pencerede başlık üstte, bağlantılar altta soldadır. Gövde ortada, en çok 40 remdir. “Okuma sırası bir karayolu değildir.” sıradan bir paragraftır.

Dört beyaz kart alt alta durur. Solda 1, 2, 3, 4 numaraları vardır. Numaralar kartın dışında kaybolmaz. Kartın açık gri çerçevesi vardır ve köşeleri yuvarlaktır. Kartların arasında 1 rem kâğıt görünür. İstanbul’un altında daireli “Galata Kulesi” ve “Kapalıçarşı” daha içeridedir. Bu alt maddeler 5 ve 6 olmaz. Van’ın altında “Van Gölü” ve “Van Kalesi” yine daireyledir. Şeritteki “Van” tıklanınca sayfa üçüncü karta kayar. Adresin sonunda `#van` durur.

`ol > li` yalnız dış maddeleri kart yapar. İç `ul` öğeleri bu kenarlığı almaz. İç liste düz satır olarak kartın içinde kalır.

## Son kartın boşluğu (Last Child)

Kartlar `margin-bottom` ile ayrılır. Son kartın altında aynı boşluk, sayfa sonuna fazladan kâğıt ekler. `li:last-child` o alt boşluğu sıfırlar. İç listedeki son daireli madde bu seçiciye karışmasın diye seçici `ol > li:last-child` olur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Son durak</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      ol {
        max-width: 24rem;
        padding-left: 1.4rem;
      }

      ol > li {
        background-color: #ffffff;
        border: 2px solid #cfc8bc;
        border-radius: 0.5rem;
        padding: 0.6rem;
        margin-bottom: 1rem;
      }

      ol > li:last-child {
        margin-bottom: 0;
      }
    </style>
  </head>
  <body>
    <h1>İki durak</h1>
    <ol>
      <li>İstanbul</li>
      <li>Van</li>
    </ol>
    <p>Bu cümle son kartın hemen altındadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
İki beyaz kartın arasında yaklaşık 1 rem kâğıt vardır. “Van” kartının altında aynı 1 rem boşluk yoktur. “Bu cümle son kartın hemen altındadır.” kartın bitimine yakın durur. Numaralar 1 ve 2 olarak kalır. İç liste bu kısa örnekte yoktur. Tam durak sayfasında iç maddelerin sonuncusu da `li:last-child` olabilirdi. `ol > li:last-child` yalnız dış listenin son durağını, yani İzmir kartını seçer. Galata Kulesi o kurala girmez.

## Sık yapılan hata

`li` seçicisini daraltmadan boyamak, iç maddeleri de ayrı kart yapar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İç kart</title>
    <style>
      li {
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        margin-bottom: 1rem;
      }
    </style>
  </head>
  <body>
    <ol>
      <li>
        İstanbul
        <ul>
          <li>Galata Kulesi</li>
        </ul>
      </li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
Hem “İstanbul” hem “Galata Kulesi” ayrı beyaz kartlardır. Kule, durağın içindeki satır değil, ikinci bir durak gibi çerçevelenir. Numara ile daire iç içe kutulara bölünür.

Doğru seçici yalnız dış maddedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dış kart</title>
    <style>
      ol > li {
        background-color: #ffffff;
        border: 2px solid #cfc8bc;
        border-radius: 0.5rem;
        padding: 0.8rem;
        margin-bottom: 1rem;
      }
    </style>
  </head>
  <body>
    <ol>
      <li>
        İstanbul
        <ul>
          <li>Galata Kulesi</li>
        </ul>
      </li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
Tek beyaz kart “1. İstanbul” maddesidir. “Galata Kulesi” o kartın içinde, daireyle, kendi çerçevesi olmadan durur.

## Egzersizler

1. `duraklar.html` dosyasında yeşil şerit ve ortaya alınmış 40 remlik bir sütun olsun. Dört durak numaralı beyaz kartlar olarak alt alta dursun.
2. İstanbul’un altındaki Galata Kulesi ve Kapalıçarşı daireli, kartın içinde ve çerçevesiz görünsün. 5. numara almasın. Şeritteki Van bağlantısı üçüncü karta indirsin.
3. `ol > li` yerine `li` yazın. İç maddeler de kart olsun. Seçiciyi daraltın. Yalnızca dört durak çerçeveli kalsın. Dar pencerede şerit alt alta insin.

[← Önceki gün](../24-about/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../26-contact-form/ders.md)
