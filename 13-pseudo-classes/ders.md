# 13. Gün — Bağlantı durumları (Pseudo-classes)

Bu gün, bir bağlantının durduğu hâle göre görünüşünü değiştirir. 7. günde çizgi ve renk sabitti. Fare üzerine gelince, bağlantı daha önce açılmışsa veya klavye odağı oradaysa başka bir kural devreye girebilir. `a:link` henüz açılmamış bağlantıdır. `a:visited` açılmış olandır. `a:hover` göstergeç üzerindedir. `a:focus` klavye veya tıklama odağı oradadır. `a:active` tıklamanın basılı anıdır.

## Sıra, hangi rengin kalacağını belirler

Aynı özelliği birkaç durum birden değiştiriyorsa kaynakta alttaki kural, eşit özgüllükte üste yazar. Bağlantı durumlarının okunaklı sırası şudur: link, visited, hover, active. Odak, ayrı bir kural olarak en sonda durur. Böylece üzerine gelmek, odak çerçevesini silmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Durumlar</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1.1rem;
        color: #1e2430;
      }

      a:link {
        color: #0c5c8a;
        text-decoration: underline;
      }

      a:visited {
        color: #5c4575;
        text-decoration: underline;
      }

      a:hover {
        background-color: #e7e2d8;
      }

      a:active {
        color: #0e4d5c;
      }

      a:focus {
        outline: 3px solid #c47b00;
        outline-offset: 2px;
      }
    </style>
  </head>
  <body>
    <h1>Notlar</h1>
    <p><a href="#van">Van bölümüne in</a></p>
    <p><a href="https://example.com">Example Domain</a></p>
    <h2 id="van">Van</h2>
    <p>Göl geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
İki bağlantı da altı çizilidir. Henüz açılmamışlarsa renkleri bağlantı mavisidir. Example Domain daha önce bu tarayıcıda açıldıysa o bağlantı morumsu durur. Çizgi mor olanda da kalır. Renk tek işaret değildir. “Van bölümüne in” bağlantısının üzerine gelince arkası açık bej olur. Çizgi durur. Fare çekilince bej kaybolur. Bağlantıya Sekme tuşuyla gelinince çevresinde amber bir çerçeve belirir. Çerçeve ile yazı arasında yaklaşık 2 piksel açık yer vardır. Mouse ile tıklamanın basılı anında renk bir an koyu deniz yeşiline dönebilir. Sayfa içi “Van bölümüne in” tıklanınca sayfa Van başlığına kayar. Example Domain tıklanınca o sitenin sayfası açılır.

`outline`, kutunun dışına çizilen bir hattır. Kenarlık gibi yer kaplamaz ve komşu satırı itmez. Odak çerçevesini `outline: none` ile silmek, klavyeyle gezen kişiyi yerini göremez bırakır. Amber çerçeve, tarayıcının kendi çerçevesinin yerine konmuşsa odak kaybolmaz.

## Gezinti ve cümle aynı durumu paylaşmak zorunda değildir

`nav a` seçicisi, durum seçicisiyle birleşir. Gezintide bej zemin, cümlede ise yalnızca alt çizgi kalabilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki tür bağlantı</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      nav a {
        text-decoration: none;
        color: #0e4d5c;
        padding: 0.3rem 0.6rem;
      }

      nav a:hover,
      nav a:focus {
        background-color: #0e4d5c;
        color: #ffffff;
      }

      p a:link,
      p a:visited {
        color: #0c5c8a;
        text-decoration: underline;
      }
    </style>
  </head>
  <body>
    <nav>
      <ul>
        <li><a href="#izmir">İzmir</a></li>
        <li><a href="#trabzon">Trabzon</a></li>
      </ul>
    </nav>
    <p>
      Kıyı notu
      <a href="https://example.com">Example Domain</a>
      adresinde değildir.
    </p>
    <h2 id="izmir">İzmir</h2>
    <h2 id="trabzon">Trabzon</h2>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” ve “Trabzon” listede koyu deniz yeşili ve çizgisiz durur. Birinin üzerine gelince veya Sekme ile odaklanınca zemin yeşil, yazı beyaz olur. Paragraftaki “Example Domain” mavi ve altı çizili kalır. Onun üzerine gelince yeşil bir şerit oluşmaz. İki grup ayrı seçicidedir.

