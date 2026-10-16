# 29. Gün — Sayfaları birbirine bağlayan site (Multi-page Site)

Bu gün, kapak, hakkında, durak listesi ve iletiyi aynı `stil.css` dosyasına bağlar. 2. günde bir stil dosyası iki sayfayı boyuyordu. Bugün dört sayfa aynı şeridi, aynı yazıyı ve aynı sütunu kullanır. Yeni bir özellik yoktur. Bir rengin değişmesi, stil dosyasında bir kez yapılır. Dört sayfa da yenilenince aynı yeşile döner.

Dört HTML dosyası ve `stil.css` aynı klasöre kaydedilir. Klasör adı başka bir dersin dosyasıyla karışmasın diye `site` olabilir. Açılan dosya `index.html` dir.

## Ortak stil

`stil.css`:

```css
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
  font-size: 1.4rem;
}

nav ul {
  display: flex;
  gap: 1rem;
  list-style: none;
  margin: 0;
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

nav strong {
  color: #ffffff;
  text-decoration: underline;
}

main {
  max-width: 40rem;
  margin: 0 auto;
  padding: 1.5rem 1rem 3rem;
}

a:link,
a:visited {
  color: #0c5c8a;
}

header a:link,
header a:visited,
header strong {
  color: #ffffff;
}

@media (max-width: 36rem) {
  header {
    flex-direction: column;
    align-items: flex-start;
  }
}
```

Tarayıcıda görünen:
`stil.css` tek başına açılırsa kurallar düz metin olarak durur. Sayfa görünmez. Renk, bu dosyayı bağlayan HTML belgelerinde çıkar.

## Dört sayfa

`index.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kent notları</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <header>
      <h1>Kent notları</h1>
      <nav>
        <ul>
          <li><strong>Kapak</strong></li>
          <li><a href="hakkinda.html">Hakkında</a></li>
          <li><a href="duraklar.html">Duraklar</a></li>
          <li><a href="iletisim.html">İletişim</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <p>Dört sayfa aynı stil dosyasını kullanır.</p>
      <p><a href="duraklar.html">Durak listesini aç</a></p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şeritte “Kent notları” solda beyazdır. “Kapak” beyaz ve altı çizilidir, tıklanınca bir yere gitmez. Diğer üç ad beyaz ve çizgisizdir. Gövde ortada, en çok 40 remdir. “Durak listesini aç” mavidir. Bu bağlantı gövdededir, şeritte değildir. Tıklanınca durak sayfası açılır. Dar pencerede şerit alt alta iner.

`hakkinda.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Hakkında</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <header>
      <h1>Hakkında</h1>
      <nav>
        <ul>
          <li><a href="index.html">Kapak</a></li>
          <li><strong>Hakkında</strong></li>
          <li><a href="duraklar.html">Duraklar</a></li>
          <li><a href="iletisim.html">İletişim</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <p>Notu yazan Serhat’tır. Kentler İstanbul, İzmir, Trabzon ve Van’dır.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Şerit aynı yeşildir. Büyük başlık “Hakkında”dır. Gezintide “Hakkında” çizilidir ve bağlantı değildir. “Kapak” tıklanınca `index.html` geri gelir. Gövde metni koyu mürekkeptir ve 40 rem sütundadır.

