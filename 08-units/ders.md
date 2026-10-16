# 8. Gün — Birimler (Units)

Bu gün, ölçülerin neye göre hesaplandığını ayırır. 6. günde boyut pikseldi. Piksel sabittir. `rem` kök yazı boyutuna, `em` bulunduğu yerin yazı boyutuna, `%` ise çoğunlukla kapsayan kutunun ölçüsüne bakar. Sonraki günlerdeki boşluk ve genişlik bu dört birimle yazılır.

## Piksel sabit, rem köke bağlıdır

`px` ekran pikselidir. `rem` kök öğenin, yani `html` etiketinin yazı boyutunun katıdır. Kök 16 piksel ise `1rem` 16 pikseldir. `2rem` 32 piksel olur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Rem</title>
    <style>
      html {
        font-size: 16px;
      }

      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1rem;
      }

      h1 {
        color: #0e4d5c;
        font-size: 2rem;
      }

      .kucuk {
        font-size: 0.875rem;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Saat Kulesi 1 rem yüksekliğindeki bir gövde metnindedir.</p>
    <p class="kucuk">Bu satır 0.875 rem ile biraz daha küçüktür.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” gövde metninin yaklaşık iki katı büyüklüktedir ve koyu deniz yeşilidir. Birinci paragraf kök boyuttadır. “Bu satır 0.875 rem ile biraz daha küçüktür.” satırı paragraftan bir parça küçüktür. Üç ölçü de 16 pikselden hesaplanır. Kök `font-size: 20px` yapılırsa başlık, gövde ve küçük satır birden büyür. Piksel ile yazılmış bir başlık yerinde kalırdı. `rem`, sayfanın ölçeğini tek yerden değiştirir.

`.kucuk` sınıfı o paragrafın boyutunu köke bağlar. Aynı sınıf başka bir paragrafa da konunca o satır da 0.875 rem olur.

## em bulunduğu yere bakar

`em`, özelliğin yazıldığı öğenin yazı boyutuna bağlıdır. `font-size` için hesap, öğenin kendi boyutundan önce, üst öğenin boyutundan yapılır. İç içe iki `em` punto, katlanarak küçülür veya büyür.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Em</title>
    <style>
      body {
        font-size: 16px;
        font-family: Arial, Helvetica, sans-serif;
        background-color: #f4f1ea;
        color: #1e2430;
      }

      .dis {
        font-size: 1.2em;
      }

      .ic {
        font-size: 1.2em;
      }
    </style>
  </head>
  <body>
    <p>Düz satır 16 pikseldir.</p>
    <article class="dis">
      <p>Dış satır biraz büyüktür.</p>
      <p class="ic">İç satır bir kez daha büyür.</p>
    </article>
  </body>
</html>
```

Tarayıcıda görünen:
“Düz satır 16 pikseldir.” kök boyuttadır. “Dış satır biraz büyüktür.” ondan büyüktür. Yaklaşık 19 pikseldir. “İç satır bir kez daha büyür.” dış satırın da 1.2 katıdır. Yaklaşık 23 pikseldir. İki sınıf da aynı `1.2em` değerini taşır. Sonuçlar eşit değildir. İç paragraf, dış yazının büyümüş boyutunu katlar. Paragraflar ayrı satırlarda durduğu için boy farkı alt alta okunur. Kent notunda iç içe `em` ile punto büyütmek yerine `rem` kullanılır. Başlık `2rem`, gövde `1rem` olunca bir listenin içindeki satır başlığın katına çıkmaz.

## Yüzde, kapsayana bakar

Genişlikte `%`, üst öğenin genişliğinin yüzdesidir. Yazı boyutunda `%`, üst öğenin yazı boyutunun yüzdesidir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yüzde</title>
    <style>
      body {
        font-family: Arial, Helvetica, sans-serif;
        background-color: #f4f1ea;
        color: #1e2430;
      }

      .yari {
        width: 50%;
        background-color: #e7e2d8;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p class="yari">Bu kutu, sayfa genişliğinin yarısı kadardır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” normal bir başlıktır. Altındaki paragrafın arkası açık bejdir. Bej kutu, pencerenin yaklaşık yarısı kadar genişler. Pencere daraltılınca kutu da daralır. Yarım oran kalır. 200 piksel yazılsaydı pencere değişince kutu aynı genişlikte durur, dar pencerede taşabilirdi. Yüzde, kutu üst öğeyle birlikte ölçeklenir.

## Görünüm birimi (Viewport)

`vw` pencere genişliğinin yüzde biridir. `vh` pencere yüksekliğinin yüzde biridir. `50vw` pencerenin yarısı kadar bir genişliktir. Pencere değişince ölçü de değişir. `%` ise üst öğenin ölçüsüne bakar. İkisi dar bir kartın içinde aynı değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Pencere payı</title>
    <style>
      body {
        margin: 0;
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .pencere {
        width: 50vw;
        padding: 1rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }

      .uste {
        width: 50%;
        padding: 1rem;
        margin-top: 1rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
      }

      .dar-kutu {
        width: 20rem;
      }
    </style>
  </head>
  <body>
    <p class="pencere">İstanbul. Bu kutu pencerenin yarısıdır.</p>
    <article class="dar-kutu">
      <p class="uste">Van. Bu kutu yazının durduğu kutunun yarısıdır.</p>
    </article>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şerit, tarayıcı penceresinin yaklaşık yarısı kadardır. Pencere sürüklenince şerit de büyür veya küçülür. “İstanbul. Bu kutu pencerenin yarısıdır.” beyazdır. Alttaki beyaz kutu, yeşil çerçevelidir ve 20 remlik yazının yarısı, yani yaklaşık 10 remdir. Pencere genişlese de bu beyaz kutu 10 remde kalır. Çünkü `%` üst öğeye bakar. Üst öğe 20 remdir. `vw` üst öğeyi görmez. Kaydırma çubuğu çıkınca `100vw` bazen çubuğun payı kadar taşabilir. Tam sayfa genişliği için `100vw` yerine `100%` ve `box-sizing` daha az sürpriz verir. `vw` bir şeridi pencereye oranlamak için kullanılır, satır ölçüsü için değil. Okuma sütunu `rem` ile sınırlanır.

## Sık yapılan hata

İç içe her kutuya `font-size: 0.8em` yazmak, en alttaki metni okunmayacak kadar küçültür.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Katlanan küçülme</title>
    <style>
      body {
        font-size: 16px;
      }

      article,
      section,
      p {
        font-size: 0.8em;
      }
    </style>
  </head>
  <body>
    <article>
      <p>İstanbul</p>
      <section>
        <p>İzmir</p>
        <p>Van</p>
      </section>
    </article>
  </body>
</html>
```

Tarayıcıda görünen:
“İstanbul” birden fazla katmandan geçtiği için 16 pikselin çok altında kalır. “İzmir” ve “Van” bir katman daha içerde olduğu için daha da küçük durur. Aynı `0.8em` her basamakta yeniden uygulanmıştır.

Doğru ölçüde üç ad da köke bağlanır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Köke bağlı</title>
    <style>
      html {
        font-size: 16px;
      }

      p {
        font-size: 1rem;
      }
    </style>
  </head>
  <body>
    <p>İstanbul</p>
    <p>İzmir</p>
    <p>Van</p>
  </body>
</html>
```

Tarayıcıda görünen:
Üç satır da aynı boyuttadır. Biri diğerinin içinde küçülmez.

İkinci hata, `width: 50` yazıp birimi unutmaktır. Sıfır dışındaki sayılar birim ister. Birimsiz 50, genişlik bildirimini düşürür. Kutu yine satırın tamamını kaplar. `0` birim almadan da durabilir. `50%` veya `50px` açık yazılır.

## Egzersizler

1. Kökü 16 piksel yapın. Gövde `1rem`, “İzmir” başlığı `2rem` olsun. Kökü 20 piksele çıkarın. Başlık ve gövde birlikte büyüsün.
2. İç içe iki öğeye `1.2em` verin. İçteki yazı dıştakinden büyük görünsün. Sonra ikisini de `1.2rem` yapın. İçteki, dıştakinin katına çıkmasın. İkisi de kökün 1.2 katı olsun.
3. Bir paragrafa `%50` genişlik ve açık bej zemin verin. Pencereyi daraltın. Bej kutu yarı oranını koruyarak küçülsün.

[← Önceki gün](../07-text/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../09-box-model/ders.md)
