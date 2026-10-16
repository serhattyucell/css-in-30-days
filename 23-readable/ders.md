# 23. Gün — Okunabilir sayfa (Readable Page)

Bu gün, ilk yirmi iki gündeki kuralları uzun bir notun okunması için bir araya getirir. Yeni bir özellik yoktur. Kâğıt zemin, koyu mürekkep, sınırlı satır genişliği, satır aralığı, başlık boyutu ve odak çerçevesi zaten yazılmıştı. Bugün bunlar aynı belgede, birbirinin rengini silmeden durur. Dar bir satır, gözün sonraki satırın başını kaybetmemesi içindir.

## Satır ölçüsü ve punto

Gövde `1rem` ve `1.6` satır aralığında durur. Ana sütun `38rem` ile sınırlanır ve ortaya alınır. Başlıklar `rem` ile köke bağlıdır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Okunabilir not</title>
    <style>
      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1.125rem;
        line-height: 1.6;
      }

      main {
        max-width: 38rem;
        margin: 0 auto;
        padding: 1.5rem 1rem 3rem;
      }

      h1 {
        margin: 0 0 0.5rem;
        color: #0e4d5c;
        font-family: Georgia, "Times New Roman", serif;
        font-size: 2.2rem;
        line-height: 1.2;
      }

      h2 {
        margin: 2rem 0 0.5rem;
        color: #0e4d5c;
        font-size: 1.4rem;
        line-height: 1.3;
      }

      p {
        margin: 0 0 1rem;
      }

      a:link,
      a:visited {
        color: #0c5c8a;
        text-decoration: underline;
      }

      a:hover,
      a:focus {
        color: #0e4d5c;
        outline: 3px solid #c47b00;
        outline-offset: 2px;
      }
    </style>
  </head>
  <body>
    <main>
      <h1>Karadeniz kıyısı</h1>
      <p>Trabzon notu kısa cümlelerle, dar bir sütunda okunur.</p>
      <h2>Kıyı</h2>
      <p>
        Çarşıdan denize inilir. Satır 38 rem’den genişlemez.
        Göz, uzun bir satırın sonundan başa dönerken yorulmaz.
      </p>
      <h2>Sözlük</h2>
      <p>
        Renk adları bu sayfada hex değeriyle durur.
        Örnek adres
        <a href="https://example.com">Example Domain</a>
        sayfasıdır.
      </p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfa açık kâğıttır. Metin, pencerenin ortasında, en çok 38 rem genişliğinde bir sütundadır. Geniş bir pencerede sağda ve solda boş kâğıt kalır. Dar pencerede sütun kenarlara 1 rem payla sığar. “Karadeniz kıyısı” tırnaklı bir aileyle, koyu deniz yeşili ve gövdenin yaklaşık iki katı büyüklüğündedir. “Kıyı” ve “Sözlük” daha küçüktür, aynı yeşildir ve üstlerinde gövdeden daha geniş bir boşluk vardır. Paragraflar koyu mürekkep, 1.125 rem ve ferah satır aralığındadır. “Example Domain” altı çizili ve mavidir. Üzerine gelince veya Sekme ile gelince yeşile döner ve amber bir çerçeve belirir. Çerçeve satırı aşağı itmez.

Bu sayfada gölge, hareket ve ikinci bir yazı rengi yığını yoktur. Okunurluk, zemin ile mürekkebin ayrılmasından ve satırın kısa tutulmasından gelir.

## Odak silinmez

Ana metindeki bağlantının alt çizgisi durur. `outline: none` bu belgede yazılmaz. Klavye ile gezen kişi yerini görür.

Aşağıdaki kısa belge, ölçü olmadan aynı metnin nasıl yayıldığını gösterir. Tam sayfanın kopyası değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ölçüsüz satır</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1.125rem;
      }
    </style>
  </head>
  <body>
    <h1>Karadeniz kıyısı</h1>
    <p>Bu paragraf pencere kenarına kadar gider. Geniş ekranda satır çok uzar.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Karadeniz kıyısı” tarayıcının varsayılan dev puntosundadır. Paragraf sol kenardan sağ kenara kadar uzar. 38 remlik bir sütun yoktur. Satır, geniş pencerede gözün izleyemeyeceği kadar uzun olabilir. Zemin kâğıttır. Ölçü eksik olduğu için bu belge, günün asıl sayfasının yerine geçmez.

## İlk paragraf (Lead)

`p:first-of-type` sütundaki ilk paragrafı biraz büyütür. Sonraki paragraflar gövde puntosunda kalır. İlk çocuk şartı burada yetmez. Sütunun ilk öğesi bir başlıktır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İlk paragraf</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1.05rem;
        line-height: 1.6;
      }

      main {
        max-width: 38rem;
        margin: 0 auto;
        padding: 1rem;
      }

      p:first-of-type {
        font-size: 1.25rem;
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <main>
      <h1>Van Gölü</h1>
      <p>Göl geniştir. Bu ilk paragraf, başlıktan sonra gelen giriş cümlesidir.</p>
      <p>Kale tepeden bakar. Bu ikinci paragraf gövde puntosundadır.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü” normal bir büyük başlıktır. Altındaki ilk paragraf 1.25 rem ve koyu deniz yeşilidir. “Kale tepeden bakar…” 1.05 rem ve koyu mürekkeptir. İki paragraf da sütunun 38 rem sınırı içindedir. Başlık yeşil girişten daha büyüktür. Giriş, gövdeden bir kademe büyüktür. `p:first-child` olsaydı hiçbiri seçilmezdi. İlk çocuk başlıktır.

## Sık yapılan hata

Açık gri yazıyı açık kâğıda basmak, punto doğru olsa da satırı siler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Soluk mürekkep</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #d9d3c7;
        font-size: 1.125rem;
      }
    </style>
  </head>
  <body>
    <p>Trabzon notu bu renkte okunmaz.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Cümle kâğıda yakın, çok açık bir tondadır. Punto büyük olsa bile harf kenardan zor ayrılır. Satır biçim olarak durur, okuma olarak durmaz.

Doğru mürekkep koyudur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Koyu mürekkep</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1.125rem;
        line-height: 1.6;
      }

      main {
        max-width: 38rem;
        margin: 0 auto;
        padding: 1rem;
      }
    </style>
  </head>
  <body>
    <main>
      <p>Trabzon notu koyu harfle, dar sütunda okunur.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Cümle koyu mürekkeptir. Zemin açık kâğıttır. Sütun ortaya alınmıştır ve 38 remde durur.

## Egzersizler

1. Ana sütunu 38 rem ile sınırlayın ve ortaya alın. Gövde 1.125 rem ve 1.6 satır aralığında, koyu mürekkeple kâğıdın üstünde dursun. Başlık tırnaklı aileyle ve yeşil olsun.
2. Bir bağlantı mavi ve altı çizili kalsın. Sekme tuşuyla gelince amber çerçeve görünsün. Çerçeve satırları birbirine kaydırmasın.
3. Yazı rengini açık gri yapın. Cümlenin zor okunduğunu görün. Rengi koyu mürekkepe döndürün. Aynı cümle kâğıttan ayrılsın.

[← Önceki gün](../22-cascade/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../24-about/ders.md)
