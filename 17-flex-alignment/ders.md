# 17. Gün — Esnek hizalama (Flex Alignment)

Bu gün, esnek satırın içindeki boşluğu dağıtır. 16. günde çocuklar soldan, aralarında `gap` ile diziliyordu. `justify-content` ana eksendeki boşluğu dağıtır. Yatay satırda bu eksen soldan sağadır. `align-items` karşı ekseni kullanır. Yatay satırda karşı eksen yukarıdan aşağıdır. `flex-wrap` sığmayan çocuğu alt satıra indirir. `flex` çocuğun o satırda ne kadar büyüyebileceğini söyler.

## Ana eksen boşluğu dağıtır

`flex-start` sola yaslar. `center` grubu ortaya alır. `space-between` ilk çocuğu sola, son çocuğu sağa iter, aradaki boşluğu eşit böler. `space-between` ile `gap` birlikte kullanılırsa aralık en az gap kadar olur, fazlası dağılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dağıtılan boşluk</title>
    <style>
      body {
        margin: 0;
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 1rem;
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
      }

      h1 {
        font-size: 1.4rem;
        margin: 0;
      }

      nav ul {
        display: flex;
        gap: 1rem;
        list-style: none;
        margin: 0;
        padding: 0;
      }

      a {
        color: #ffffff;
        text-decoration: none;
      }

      a:focus {
        outline: 3px solid #c47b00;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Kent notları</h1>
      <nav>
        <ul>
          <li><a href="#izmir">İzmir</a></li>
          <li><a href="#van">Van</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <h2 id="izmir">İzmir</h2>
      <h2 id="van">Van</h2>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şerit tek satırdır. “Kent notları” solda, beyaz ve başlığın varsayılan dev puntosundan küçüktür. “İzmir” ve “Van” sağda, yan yana ve beyazdır. Başlık ile gezinti arasında boşluk vardır. İkisi şeridin dikey ortasındadır. Biri yukarı yapışık, öteki aşağı kayık durmaz. `align-items: center` bu dikey ortalamayı yapar. `justify-content: space-between` soldaki başlık ile sağdaki gezintiyi iki uca iter.

Yön `column` olursa ana eksen dikey olur. O zaman `justify-content` üst-alt boşluğunu, `align-items` sağ-sol hizasını yönetir. İki özelliğin adı değişmez. Değişen, eksenin hangi yöne baktığıdır.

## Satır kayınca pay paylaşılır

`flex: 1` çocuğun büyüyebileceğini söyler. Kardeşler aynı değeri taşırsa fazla genişliği eşit bölerler. `flex-wrap: wrap` sığmayan kartı alt satıra indirir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Paylaşılan kartlar</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      ul {
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
        list-style: none;
        padding: 0;
      }

      li {
        flex: 1;
        min-width: 10rem;
        padding: 1rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        border-radius: 0.5rem;
      }
    </style>
  </head>
  <body>
    <h1>Dört kart</h1>
    <ul>
      <li>İstanbul, Boğaz</li>
      <li>İzmir, körfez</li>
      <li>Trabzon, kıyı</li>
      <li>Van, göl</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Pencere genişken dört beyaz kart aynı satırda, eşit payla durur. Aralarında 1 rem boşluk vardır. Çerçeveler yeşil, köşeler yuvarlaktır. Madde işareti yoktur. Pencere daralınca 10 rem’den daha dar kalamayan kart alta iner. Alt satırdaki kartlar kalan genişliği yine paylaşır. Tek kart alta kalırsa satırın tamamına yayılabilir. `min-width`, kartın okunamaz inceliğe inmesini engeller.

`flex: 1` üç değerin kısaltmasıdır: büyüme, küçülme ve taban. Bu rehberde anlamı şöyledir. Kardeşlerle birlikte fazla yeri al, gerekirse küçül, tabanı içeriğin boyuna bırak. Her karta sabit 200 piksel yazmak da yan yana dizer. Pencere değişince boşluk kartların arasında toplanır veya taşma olur. `flex` fazla yeri kartlara verir.

## Tek çocuğun hizası (Align Self)

`align-self` bir esnek çocuğu, kardeşlerinden farklı hizalar. Kabın `align-items` değeri diğer çocuklarda kalır. `stretch` karşı eksende kutuyu uzatır. `flex-start` üste yaslar. `flex-end` alta yaslar. Yatay satırda karşı eksen dikeydir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek çocuk</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      ul {
        display: flex;
        align-items: stretch;
        gap: 1rem;
        list-style: none;
        padding: 0;
        height: 8rem;
        background-color: #e7e2d8;
      }

      li {
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        padding: 0.5rem 1rem;
      }

      .alta {
        align-self: flex-end;
      }
    </style>
  </head>
  <body>
    <h1>Kartlar</h1>
    <ul>
      <li>İstanbul</li>
      <li class="alta">Van</li>
      <li>İzmir</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Açık bej bir şerit 8 rem yüksektir. “İstanbul” ve “İzmir” beyaz kartları bu şeridin tepesinden altına kadar uzar. `stretch` yüksekliği doldurur. “Van” kartı şeridin altına yaslanır ve yalnızca yazısı kadar yüksektir. Üç kart yan yanadır, aralarında 1 rem vardır. Van, kardeşlerinin yüksekliğini almaz. `align-self: flex-end` yalnız onu ayırır.

`align-content` ise kaydırılmış satırların arasındaki dikey boşluğu yönetir. Tek satırda etkisi görünmez. `flex-wrap: wrap` ile iki satır oluşunca `space-between` satırları kabın üstüne ve altına iter. Tek çocuğun hizası `align-self`, satır kümesinin hizası `align-content` değeridir.

## Sık yapılan hata

Yatay satırda dikey ortalama için `justify-content: center` yazmaktır. O özellik grubu yatayda ortaya alır. Kutular yukarıya yapışık kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yanlış eksen</title>
    <style>
      header {
        display: flex;
        justify-content: center;
        height: 6rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Van</h1>
    </header>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şerit 6 rem yüksektir. “Van” şeridin yatay ortasındadır ve üst kenara yakındır. Dikey olarak şeridin ortasında değildir. Başlığın kendi kenar boşluğu onu bir parça aşağı iter. Şeridin alt yarısı boş kalır.

Doğru dikey ortalama karşı eksendedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Doğru eksen</title>
    <style>
      header {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 6rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }

      h1 {
        margin: 0;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Van</h1>
    </header>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” hem yatayda hem dikeyde yeşil şeridin ortasındadır. Alt yarısı boş bir bant gibi durmaz.

## Egzersizler

1. Üst şeritte başlık solda, iki bağlantı sağda dursun. İkisi de şeridin dikey ortasında hizalansın. Bağlantılar beyaz olsun.
2. Dört kent kartı eşit pay alsın. Pencereyi daraltın. Kartlar 10 remden ince bir sütuna ezilmeden alt satıra insin. Aralarındaki boşluk 1 rem kalsın.
3. Yalnızca `justify-content: center` ile 6 rem’lik şeritte başlığı ortaya alın. Başlık yukarıda kalsın. `align-items: center` ekleyince başlık şeridin dikey ortasına insin.

[← Önceki gün](../16-flexbox/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../18-grid/ders.md)
