# 24. Gün — Küçük sayfa: hakkında (About)

Bu gün, notu kimin tuttuğunu anlatan sayfaya görünüş verir. Yeni bir özellik yoktur. Üst şerit, gezinti, dar sütun, liste, figür ve alt çizgi önceki günlerin kurallarıdır. İş, bu kuralları “hakkında” sayfasında bir arada tutmaktır.

## Kapak sayfası

Belge `hakkinda.html` adıyla kaydedilir. `serhat.jpg` aynı klasördeyse fotoğraf 24 rem içinde, kendi oranında durur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Hakkında</title>
    <style>
      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1.05rem;
        line-height: 1.6;
      }

      header {
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
      }

      h1 {
        margin: 0;
        font-size: 1.8rem;
      }

      nav ul {
        display: flex;
        gap: 1rem;
        list-style: none;
        margin: 0.8rem 0 0;
        padding: 0;
      }

      nav a {
        color: #ffffff;
        text-decoration: none;
      }

      nav a:hover,
      nav a:focus {
        text-decoration: underline;
        outline: 3px solid #c47b00;
      }

      main {
        max-width: 40rem;
        margin: 0 auto;
        padding: 1.5rem 1rem 3rem;
      }

      h2 {
        color: #0e4d5c;
        font-size: 1.3rem;
        margin: 2rem 0 0.4rem;
      }

      ul {
        padding-left: 1.2rem;
      }

      figure {
        margin: 1rem 0;
        max-width: 24rem;
      }

      img {
        max-width: 100%;
        height: auto;
        border-radius: 0.5rem;
        background-color: #e7e2d8;
      }

      figcaption {
        color: #5e6670;
        font-size: 0.9rem;
      }

      blockquote {
        margin: 1rem 0;
        padding: 0.5rem 1rem;
        border-left: 4px solid #0e4d5c;
        background-color: #ffffff;
      }

      footer {
        padding: 1rem;
        color: #5e6670;
      }

      @media (max-width: 36rem) {
        nav ul {
          flex-direction: column;
          gap: 0.4rem;
        }
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Hakkında</h1>
      <nav>
        <ul>
          <li><a href="#amac">Amaç</a></li>
          <li><a href="#kentler">Dört kent</a></li>
          <li><a href="#yazar">Notu yazan</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <h2 id="amac">Amaç</h2>
      <p>Bu sayfa bir seyahat acentesi değildir. Serhat’ın kent notlarının kapağıdır.</p>
      <h2 id="kentler">Dört kent</h2>
      <ul>
        <li>İstanbul, Boğaz’ın iki yakasında</li>
        <li>İzmir, Ege kıyısında</li>
        <li>Trabzon, Karadeniz kıyısında</li>
        <li>Van, gölün kıyısında</li>
      </ul>
      <h2 id="yazar">Notu yazan</h2>
      <figure>
        <img src="serhat.jpg" alt="Serhat’ın not defterinin kapağı" />
        <figcaption>Not defteri. Dosya yoksa alternatif metin kutuda kalır.</figcaption>
      </figure>
      <blockquote>
        <p>Dört kent aynı defterde durur. Defter bir güzergâh değildir.</p>
      </blockquote>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Üstte koyu deniz yeşili bir şerit vardır. “Hakkında” beyaz ve büyüktür. Altında Amaç, Dört kent ve Notu yazan beyaz, çizgisiz ve yatay durur. Pencere 36 rem ve altındaysa üç ad alt alta iner. Birine gelince alt çizgi ve amber çerçeve belirir. Tıklanınca sayfa o başlığa kayar.

Gövde ortada, en çok 40 remdir. Bölüm başlıkları yeşil ve gövdeden büyüktür. Dört kent madde işaretli, soldan içeri bir liste olarak durur. Numara yoktur. Fotoğraf varsa en çok 24 rem ve yuvarlak köşelidir. Yoksa bej zemin, kırık simge ve “Serhat’ın not defterinin kapağı” görünür. Alt yazı soluk ve biraz küçüktür. Alıntının solunda 4 piksel yeşil çizgi, arkası beyazdır. Diğer üç kenarda çizgi yoktur. En altta “Notu yazan: Serhat” soluk gri-mavidir. Sayfa bir acente afişi gibi büyümez. Bir kapak sütunudur.

## Fotoğrafın oranı (Aspect Ratio)

Kapak fotoğrafı `aspect-ratio: 3 / 2` ile yerini önceden tutar. Dosya yokken bej kutu da aynı oranda durur. Metin, resim gelince aşağı zıplamaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kapak oranı</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      figure {
        max-width: 24rem;
        margin: 0;
      }

      img {
        width: 100%;
        height: auto;
        aspect-ratio: 3 / 2;
        object-fit: cover;
        background-color: #e7e2d8;
        border-radius: 0.5rem;
      }

      figcaption {
        color: #5e6670;
        font-size: 0.9rem;
      }
    </style>
  </head>
  <body>
    <h1>Not defteri</h1>
    <figure>
      <img src="serhat.jpg" alt="Serhat’ın not defterinin kapağı" />
      <figcaption>Dosya yoksa kutu 3:2 oranında kalır.</figcaption>
    </figure>
  </body>
</html>
```

Tarayıcıda görünen:
Görsel en çok 24 remdir. Yüksekliği, genişliğin üçte ikisi kadardır. Dosya varsa fotoğraf bu dikdörtgeni doldurur, taşan kenar kesilir, oran bozulmaz. Dosya yoksa bej kutu ve “Serhat’ın not defterinin kapağı” aynı yerde durur. Alt yazı soluk, kutunun altındadır. Pencere daralınca kutu daralır, 3’e 2 oranı kalır.

## Sık yapılan hata

Şeritteki beyaz bağlantıyı, gövdenin mavi bağlantı kuralıyla ezmektir. Üstteki adlar yeşil zeminde mavi ve altı çizili kalırsa şerit dağılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ezilen şerit</title>
    <style>
      a {
        color: #0c5c8a;
      }

      header {
        background-color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <header>
      <a href="#amac">Amaç</a>
    </header>
  </body>
</html>
```

Tarayıcıda görünen:
“Amaç” mavi ve altı çizili, yeşil şeridin üstündedir. Beyaz değildir. Genel `a` kuralı, şerit için ayrı bir renk yazılmadığı sürece geçerlidir.

Doğru belgede şerit bağlantısı ayrıca beyazdır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Beyaz şerit bağlantısı</title>
    <style>
      header {
        background-color: #0e4d5c;
        padding: 1rem;
      }

      header a {
        color: #ffffff;
        text-decoration: none;
      }
    </style>
  </head>
  <body>
    <header>
      <a href="#amac">Amaç</a>
    </header>
  </body>
</html>
```

Tarayıcıda görünen:
“Amaç” beyazdır ve altı çizili değildir. Yeşil zeminden ayrılır.

## Egzersizler

1. `hakkinda.html` dosyasında yeşil şerit, beyaz “Hakkında” ve yatay üç bağlantı görünsün. Dar pencerede bağlantılar alt alta insin.
2. Dört kent maddeli listede, fotoğraf en çok 24 rem ve alt yazı soluk olsun. Dosya yokken alternatif metin görünsün. Köşe yuvarlak kalsın.
3. Alıntının yalnızca sol kenarı yeşil olsun. Genel `a` rengi şeritteki beyazı boyamasın. “Amaç” beyaz kalsın.

[← Önceki gün](../23-readable/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../25-stop-list/ders.md)
