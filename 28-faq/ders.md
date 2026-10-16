# 28. Gün — Küçük sayfa: sık sorulan sorular (FAQ)

Bu gün, beş soruyu üstte bir sıra, altta açık cevaplar olarak biçimlendirir. Yeni bir özellik yoktur. Cevaplar gizlenmez. Açılıp kapanan kutu bu sayfada yoktur. Soru bir başlıktır, cevap bir paragraftır, aralarındaki boşluk ve sol çizgi onları ayırır.

## Açık cevaplar, dar sütun

Belge `sorular.html` adıyla kaydedilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sık sorulan sorular</title>
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
        font-size: 1.7rem;
      }

      main {
        max-width: 40rem;
        margin: 0 auto;
        padding: 1.5rem 1rem 3rem;
      }

      nav ol {
        margin: 0 0 1.5rem;
        padding-left: 1.2rem;
      }

      nav a:link,
      nav a:visited {
        color: #0c5c8a;
        text-decoration: underline;
      }

      nav a:hover,
      nav a:focus {
        color: #0e4d5c;
        outline: 3px solid #c47b00;
        outline-offset: 2px;
      }

      article {
        margin-bottom: 1.2rem;
        padding: 0.2rem 0 0.2rem 1rem;
        border-left: 4px solid #0e4d5c;
        background-color: #ffffff;
      }

      h2 {
        margin: 0;
        padding: 0.8rem 1rem 0;
        color: #0e4d5c;
        font-size: 1.2rem;
      }

      article p {
        margin: 0;
        padding: 0.4rem 1rem 0.9rem;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Sık sorulan sorular</h1>
    </header>
    <main>
      <nav>
        <ol>
          <li><a href="#yol">Notlar bir yol tarifi midir?</a></li>
          <li><a href="#kirik">Fotoğraf neden kırık görünür?</a></li>
          <li><a href="#form">Form neden ileti göndermez?</a></li>
          <li><a href="#cizgi">Tabloda çizgi neden tek hâttedir?</a></li>
          <li><a href="#kent">Hangi kentler vardır?</a></li>
        </ol>
      </nav>
      <article>
        <h2 id="yol">Notlar bir yol tarifi midir?</h2>
        <p>Değildir. İstanbul, Trabzon, Van ve İzmir bir okuma sırasıdır.</p>
      </article>
      <article>
        <h2 id="kirik">Fotoğraf neden kırık görünür?</h2>
        <p>Dosya, sayfayla aynı klasörde yoksa simge ve alternatif metin kalır.</p>
      </article>
      <article>
        <h2 id="form">Form neden ileti göndermez?</h2>
        <p>Yazılanlar adres çubuğuna düşer. serhat@example.com bir örnektir.</p>
      </article>
      <article>
        <h2 id="cizgi">Tabloda çizgi neden tek hâttedir?</h2>
        <p>Komşu kenarlıklar birleşir. Çift çizgi ızgarayı kalınlaştırır.</p>
      </article>
      <article>
        <h2 id="kent">Hangi kentler vardır?</h2>
        <p>İstanbul, İzmir, Trabzon ve Van.</p>
      </article>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şeritte beyaz “Sık sorulan sorular” vardır. Altında, ortaya alınmış 40 remlik sütunun başında numaralı beş soru durur. Her soru mavi ve altı çizilidir. Üzerine gelince yazı yeşile döner, amber çerçeve belirir. “Form neden ileti göndermez?” tıklanınca sayfa o başlığa kayar. Adreste `#form` vardır.

Cevaplar kapalı kutu değildir. Her soru beyaz bir bloğun içindedir. Bloğun solunda 4 piksel yeşil çizgi vardır. Soru yeşil ve gövdeden biraz büyüktür. Cevap koyu mürekkeptir ve sorunun hemen altındadır. Blokların arasında kâğıt görünür. Beş cevap da sayfa açılınca okunur. İkinci bir tıklama gerekmez.

## Son cevabın boşluğu (Last Child)

Beş beyaz blok alt alta durunca sonuncunun alt boşluğu sayfayı uzatır. `article:last-child` o boşluğu kapatır. İlk soru `article:first-of-type` ile üst boşluğunu da kısaltabilir. Üstteki numaralı liste, main’in ilk çocuğu olduğu için `article:first-child` ilk soruyu seçmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Son cevap</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      main {
        max-width: 32rem;
        margin: 0 auto;
      }

      article {
        margin-bottom: 1rem;
        padding: 0.6rem 1rem;
        border-left: 4px solid #0e4d5c;
        background-color: #ffffff;
      }

      article:last-child {
        margin-bottom: 0;
      }

      h2 {
        margin: 0;
        color: #0e4d5c;
        font-size: 1.15rem;
      }
    </style>
  </head>
  <body>
    <main>
      <article>
        <h2>Notlar bir yol tarifi midir?</h2>
        <p>Değildir. Dört kent bir okuma sırasıdır.</p>
      </article>
      <article>
        <h2>Hangi kentler vardır?</h2>
        <p>İstanbul, İzmir, Trabzon ve Van.</p>
      </article>
    </main>
    <p>Son cevabın altında kart boşluğu yoktur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
İki beyaz blok, solda yeşil çizgiyle durur. Aralarında yaklaşık 1 rem kâğıt vardır. “Hangi kentler vardır?” bloğunun altında aynı boşluk yoktur. “Son cevabın altında kart boşluğu yoktur.” cümlesi bloğa yakındır. Başlıklar yeşil, cevaplar koyu mürekkeptir. İki cevap da açıktır.

## Sık yapılan hata

Başlığı kalın paragraf yapıp `id` koymamak, üstteki bağlantıyı boş bir adrese götürür.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağsız soru</title>
    <style>
      p {
        font-weight: 700;
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <p><a href="#form">Form neden ileti göndermez?</a></p>
    <p>Form neden ileti göndermez? Çünkü sunucu yoktur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Üstte mavi bir bağlantı, altta yeşil kalın bir cümle vardır. Tıklama `#form` hedefini bulamaz. Sayfa yerinde kalır veya en üste sıçrar. Soru ile cevap aynı blokta ayırt edilmez. Sol çizgi yoktur.

Doğru belgede soru bir başlıktır ve bağlantıyla aynı kimliği taşır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağlı soru</title>
    <style>
      article {
        border-left: 4px solid #0e4d5c;
        background-color: #ffffff;
        padding: 0.6rem 1rem;
      }

      h2 {
        color: #0e4d5c;
        font-size: 1.2rem;
      }
    </style>
  </head>
  <body>
    <p><a href="#form">Form neden ileti göndermez?</a></p>
    <article>
      <h2 id="form">Form neden ileti göndermez?</h2>
      <p>Yazılanlar adres çubuğunda durur.</p>
    </article>
  </body>
</html>
```

Tarayıcıda görünen:
Bağlantı tıklanınca yeşil başlık üste gelir. Cevap başlığın altında, beyaz bloğun içindedir. Bloğun solunda yeşil çizgi vardır.

## Egzersizler

1. `sorular.html` dosyasında beş soru üstte numaralı ve mavi bağlantı olarak dursun. Her cevap sayfa açılınca görünsün. Gizlenen bir kutu belirmesin.
2. Her soru beyaz blokta, solda yeşil çizgiyle dursun. Başlık yeşil, cevap koyu mürekkep olsun. Sütun 40 remde ortaya alınsın.
3. Bir sorunun `id` değerini silin. Bağlantı o başlığa inmesin. Kimliği geri koyun. Tıklama başlığı üste alsın ve amber odak çerçevesi görünsün.

[← Önceki gün](../27-comparison-table/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../29-site/ders.md)
