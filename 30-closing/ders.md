# 30. Gün — Kapanış sayfası: yazı tipi (Typography), renk (Color), kutu (Box), bağlantı (Link), görsel (Image), tablo (Table) ve form

Bu gün, otuzuncu sayfada yazı tipini, rengi, kutuyu, bağlantıyı, görseli, tabloyu ve formu bir kez daha aynı belgede toplar. Yeni bir özellik yoktur. 29. gündeki site dört dosyayı bir stile bağladı. Bu sayfa tek dosyadır. Yedi parçanın her biri ekranda ayrı ayrı durur. Parça eksikse sayfa kapanış sayfası olmaz.

## Yedi parça aynı sütunda

Yazı tipi aileyi ve puntoyu kurar. Renk, kâğıdı mürekkepten ayırır. Kutu, kartın iç boşluğunu ve çerçevesini kurar. Bağlantı, başka sayfaya giden çizili sözdür. Görsel, klasördeki dosyaya sığar. Tablo, kenti plakayla hizalar. Form, bir kenti adres çubuğuna yazar.

Belge `kapanis.html` adıyla kaydedilir. `kapanis.jpg` aynı klasördeyse fotoğraf 20 rem içinde durur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kapanış</title>
    <style>
      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Georgia, "Times New Roman", serif;
        font-size: 1.05rem;
        line-height: 1.6;
      }

      header {
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
        font-family: Arial, Helvetica, sans-serif;
      }

      h1 {
        margin: 0;
        font-size: 2rem;
      }

      main {
        max-width: 40rem;
        margin: 0 auto;
        padding: 1.5rem 1rem 3rem;
      }

      h2 {
        color: #0e4d5c;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1.3rem;
      }

      .kart {
        background-color: #ffffff;
        border: 2px solid #cfc8bc;
        border-radius: 0.5rem;
        padding: 1rem;
        margin: 0 0 1rem;
      }

      a:link,
      a:visited {
        color: #0c5c8a;
        text-decoration: underline;
      }

      a:hover,
      a:focus {
        outline: 3px solid #c47b00;
        outline-offset: 2px;
      }

      img {
        max-width: 100%;
        height: auto;
        border-radius: 0.5rem;
        background-color: #e7e2d8;
      }

      figcaption {
        color: #5e6670;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 0.9rem;
      }

      table {
        border-collapse: collapse;
        width: 100%;
        font-family: Arial, Helvetica, sans-serif;
      }

      th,
      td {
        border: 1px solid #cfc8bc;
        padding: 0.5rem;
        text-align: left;
      }

      th {
        background-color: #0e4d5c;
        color: #ffffff;
      }

      label {
        display: block;
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 700;
      }

      select {
        font: inherit;
        width: 100%;
        max-width: 16rem;
        padding: 0.5rem;
        margin: 0.3rem 0 1rem;
        border: 2px solid #cfc8bc;
        border-radius: 0.4rem;
        background-color: #ffffff;
      }

      select:focus {
        outline: 3px solid #c47b00;
      }

      button {
        font-family: Arial, Helvetica, sans-serif;
        cursor: pointer;
        padding: 0.6rem 1rem;
        border: 0;
        border-radius: 0.5rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Kapanış</h1>
    </header>
    <main>
      <p class="kart">Bu kart, kutunun iç boşluğunu ve çerçevesini gösterir.</p>
      <h2>Liste</h2>
      <ul>
        <li>İstanbul</li>
        <li>İzmir</li>
        <li>Trabzon</li>
        <li>Van</li>
      </ul>
      <p><a href="duraklar.html">Durak listesini aç</a></p>
      <h2>Görsel</h2>
      <figure>
        <img src="kapanis.jpg" alt="Dört kentin adının yazdığı bir not kâğıdı" />
        <figcaption>Dosya yoksa alternatif metin bu kutuda kalır.</figcaption>
      </figure>
      <h2>Tablo</h2>
      <table>
        <caption>Plakalar</caption>
        <tr>
          <th scope="col">Kent</th>
          <th scope="col">Plaka</th>
        </tr>
        <tr>
          <td>İstanbul</td>
          <td>34</td>
        </tr>
        <tr>
          <td>Van</td>
          <td>65</td>
        </tr>
      </table>
      <h2>Form</h2>
      <form action="kapanis.html" method="get">
        <label for="kent">Kent (zorunlu)</label>
        <select id="kent" name="kent" required>
          <option value="">Seçin</option>
          <option value="istanbul">İstanbul</option>
          <option value="izmir">İzmir</option>
          <option value="trabzon">Trabzon</option>
          <option value="van">Van</option>
        </select>
        <button type="submit">Kenti adres çubuğuna yaz</button>
      </form>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şeritte beyaz “Kapanış” tırnaksız aileyle ve büyük puntoyla durur. Gövde tırnaklı bir aileyle, açık kâğıdın üstünde, ortada ve en çok 40 remdedir. İlk kart beyaz, açık gri çerçeveli ve yuvarlak köşelidir. Yazı çerçeveye yapışmaz.

“Liste” yeşil bir ara başlıktır ve tırnaksızdır. Altında İstanbul, İzmir, Trabzon ve Van madde işaretleriyle durur. “Durak listesini aç” mavi ve altı çizilidir. Sekme ile gelince amber çerçeve belirir. `duraklar.html` aynı klasördeyse o sayfa açılır. Yoksa tarayıcı dosyayı bulamaz. Bağlantı yine mavi kalır.

“Görsel” başlığının altında en çok ana sütun kadar geniş, kendi oranında bir fotoğraf vardır. Köşeleri yuvarlaktır. Dosya yoksa bej zemin, kırık simge ve “Dört kentin adının yazdığı bir not kâğıdı” görünür. Alt yazı soluk ve tırnaksızdır.

Tabloda “Kent” ve “Plaka” beyaz yazı, yeşil zemindir. İstanbul ile 34, Van ile 65 aynı satırdadır. Çizgiler tek hattır. Yazı tırnaksızdır ve çizgiden içeridedir. “Plakalar” tablonun adıdır.

Formda “Kent (zorunlu)” kalın ve kutunun üstündedir. Liste beyaz, gri kenarlı ve en çok 16 remdir. Düğme yeşildir, yazısı beyazdır. Fare el şeklini alır. Kent seçilmeden adres değişmez. Trabzon seçilince adresin sonunda `kent=trabzon` görünür. Liste, görsel ve tablo yenilemeden sonra da yerinde kalır.

## Parça silinince sayfa eksik kalır

Aşağıdaki kısa belge yalnızca yazı ve bağlantı taşır. Kapanış sayfası bu hâlde bitmiş sayılmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Eksik kapanış</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Georgia, "Times New Roman", serif;
      }

      a {
        color: #0c5c8a;
      }
    </style>
  </head>
  <body>
    <h1>Kapanış</h1>
    <p><a href="https://example.com">Example Domain</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