## İlk ve son çocuk (First and Last Child)

`:first-child` ebeveynin ilk çocuğunu seçer. `:last-child` son çocuğu seçer. Öğe türü de eklenebilir. `li:last-child` listenin son maddesidir. İlk çocuk bir başlıksa `p:first-child` hiçbir paragrafı seçmez. Paragraf ilk çocuk değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İlk ve son</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      ul {
        list-style: none;
        padding: 0;
        margin: 0;
      }

      li {
        padding: 0.5rem 0;
        border-bottom: 1px solid #cfc8bc;
      }

      li:first-child {
        color: #0e4d5c;
        font-weight: 700;
      }

      li:last-child {
        border-bottom: 0;
      }
    </style>
  </head>
  <body>
    <h1>Kentler</h1>
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
“İstanbul” koyu deniz yeşili ve kalındır. Diğer üç kent koyu mürekkeptir. Her satırın altında açık gri bir çizgi vardır. “Van” satırının altında çizgi yoktur. Son çocuğun alt kenarlığı sıfırdır. Liste işareti yoktur ve soldan başlar. Başlık listenin ilk çocuğu değildir. `li:first-child` başlığı boyamaz.

`:first-of-type` aynı türün ilkini seçer. Bir `main` içinde önce bir başlık, sonra paragraflar varsa `p:first-of-type` ilk paragrafı alır. `p:first-child` almaz. Tür şartı, listenin gerçekten ilk öğesi olmayan bir paragrafı boyamamak için burada `li` ile birlikte yazılmıştır.

## Sık yapılan hata

`:hover` kuralını `:link` kuralından önce yazmak, üzerine gelince rengin değişmemesine yol açabilir. Özellikle `:visited` alttaysa ve rengi yeniden kuruyorsa hover etkisiz kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kaybolan üzerine gelme</title>
    <style>
      a:hover {
        color: #c47b00;
      }

      a:link,
      a:visited {
        color: #0c5c8a;
      }
    </style>
  </head>
  <body>
    <p><a href="#van">Van</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” mavidir ve altı çizilidir. Fare üzerine gelince amber olmaz. Alttaki kural hem açılmamış hem açılmış bağlantının rengini maviye sabitler. Hover kuralı daha yukarıda kaldığı için aynı özellikte yenilir.

Doğru sırada hover, link ve visited kurallarının altındadır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Duran üzerine gelme</title>
    <style>
      a:link,
      a:visited {
        color: #0c5c8a;
        text-decoration: underline;
      }

      a:hover,
      a:focus {
        color: #0e4d5c;
        outline: 3px solid #c47b00;
      }
    </style>
  </head>
  <body>
    <p><a href="#van">Van</a></p>
    <h2 id="van">Van</h2>
  </body>
</html>
```

Tarayıcıda görünen:
Bağlantı mavi ve altı çizilidir. Üzerine gelince yazı koyu deniz yeşili olur ve amber bir odak çerçevesi belirir. Çerçeve, yalnız renge güvenmeden üzerine gelindiğini de gösterir.

## Egzersizler

1. Açılmamış bağlantı mavi ve altı çizili, daha önce açılmış bağlantı mor ve altı çizili olsun. Example Domain bu tarayıcıda daha önce açıldıysa mor göründüğünü kontrol edin.
2. “Van bölümüne in” üzerine gelince arkası açık bej olsun. Sekme tuşuyla gelince amber bir `outline` görünsün. Çerçeveyi silmeyin.
3. Hover kuralını link kuralının üstüne alın. Renk değişmesin. Hover kuralını alta indirin. Üzerine gelince renk değişsin.

[← Önceki gün](../12-display/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../14-lists-tables/ders.md)
