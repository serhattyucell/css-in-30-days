# 11. Gün — Kenarlık (Border)

Bu gün, kutunun çizgisini ve köşesini ayarlar. 9. günde `border: 2px solid #0e4d5c` hazır bir kısaltmaydı. Kısaltma üç şeyi birden taşır: kalınlık, biçim ve renk. Biçim yazılmazsa çizgi görünmez. `border-radius` köşeyi yuvarlar. Yuvarlak köşe, çerçevesiz bir kutuda da zeminin köşesini keser.

## Çizgi kalınlık, biçim ve renk ister

`solid` düz çizgi, `dashed` kesik çizgi, `dotted` nokta dizisidir. Dört kenar ayrı da yazılabilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kenarlık</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .duz {
        border: 3px solid #0e4d5c;
        padding: 1rem;
        background-color: #ffffff;
        margin-bottom: 1rem;
      }

      .kesik {
        border-width: 3px;
        border-style: dashed;
        border-color: #c47b00;
        padding: 1rem;
        background-color: #ffffff;
      }
    </style>
  </head>
  <body>
    <h1>İki çizgi</h1>
    <p class="duz">İstanbul notu düz yeşil bir çerçevededir.</p>
    <p class="kesik">Van notu kesik amber bir çerçevededir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Birinci paragrafın çevresinde kesintisiz, koyu deniz yeşili, yaklaşık 3 piksel bir çerçeve vardır. İçinde beyaz zemin ve 1 rem boşluk durur. İkinci paragrafın çevresi kesik kesik amberdir. Aynı kalınlıktadır, beyazdır ve yazısı çerçeveye yapışmaz. İki kutu arasında yaklaşık 1 rem kâğıt vardır.

Tek bir kenar, vurgunun yerini gösterir. Üst ve alt çizgi yazılmazsa kutu açık kalır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sol çizgi</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      blockquote {
        margin-left: 0;
        margin-right: 0;
        padding: 0.5rem 1rem;
        border-left: 4px solid #0e4d5c;
        background-color: #ffffff;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <blockquote>
      <p>Karadeniz kıyısı bu notta durur.</p>
    </blockquote>
  </body>
</html>
```

Tarayıcıda görünen:
Alıntı, tarayıcının varsayılan büyük girintisinden çıkar ve soldan başlar. Solunda 4 piksel kalınlığında düz yeşil bir çizgi vardır. Sağda, üstte ve altta çizgi yoktur. Yazı çizgiden 1 rem sağda, üstten ve alttan yarım rem içeride durur. Zemin beyazdır. Çevresi kâğıttır. Alıntının anlamı etiketindedir. Yeşil çizgi, o bloğu sayfada bulmayı kolaylaştırır.

## Köşe yuvarlanır

`border-radius` dört köşeyi birden yuvarlar. Değer büyüdükçe kavis artar. Kutu kareye yakınsa `%50` onu daireye yaklaştırır. Dikdörtgen bir paragrafta `%50` kapsül gibi uzun bir oval verir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Köşe</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      .kart {
        width: 16rem;
        padding: 1rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        border-radius: 0.75rem;
        color: #1e2430;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p class="kart">Saat Kulesi, yuvarlak köşeli bir kartın içindedir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz kartın dört köşesi keskin değildir. Her köşe yaklaşık 0.75 rem yarıçapla yuvarlanmıştır. Yeşil çizgi de aynı kavisi izler. Yazı köşeye taşmaz. Kart 16 rem genişliğinde soldan başlar. Sayfanın ortasında değildir. Ortaya almak için sol ve sağ `auto` kenar boşluğu ayrıca yazılır.

## Köşeler ayrı ayrı (Corner Radius)

`border-radius` dört sayı alırsa sıra yine saattir: sol üst, sağ üst, sağ alt, sol alt. `0` keskin köşe bırakır. Yatay ve dikey yarıçap ayrı da yazılabilir. Tek yüzde elli, kutuyu daireye yaklaştırır. Dikdörtgende kapsül olur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dört köşe</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .yuvarlak {
        width: 16rem;
        padding: 1rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        border-radius: 1.5rem 0 1.5rem 0;
      }
    </style>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p class="yuvarlak">Sol üst ve sağ alt yuvarlak, diğer iki köşe keskindir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz kartın sol üst köşesi ve sağ alt köşesi yaklaşık 1.5 rem kavislidir. Sağ üst ve sol alt köşeler keskin kalır. Yeşil çizgi kavisi izler. Yazı keskin köşeye taşmaz çünkü iç boşluk vardır. Dört köşe aynı sayı olsaydı kartın hepsi aynı kavisle dururdu. `border-radius: 1.5rem 0` iki değerdir. Birinci sol üst ve sağ alta, ikinci sağ üst ve sol alta gider. Çapraz köşeler eşlenir. Dört köşeyi tek tek kontrol etmek için dört sayı yazılır.

`border-top-left-radius` yalnız bir köşeyi adlandırır. Uzun ad, hangi köşenin değiştiğini tek başına söyler. Kısaltma, dört köşe birden kurulacaksa daha kısa olur.

## Sık yapılan hata

Biçimi yazmadan yalnızca kalınlık ve renk vermek, çizgiyi göstermez. Varsayılan biçim `none` değeridir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Görünmeyen çizgi</title>
    <style>
      p {
        border-width: 4px;
        border-color: #0e4d5c;
        padding: 1rem;
      }
    </style>
  </head>
  <body>
    <p>Van Gölü</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü” çevresinde yeşil bir çerçeve yoktur. Kalınlık ayrılmış olsa da biçim boştur. İç boşluk yazıyı kenardan içeri alır. Bu, çizgi varmış gibi bir genişlik bırakabilir. Çizginin rengi görünmez.

Doğru kısaltma üç parçayı birden taşır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Görünen çizgi</title>
    <style>
      p {
        border: 4px solid #0e4d5c;
        padding: 1rem;
        border-radius: 0.5rem;
      }
    </style>
  </head>
  <body>
    <p>Van Gölü</p>
  </body>
</html>
```

Tarayıcıda görünen:
Cümlenin çevresinde düz yeşil bir çerçeve vardır. Köşeler hafifçe yuvarlaktır. Yazı çerçeveden içeridedir.

İkinci hata, `border-radius` değerini kenarlık yokken “işe yaramadı” sanmaktır. Zemin de boyalı değilse yuvarlak köşe görünmez. Beyaz zemin ile kâğıt zemin aynı tondaysa kavis seçilmez. Zemin beyaz, sayfa kâğıt olunca köşe okunur.

## Egzersizler

1. Bir paragrafı 3 piksel düz yeşil çerçeve ile, diğerini 3 piksel kesik amber çerçeve ile gösterin. İkisinin de iç boşluğu olsun. Yazı çizgiye değmesin.
2. Bir alıntının yalnız sol kenarına 4 piksel yeşil çizgi koyun. Diğer üç kenarda çizgi görünmesin. Alıntı sayfanın büyük varsayılan girintisinde kalmasın.
3. Bir kartın köşelerini `0.75rem` yuvarlayın. Çerçeve ve beyaz zemin aynı kavisi izlesin. Biçimi silin. Çizgi kaybolsun. `solid` geri gelince çizgi de köşesiyle birlikte dönsün.

[← Önceki gün](../10-size/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../12-display/ders.md)