Kâğıt zemin, tırnaklı bir başlık ve mavi bir bağlantı vardır. Bağlantı tıklanınca Example Domain sayfası açılır. Fotoğraf, tablo, kart çerçevesi ve form yoktur. Yedi parçadan yazı tipi, renk ve bağlantı durur. Kutu, görsel, tablo ve form eksiktir. Kapanış, `kapanis.html` belgesindeki yedi parça bir aradayken tamamdır.

## Başlık aralığı ve oran (Letter Spacing)

Kapanış başlığı seyrek harf ve tırnaklı gövdeyle ayrılır. Görsel `aspect-ratio` ile 16:9 yer tutar. Bu iki ayrıntı, yedi parçanın yanına yeni bir özellik yığını koymaz. Harf aralığı 7. günde, oran 15. günde kurulmuştur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Başlık ve oran</title>
    <style>
      body {
        margin: 0;
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Georgia, "Times New Roman", serif;
      }

      header {
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
        font-family: Arial, Helvetica, sans-serif;
      }

      h1 {
        margin: 0;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        font-size: 1.6rem;
      }

      main {
        max-width: 32rem;
        margin: 0 auto;
        padding: 1rem;
      }

      img {
        width: 100%;
        height: auto;
        aspect-ratio: 16 / 9;
        object-fit: cover;
        background-color: #e7e2d8;
        border-radius: 0.5rem;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Kapanış</h1>
    </header>
    <main>
      <img src="kapanis.jpg" alt="Dört kentin adının yazdığı bir not kâğıdı" />
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Şeritte “KAPANIŞ” seyrek, beyaz ve büyük harfle durur. Kaynakta kelime “Kapanış” diye yazılmıştır. Gövde tırnaklıdır. Görsel 32 remlik sütunda 16:9 bir dikdörtgendir. Dosya varsa not kâğıdı bu oranı doldurur. Dosya yoksa bej kutu ve alternatif metin aynı oranı tutar. Tablo ve form bu kısa denemede yoktur. Onlar kapanış belgesinin asıl örneğinde durur. Bu deneme, başlığın harf aralığı ile görselin oranını ayrı ayrı seçmeyi gösterir.

## Sık yapılan hata

Tablonun yazısını, gövdenin tırnaklı ailesine bırakıp hücre iç boşluğunu vermemek, ızgarayı başlıkla aynı biçimde ezer.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sıkışık tablo</title>
    <style>
      body {
        font-family: Georgia, "Times New Roman", serif;
      }

      th,
      td {
        border: 1px solid #0e4d5c;
      }
    </style>
  </head>
  <body>
    <table>
      <tr>
        <th>Van</th>
        <td>65</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” ve “65” tırnaklı harflerle, çizgiye yapışık durur. Çizgiler çift görünebilir çünkü birleşme yazılmamıştır. Form yoktur. Fotoğraf yoktur.

Doğru belgede tablo kendi ailesini, tek çizgisini ve iç boşluğunu alır. Form da kendi düğmesini alır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ayrılmış parçalar</title>
    <style>
      table {
        border-collapse: collapse;
        font-family: Arial, Helvetica, sans-serif;
      }

      th,
      td {
        border: 1px solid #cfc8bc;
        padding: 0.5rem;
      }

      button {
        font-family: Arial, Helvetica, sans-serif;
        background-color: #0e4d5c;
        color: #ffffff;
        border: 0;
        padding: 0.5rem 1rem;
        border-radius: 0.5rem;
      }
    </style>
  </head>
  <body>
    <table>
      <tr>
        <th>Van</th>
        <td>65</td>
      </tr>
    </table>
    <form action="kapanis.html" method="get">
      <button type="submit">Kenti adres çubuğuna yaz</button>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” ve “65” tırnaksız, çizgiden içeride ve tek hatlı bir tablodadır. Düğme yeşil ve beyazdır, tablonun içinde değildir. İki parça alt alta durur.

## Egzersizler

1. `kapanis.html` dosyasında kâğıt zemin, yeşil şerit ve 40 remlik tırnaklı bir sütun görünsün. Beyaz kartın çerçevesi ve iç boşluğu olsun. Dört kent maddeli listede dursun.
2. Görsel dosyasını kaldırın. Kırık simge ve alternatif metin görünsün. Dosyayı geri koyun. Fotoğraf oranını bozmadan 20 rem sınırının içinde kalsın. Alt yazı soluk dursun.
3. Tabloda İstanbul’un sağında 34, Van’ın sağında 65 görünsün. Formda kent seçilmeden adres değişmesin. Trabzon seçilince `kent=trabzon` adresin sonunda dursun. Görsel ve tablo yerinde kalsın.

[← Önceki gün](../29-site/ders.md) · [İçindekiler](../README.md)
