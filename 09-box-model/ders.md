# 9. Gün — Kutu modeli (Box Model)

Bu gün, her öğeyi dört katmanlı bir kutu olarak okur. İçerik ortadadır. Onun çevresinde iç boşluk, yani `padding` durur. İç boşluğun çevresinde `border` vardır. Kenarlığın dışında da `margin` durur ve komşu kutuyu iter. 7. gündeki hiza, yazıyı kutunun içinde kaydırıyordu. Kenar boşluğu kutunun kendisini komşusundan ayırır.

## İç boşluk ile kenar boşluğu ayrı yerdedir

Zemin, içeriği ve iç boşluğu boyar. Kenar boşluğunu boyamaz. Kenar boşluğu, zeminin bittiği yerden sonraki aralıktır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dört katman</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1rem;
      }

      .kart {
        background-color: #ffffff;
        color: #1e2430;
        padding: 1rem;
        border: 2px solid #0e4d5c;
        margin: 1.5rem;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
    <p class="kart">Göl geniştir. Beyaz kutu, göl cümlesinin çevresine iç boşluk bırakır.</p>
    <p>Bu paragraf kartın altındadır ve aradaki açıklık kenar boşluğudur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfa açık kâğıttır. “Van” başlığından sonra beyaz bir kutu gelir. Kutunun çevresinde koyu deniz yeşili, yaklaşık 2 piksellik bir çizgi vardır. “Göl geniştir…” cümlesi çizgiye yapışmaz. Yazı ile çizgi arasında içeriden yaklaşık 1 rem boşluk vardır. Bu boşluk beyazdır çünkü iç boşluk da zemine dahildir. Çizginin dışında, kâğıt renginde bir aralık vardır. Alttaki “Bu paragraf kartın altındadır…” cümlesi beyaz kutuya değmez. İkisinin arasındaki kâğıt, `margin` değeridir.

`padding: 1rem` dört yana birden aynı boşluğu verir. `padding: 1rem 2rem` önce üst ve alt, sonra sağ ve sol demektir. `margin: 0` kenar boşluğunu sıfırlar. Tarayıcı, başlık ve paragrafa varsayılan bir kenar boşluğu verir. İki paragraf arasındaki açıklığın bir kısmı oradan gelir.

## Dikey kenar boşlukları birleşir

Üst üste iki bloğun alt ve üst kenar boşluğu, ikisi birden toplanmaz. Çoğu durumda büyük olan kalır. Buna kenar boşluğu birleşmesi denir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Birleşen boşluk</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      p {
        margin-top: 1rem;
        margin-bottom: 1rem;
        background-color: #ffffff;
      }
    </style>
  </head>
  <body>
    <p>İstanbul</p>
    <p>Trabzon</p>
  </body>
</html>
```

Tarayıcıda görünen:
İki beyaz satır arasında yaklaşık 1 rem kâğıt vardır. 1 rem artı 1 rem, 2 rem olmamıştır. Üst paragrafın alt boşluğu ile alt paragrafın üst boşluğu birleşmiş, büyük olan 1 rem kalmıştır. Kutuların yan yana gelen yatay boşlukları birleşmez. Soldaki ve sağdaki boşluk, her kutu için ayrı durur. Dikey birleşme, paragrafın varsayılan boşluğunun neden bazen beklenenden küçük göründüğünü açıklar.

Bir bloğu yatayda ortaya almak, sol ve sağ kenar boşluğunu `auto` yapmaktır. Bunun için kutunun genişliği, üst öğeden dar olmalıdır. Genişlik 10. günde ayrıca açılır. Kısa bir deneme bugün de görünür:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ortada kutu</title>
    <style>
      .dar {
        width: 16rem;
        margin-left: auto;
        margin-right: auto;
        padding: 1rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        text-align: center;
      }
    </style>
  </head>
  <body>
    <p class="dar">Van Gölü</p>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz kutu yaklaşık 16 rem genişliğindedir ve sayfanın yatay ortasındadır. Sol ve sağda kâğıt boşluğu kalır. “Van Gölü” kutunun içinde de ortalanmıştır. `text-align` yazıyı, `auto` kenar boşluğu kutuyu ortalar. İkisi birlikte durunca hem kutu hem yazı ortadadır. Yalnızca `text-align` olsaydı tam genişlikteki paragrafın yazısı ortalanır, dar bir kutu ortaya çıkmazdı.

## Dört yön (Shorthand Order)

Kısaltmada bir değer dört yana gider. İki değer önce üst ve alt, sonra sağ ve sol demektir. Üç değer üst, yanlar ve alttır. Dört değer saat yönüdür: üst, sağ, alt, sol. Saat, tepeden başlayıp sağa döner.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Saat yönü</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .saat {
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        padding: 0.4rem 2rem 1.2rem 0.6rem;
        margin: 1rem 0 0 2rem;
      }
    </style>
  </head>
  <body>
    <p class="saat">Van Gölü. Üst dar, sağ geniş, alt daha geniş, sol orta bir iç boşluktadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz kutu, sayfanın solundan 2 rem içeride başlar. Üst kenar boşluğu yaklaşık 1 remdir. Dört sayı saat yönündedir: üst `1rem`, sağ `0`, alt `0`, sol `2rem`. Sağ ve alt kenar boşluğu yoktur. Yazı, yeşil çizgiye her yandan aynı uzaklıkta değildir. Üstte yaklaşık 0.4 rem, sağda 2 rem, altta 1.2 rem, solda 0.6 rem boşluk vardır. “Van Gölü…” cümlesi sol iç boşluğun bittiği yerden başlar ve sağda geniş bir beyaz alan bırakır. Uzun cümle sağdaki 2 rem paya gelince kırılır.

Saat yönü `margin` ve `border-width` kısaltmasında da aynıdır. `border-width: 1px 4px` üst ve alt kenarlığı ince, sağ ve sol kenarlığı kalın yapar. `margin: 0 auto` iki değer olduğu için üst ve alt sıfır, sağ ve sol `auto` olur. Kutuyu ortaya alan kısaltma budur. Dört sayıyı sırasız yazmak, geniş boşluğu yanlış kenara oturtur. Sol pay gerektiği hâlde metin sağa yapışır.

## Sık yapılan hata

İç boşluk ile kenar boşluğunu karıştırıp gölgeyi komşuya değdirmektir. `padding` komşuyu itmez. Yazıyı çizgiden içeri alır. `margin` çizgiyi komşudan uzaklaştırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yapışık komşu</title>
    <style>
      .kart {
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 0;
        margin: 0;
      }
    </style>
  </head>
  <body>
    <p class="kart">İzmir</p>
    <p class="kart">Van</p>
  </body>
</html>
```

Tarayıcıda görünen:
İki koyu deniz yeşili şerit vardır. “İzmir” ve “Van” beyazdır ve şeridin kenarına yapışıktır. İki şerit arasında kâğıt görünmez. Biri diğerine değer. Harfler kutunun sol kenarından başlar.

Doğru kutuda yazı içeriden, komşu dışarıdan ayrılır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ayrılmış komşu</title>
    <style>
      body {
        background-color: #f4f1ea;
      }

      .kart {
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
        margin-bottom: 1rem;
      }
    </style>
  </head>
  <body>
    <p class="kart">İzmir</p>
    <p class="kart">Van</p>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz “İzmir” ve “Van”, yeşil şeridin kenarından içeride durur. İki şerit arasında yaklaşık 1 rem kâğıt vardır. İkinci şeridin altındaki boşluk da görünür. Yazı çizgiye yapışmaz.

## Egzersizler

1. Beyaz bir kart kurun. İçinde “Göl geniştir.” cümlesi, yeşil çizgiden içeride dursun. Kartın dışında kâğıt rengi görünsün. Alttaki sıradan paragraf karta değmesin.
2. İki paragrafın üst ve alt kenar boşluğunu 1 rem yapın. Aradaki boşluk 2 rem olmasın. Büyük olan boşluk kadar, yaklaşık 1 rem görünsün.
3. 16 rem genişliğinde bir kutuyu `margin-left` ve `margin-right` ile ortaya alın. “Van Gölü” kutunun içinde de ortalansın. Kutu solda yapışık kalmasın.

[← Önceki gün](../08-units/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../10-size/ders.md)