`duraklar.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Duraklar</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <header>
      <h1>Duraklar</h1>
      <nav>
        <ul>
          <li><a href="index.html">Kapak</a></li>
          <li><a href="hakkinda.html">Hakkında</a></li>
          <li><strong>Duraklar</strong></li>
          <li><a href="iletisim.html">İletişim</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <ol>
        <li>İstanbul</li>
        <li>Trabzon</li>
        <li>Van</li>
        <li>İzmir</li>
      </ol>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Başlık “Duraklar”dır. Gezintide bu ad altı çizilidir. Numaralı dört satır İstanbul, Trabzon, Van, İzmir diye iner. Numaralar tarayıcının varsayılanıdır. Bu sayfa 25. günün kartlarını tekrar etmez. Ortak şerit ve sütun görünür. “İletişim” tıklanınca form sayfası açılır.

`iletisim.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İletişim</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <header>
      <h1>İletişim</h1>
      <nav>
        <ul>
          <li><a href="index.html">Kapak</a></li>
          <li><a href="hakkinda.html">Hakkında</a></li>
          <li><a href="duraklar.html">Duraklar</a></li>
          <li><strong>İletişim</strong></li>
        </ul>
      </nav>
    </header>
    <main>
      <form action="iletisim.html" method="get">
        <p>
          <label for="kent">Kent</label>
          <input id="kent" name="kent" type="text" />
        </p>
        <button type="submit">Kenti adres çubuğuna yaz</button>
      </form>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Şerit yine yeşildir. “İletişim” çizili bir kelimedir. Form, ortak stilde özel bir kutu kuralı almadığı için tarayıcının düz alanına benzer. Sayfanın zemini yine kâğıt, yazı yine aynı ailedir. Van yazılıp düğmeye basılınca adres `kent=Van` taşır. Şerit kaybolmaz. Asıl deneme, dört sayfanın şerit renginin `stil.css` içinden bir kez değişmesidir. `#0e4d5c` başka bir koyu tona çekilip dört sayfa yenilenince dört şerit birden değişir. Her HTML dosyasına aynı renk yeniden yazılmaz.

## Ortak giriş (Lead)

Dört sayfa aynı `giris` sınıfını kullanır. Sınıf `stil.css` içinde bir kez yazılır. Hakkında sayfasındaki ilk cümle ile kapağın ilk cümlesi aynı puntoyu alır. Her HTML dosyasına punto yeniden yazılmaz.

`stil.css` dosyasına eklenecek kural:

```css
.giris {
  font-size: 1.2rem;
  color: #0e4d5c;
}
```

`index.html` gövdesinde paragraf bu sınıfı taşır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kent notları</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <header>
      <h1>Kent notları</h1>
    </header>
    <main>
      <p class="giris">Dört sayfa aynı puntoyu paylaşır.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şerit ve beyaz başlık, dosyanın geri kalanından gelir. “Dört sayfa aynı puntoyu paylaşır.” 1.2 rem ve koyu deniz yeşilidir. Gövdenin diğer paragrafları, sınıf almazlarsa daha küçük ve koyu mürekkep kalır. Hakkında dosyasındaki bir `p` aynı `class="giris"` değerini alınca o cümle de aynı boy ve renk olur. Stil dosyasında `1.2rem` değeri `1rem` yapılırsa iki sayfa birden küçülür.

## Sık yapılan hata

Bir sayfada `href="stil.css"`, diğerinde `href="/stil.css"` yazmak, ikinci sayfayı stilsiz bırakır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kökte aranan stil</title>
    <link rel="stylesheet" href="/stil.css" />
  </head>
  <body>
    <h1>Kapak</h1>
  </body>
</html>
```

Tarayıcıda görünen:
“Kapak” siyah bir başlıktır. Yeşil şerit yoktur. Eğik çizgi, stil dosyasını klasörün içinde değil, diskin kökünde arar. Dosya klasörde durduğu hâlde sayfa boyanmaz.

Doğru adres aynı klasörün adıdır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yanındaki stil</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <header>
      <h1>Kapak</h1>
    </header>
  </body>
</html>
```

Tarayıcıda görünen:
`stil.css` yanındaysa “Kapak” beyaz yazı ve yeşil şerit olarak durur.

## Egzersizler

1. Dört HTML dosyasını ve `stil.css` dosyasını aynı klasöre koyun. Kapakta “Kapak” çizili ve beyaz, diğer üç ad bağlantı olsun. Hakkında sayfasında çizili olan sözcük “Hakkında” olsun.
2. Stil dosyasında şerit rengini değiştirin. Dört sayfayı yenileyin. Dört şerit birden yeni renge dönsün. HTML dosyalarına aynı rengi ayrıca yazmayın.
3. Bir sayfanın `href` değerine başa eğik çizgi koyun. O sayfa stilsiz kalsın. Eğik çizgiyi silin. Yeşil şerit geri gelsin. Dar pencerede şerit alt alta insin.

[← Önceki gün](../28-faq/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../30-closing/ders.md)
