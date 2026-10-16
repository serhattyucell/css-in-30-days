# 10. Gün — Boyut ve taşma (Size and Overflow)

Bu gün, kutunun ne kadar yer kaplayacağını ve sığmayan metnin ne olacağını seçer. 9. günde iç boşluk ve kenar boşluğu vardı. Genişlik yazılınca iç boşluk bu genişliğin dışına eklenebilir. `box-sizing` hesabın nereden yapılacağını söyler. `max-width` bir tavan koyar. `overflow` taşan metnin görünür kalacağını, kesileceğini veya kaydırılacağını seçer.

## İçerik kutusu ile kenarlık kutusu

Varsayılan hesap `content-box` modelidir. `width` yalnızca içeriği ölçer. İç boşluk ve kenarlık bu sayının üstüne biner. `border-box` modelinde `width`, içeriği, iç boşluğu ve kenarlığı birlikte kapsar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki hesap</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .icerik {
        box-sizing: content-box;
        width: 12rem;
        padding: 1rem;
        border: 4px solid #0e4d5c;
        background-color: #ffffff;
        margin-bottom: 1rem;
      }

      .kenar {
        box-sizing: border-box;
        width: 12rem;
        padding: 1rem;
        border: 4px solid #0e4d5c;
        background-color: #ffffff;
      }
    </style>
  </head>
  <body>
    <h1>İki kutu</h1>
    <p class="icerik">Bu kutu içerikten ölçülür. İstanbul notu taşmaya yakındır.</p>
    <p class="kenar">Bu kutu kenarlıktan ölçülür. Van notu aynı 12 rem içine sığar.</p>
  </body>
