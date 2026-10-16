# 15. Gün — Görseller (Images)

Bu gün, fotoğrafın kutuya nasıl sığacağını ayarlar. HTML, `src` ve `alt` ile resmi çağırmıştı. Büyük bir dosya sayfayı sağa taşır. `max-width: 100%` ve `height: auto` birlikte, en-boy oranını bozmadan resmi bulunduğu kutunun içine çeker. `object-fit` ise kutu sabitken resmin kesilerek mi yoksa ezilerek mi duracağını seçer. Alt metin, resim kırıkken yine görünür. CSS onun yerine geçmez.

## Resim sayfadan taşmaz

`max-width: 100%` resmin, üst öğeden daha geniş olmasını engeller. Kendi dosyası daha darsa resim zorla büyümez. `height: auto` yüksekliği genişliğe göre yeniden kurar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sığan görsel</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      figure {
        margin: 0;
        max-width: 24rem;
      }

      img {
        max-width: 100%;
        height: auto;
        border-radius: 0.5rem;
      }

      figcaption {
        color: #5e6670;
        font-size: 0.875rem;
        margin-top: 0.4rem;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
    <figure>
      <img src="van-golu.jpg" alt="Van Gölü kıyısı" />
      <figcaption>Van Gölü, kente kıyıdan bakılınca.</figcaption>
    </figure>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” başlığının altında figür en çok 24 rem genişliğindedir. `van-golu.jpg` klasördeyse fotoğraf o genişliğin içinde, kendi oranında durur. Köşeleri hafifçe yuvarlaktır. Pencere daralınca fotoğraf da daralır ve sağa kaydırma çıkarmaz. Dosya 24 remden darsa fotoğraf kendi boyutunda kalır, zorla şişmez. Alt yazı soluk gri-mavi ve gövdeden biraz küçüktür. Fotoğrafa yapışmaz. Dosya yoksa kırık simge ve “Van Gölü kıyısı” yazısı görünür. Alt yazı onun altında durmaya devam eder.

Figürün varsayılan kenar boşluğu bu örnekte sıfırlanmıştır. Sayfanın sol girintisinde durmaz. Gövdedeki diğer kenar boşlukları başlıkta kalır.

## Sabit kutu resmi keser

`object-fit: cover` resmi kutunun tamamını kaplayacak şekilde büyütür ve taşan kenarı keser. Oran bozulmaz. Bunun için kutunun hem genişliği hem yüksekliği bellidir. `contain` resmi bütünüyle gösterir ve kutuda boş şerit kalabilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kaplanan kutu</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      img {
        width: 16rem;
        height: 10rem;
        object-fit: cover;
        border-radius: 0.5rem;
        background-color: #e7e2d8;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <img src="izmir.jpg" alt="İzmir Saat Kulesi" />
  </body>
</html>
```

Tarayıcıda görünen:
Fotoğraf varsa 16 rem’e 10 rem’lik yuvarlak köşeli bir dikdörtgenin içinde durur. Kule fotoğrafı kareyse kenarlardan kesilir. Kule ezilip yassılaşmaz. Bej zemin, resim yüklenene kadar veya dosya yokken kutunun rengidir. Dosya yoksa kırık simge ve “İzmir Saat Kulesi” bu dikdörtgenin içinde kalır. `object-fit` kırık simgeyi fotoğraf gibi kesmez. Asıl resmi, dosya durunca kaplar.

`height` ile `width` verilip `object-fit` yazılmazsa tarayıcı resmi o dikdörtgene ezerek sığdırır. Kule uzar veya basılır. Oran korunacaksa ya `height: auto` ya da `object-fit: cover` seçilir. Birincisi kutuyu resme göre uzatır. İkincisi kutuyu sabit tutup resmi kırpar.

## En-boy oranı (Aspect Ratio)

`aspect-ratio` kutunun genişlik bölü yükseklik oranını kilitler. Bir sayı yazılır. `16 / 9` geniş ekran, `1 / 1` kare demektir. Yükseklik ayrıca piksel ile bağlanmaz. Genişlik değişince yükseklik oranı bozmaz. Dosya yokken bej kutu da aynı oranda yer tutar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>En-boy</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      figure {
        margin: 0;
        max-width: 24rem;
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
    <h1>Trabzon</h1>
    <figure>
      <img src="trabzon-kiyi.jpg" alt="Trabzon’da Karadeniz kıyısı" />
      <figcaption>Kıyı 16:9 kutudadır.</figcaption>
    </figure>
  </body>
</html>
```

Tarayıcıda görünen:
Fotoğraf varsa 24 remden geniş olmayan, genişliği yüksekliğinin 16’ya 9 oranı olan bir dikdörtgen görünür. `object-fit: cover` resmi bu dikdörtgene yayar ve taşan kenarı keser. Kıyı yassılaşmaz. Pencere daralınca kutu da daralır, oran kalır. Dosya yoksa aynı oranda bej bir alan ve “Trabzon’da Karadeniz kıyısı” durur. Sayfa, resim gelince aşağı zıplamaz. Oran, yerini önceden ayırmıştır. `figcaption` kutunun altında, resmin oranının dışında durur.

`aspect-ratio` ile sabit `height` birlikte yazılırsa yükseklik oranı sıkıştırabilir. Bu örnekte yükseklik `auto` kalır. Oranı kutu, kırmayı `cover` yapar.

## Sık yapılan hata

Yalnızca `width` değiştirip yüksekliği pikselde bırakmak, oranı bozar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ezilen görsel</title>
    <style>
      img {
        width: 100%;
        height: 80px;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <img src="trabzon-kiyi.jpg" alt="Trabzon’da Karadeniz kıyısı" />
  </body>
</html>
```

Tarayıcıda görünen:
Dosya varsa kıyı fotoğrafı sayfa kadar geniş ve yalnızca 80 piksel yüksek bir şerit olur. Deniz ve kıyı yassılaşır. Daraltılınca genişlik değişir, yükseklik 80 pikselde kaldığı için ezilme artar.

Doğru çift, tavan ve otomatik yüksekliği birlikte kullanır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Oranlı görsel</title>
    <style>
      img {
        max-width: 100%;
        height: auto;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <img src="trabzon-kiyi.jpg" alt="Trabzon’da Karadeniz kıyısı" />
  </body>
</html>
```

Tarayıcıda görünen:
Fotoğraf kendi oranındadır. Sayfadan genişse pencereye sığar. Yüksekliği, genişlikle birlikte küçülür. Kıyı yassılaşmaz. Dosya yoksa alternatif metin okunur.

## Egzersizler

1. `van-golu.jpg` yokken “Van Gölü kıyısı” okunsun. Dosya varken fotoğraf 24 remden geniş olmasın. Pencereyi daraltın. Sayfa sağa taşmasın. Alt yazı soluk ve küçük kalsın.
2. 16 rem’e 10 rem’lik bir kutuda `object-fit: cover` kullanın. Fotoğraf yassılaşmadan kutuyu doldursun. Taşan kenar kesilsin.
3. Yüksekliği 80 piksele kilitleyip genişliği yüzde 100 yapın. Ezilmeyi görün. Sonra `height: auto` ve `max-width: 100%` yazın. Oran geri gelsin.

[← Önceki gün](../14-lists-tables/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../16-flexbox/ders.md)