</html>
```

Tarayıcıda görünen:
İki beyaz kutu da 12 rem diye yazılmıştır. Üstteki kutu daha geniştir. 12 rem içeriğin genişliğidir. Sağında ve solunda 1 rem iç boşluk, onun dışında da 4 piksellik yeşil çizgi vardır. Alttaki kutu daha dardır. 12 rem, çizginin dışından çizginin dışına kadardır. İç boşluk ve çizgi bu 12 remin içindedir. Yazı alanı daha kısadır. Gözle bakınca alttaki kutunun yeşil çerçevesi, üsttekinin çerçevesinden daha solda biter.

Sayfanın tamamında `border-box` kullanılacaksa kural bütün öğelere verilebilir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek hesap</title>
    <style>
      * {
        box-sizing: border-box;
      }

      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      main {
        width: 32rem;
        max-width: 100%;
        margin-left: auto;
        margin-right: auto;
        padding: 1rem;
        background-color: #ffffff;
      }
    </style>
  </head>
  <body>
    <main>
      <h1>Trabzon</h1>
      <p>Kıyı notu dar pencerede sayfanın dışına taşmaz.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz sütun, pencere genişken yaklaşık 32 remdir ve yatayda ortadadır. Pencere 32 remden daralınca sütun pencereyi geçer. `%100` tavan, sütunu pencerenin içine çeker. `padding: 1rem` yazıyı içeri alır. `border-box` olduğu için bu iç boşluk 32 remin dışına eklenmez. Sütun, iç boşlukla birlikte 32 remde kalır. `*` seçicisi belgedeki her öğeyi seçer. Aynı hesap başlığa da paragrafa da uygulanır.

## Taşan metin

`height` kutuyu sabit bir yüksekliğe kilitler. Metin sığmazsa varsayılan `overflow: visible` ile kutu dışına akar ve alttaki satırın üstüne binebilir. `auto` kaydırma çubuğu getirir. `hidden` taşı keser.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Taşma</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .kisa {
        width: 14rem;
        height: 3rem;
        overflow: auto;
        padding: 0.5rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p class="kisa">
      Saat Kulesi meydandadır. Kordon kıyı boyunca yürür. Körfez kenti denize açar.
      Bu cümleler 3 rem yüksekliğe sığmaz.
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil çerçeveli beyaz kutu yaklaşık 14 rem genişliğinde ve 3 rem yüksekliğindedir. Dört cümle kutunun içinde kalır. Sığmayan satırlar kutunun altında sayfaya dökülmez. Kutunun sağında veya altında bir kaydırma çubuğu çıkar. Çubuk aşağı indirilince “Bu cümleler 3 rem yüksekliğe sığmaz.” satırı görünür. `overflow: hidden` olsaydı çubuk olmaz, sığmayan satır görünmezdi. Uzun bir kent notunu saklamak için `hidden` kullanılmaz. Not okunacaksa yükseklik serbest bırakılır. Sabit yükseklik, kısa bir kutu bilerek sınırlanacaksa ve kaydırma varsa yerindedir.

## En az ve en çok (Min and Max)

`min-height` kutunun bu yükseklikten daha kısa olmamasını ister. İçerik uzarsa kutu büyür. `max-height` tavan koyar. Taşan metin `overflow` ile kesilir veya kayar. `min-width` ve `max-width` aynı işi yatayda yapar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tavan ve taban</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .taban {
        min-height: 6rem;
        padding: 1rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        margin-bottom: 1rem;
      }

      .tavan {
        max-height: 4rem;
        overflow-y: auto;
        padding: 0.5rem 1rem;
        background-color: #ffffff;
        border: 2px solid #c47b00;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p class="taban">Kısa cümle. Kutu yine de 6 remden kısa durmaz.</p>
    <p class="tavan">
      Kordon kıyı boyunca yürür. Körfez kenti denize açar. Saat Kulesi meydandadır.
      Bu satırlar 4 rem tavana sığmaz ve kutunun içinde kayar.
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” başlığının altında beyaz, yeşil çerçeveli bir kutu vardır. İçinde tek kısa cümle olmasına rağmen kutu yaklaşık 6 rem yüksektir. Altında boş beyaz alan kalır. İkinci kutu amber çerçevelidir ve en çok 4 remdir. Uzun kıyı cümleleri dışarı dökülmez. Kutunun sağında bir kaydırma çubuğu çıkar. `overflow-y: auto` yalnız dikey taşmada çubuk getirir. `overflow-x` yatay taşmayı yönetir. İkisi birden `overflow` kısaltmasında da yazılabilir. Tek bir değer iki yöne de gider.

Kısa bir notu dev bir kutu yapmak için `min-height` abartılmaz. Taban, bir kartın tek satırlık komşusuyla aynı hizada durması için kullanılır. Tavan, uzun bir notu saklamak için değil, kaydırılacak küçük bir alan için kullanılır.

## Sık yapılan hata

`content-box` dururken `width: 100%` ve iç boşluğu birlikte vermek, kutuyu pencerenin dışına iter.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Taşan yüzde</title>
    <style>
      body {
        margin: 0;
        background-color: #f4f1ea;
      }

      p {
        box-sizing: content-box;
        width: 100%;
        padding: 2rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }
    </style>
  </head>
  <body>
    <p>Van</p>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şerit pencerenin sağından taşar. Altta yatay bir kaydırma çubuğu çıkar. `%100` içeriğin genişliğidir. 2 rem sağ ve 2 rem sol iç boşluk bu yüzdenin üstüne biner. Toplam, pencereden geniştir.

Doğru hesap kenarlık kutusudur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sığan yüzde</title>
    <style>
      body {
        margin: 0;
        background-color: #f4f1ea;
      }

      p {
        box-sizing: border-box;
        width: 100%;
        padding: 2rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }
    </style>
  </head>
  <body>
    <p>Van</p>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şerit pencere genişliğinde biter. Yatay kaydırma çıkmaz. “Van” beyazdır ve şeridin kenarından 2 rem içeride durur.

## Egzersizler

1. Aynı 12 rem, aynı iç boşluk ve aynı yeşil kenarlıkla iki kutu kurun. Biri `content-box`, biri `border-box` olsun. Kenarlık kutusunun çizgiden çizgiye daha dar kaldığını görün.
2. Ana içeriği 32 rem yapın ve ortaya alın. `max-width: 100%` koyun. Pencereyi daraltın. Beyaz sütun sayfanın dışına taşmasın.
3. 3 rem yüksekliğinde bir kutuya uzun bir İzmir notu koyun. `overflow: auto` ile kaydırma çıksın. Metin kutunun altındaki başlığın üstüne binmesin.

[← Önceki gün](../09-box-model/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../11-border/ders.md)
