# 14. Gün — Liste ve tablo (Lists and Tables)

Bu gün, madde işaretini ve tablo çizgisini CSS ile düzenler. HTML, sırayı ve hücreyi kurmuştu. İşaretin türü, listenin sol boşluğu ve tablonun çift çizgisi tarayıcının varsayılanındaydı. `list-style` işareti seçer veya kaldırır. `border-collapse` hücre çizgilerini tek hatta birleştirir. `tbody tr:nth-child(even)` çift satırlara zemin verir. Bu sözde sınıf, 13. gündeki bağlantı durumundan ayrıdır. Sıra numarasını sayar.

## İşaret kalkınca satır içeriye çekilir

`list-style: none` hem daireyi hem numarayı kaldırır. Tarayıcı listenin soluna bir iç boşluk bırakmış olabilir. O boşluk da sıfırlanmazsa maddeler sağa kayık durur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İşaretsiz liste</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      nav ul {
        list-style: none;
        padding-left: 0;
        margin: 0;
      }

      nav li {
        display: inline-block;
        margin-right: 0.8rem;
      }

      nav a {
        color: #0e4d5c;
        text-decoration: none;
      }

      nav a:hover,
      nav a:focus {
        text-decoration: underline;
        outline: 3px solid #c47b00;
      }
    </style>
  </head>
  <body>
    <nav>
      <ul>
        <li><a href="#istanbul">İstanbul</a></li>
        <li><a href="#van">Van</a></li>
      </ul>
    </nav>
    <h2 id="istanbul">İstanbul</h2>
    <h2 id="van">Van</h2>
  </body>
</html>
```

Tarayıcıda görünen:
“İstanbul” ve “Van” soldan başlar. Önlerinde daire veya numara yoktur. İkisi yan yanadır. Yazılar koyu deniz yeşilidir ve altı çizili değildir. Birinin üzerine gelince alt çizgi gelir. Sekme ile odaklanınca amber çerçeve belirir. `padding-left: 0` olmasaydı yeşil adlar, görünmez bir işaretin boşluğu kadar sağda dururdu.

Numaranın kalması istenen durak listesinde `list-style: decimal` açıkça yazılır. İç listedeki daire `list-style: disc` olarak kalır. İkisi aynı sayfada ayrı seçicilerle durur.

## Tablo çizgisi tek hat olur

Hücrelere ayrı `border` verilince varsayılan `border-collapse: separate` iki komşu çizgiyi yan yana bırakır. Çizgi çift görünür. `collapse` komşu çizgileri birleştirir. Hücre iç boşluğu yazıyı çizgiden uzak tutar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek çizgi</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      table {
        border-collapse: collapse;
        width: 100%;
        max-width: 28rem;
        background-color: #ffffff;
      }

      caption {
        text-align: left;
        font-weight: 700;
        color: #0e4d5c;
        margin-bottom: 0.5rem;
      }

      th,
      td {
        border: 1px solid #cfc8bc;
        padding: 0.5rem 0.75rem;
        text-align: left;
      }

      th {
        background-color: #0e4d5c;
        color: #ffffff;
      }

      tbody tr:nth-child(even) {
        background-color: #e7e2d8;
      }
    </style>
  </head>
  <body>
    <table>
      <caption>Plakalar</caption>
      <thead>
        <tr>
          <th scope="col">Kent</th>
          <th scope="col">Plaka</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">İstanbul</th>
          <td>34</td>
        </tr>
        <tr>
          <th scope="row">İzmir</th>
          <td>35</td>
        </tr>
        <tr>
          <th scope="row">Trabzon</th>
          <td>61</td>
        </tr>
        <tr>
          <th scope="row">Van</th>
          <td>65</td>
        </tr>
      </tbody>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
“Plakalar” tablonun üstünde, sola yaslı, kalın ve koyu deniz yeşilidir. Sütun başlıkları “Kent” ve “Plaka” beyaz yazıyla yeşil bir zemindedir. İstanbul satırının zemini beyazdır. İzmir satırı açık bejdir. Trabzon beyaz, Van bej olarak sıra sıra iner. 34, 35, 61 ve 65 kendi kentinin sağında durur. Hücrelerin arasında tek bir açık bej-gri çizgi vardır. Çift çerçeve görünmez. Yazılar çizgiye yapışmaz. Tablo en çok 28 rem genişler, dar pencerede `%100` ile sayfaya sığar.

`nth-child(even)` gövdedeki satırları sayar. Başlık satırı bu sayının içinde değildir çünkü o, `thead` içindedir. Çift olan İzmir ve Van bejdir. Birinci ve üçüncü satır beyaz kalır. Anlam yine tablonun başlık hücrelerindedir. Bej zemin, satırı gözle izlemeyi kolaylaştırır. Yalnızca beje güvenilmez. Çizgi ve başlık da durur.

## İşaretin yeri (List Style Position)

`list-style-position: outside` işareti kutunun dışında, sol boşlukta tutar. Varsayılan budur. `inside` işareti ilk satırın içine alır. Çok satırlı bir madde, ikinci satırda işaretin altından değil, kutunun sol kenarından devam eder. `outside` iken ikinci satır, birinci satırın metniyle hizalanır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İşaretin yeri</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .dis {
        list-style-position: outside;
        max-width: 18rem;
      }

      .ic {
        list-style-position: inside;
        max-width: 18rem;
      }

      li {
        background-color: #ffffff;
        margin-bottom: 0.5rem;
      }
    </style>
  </head>
  <body>
    <h1>Notlar</h1>
    <ul class="dis">
      <li>İstanbul notu uzayınca ikinci satır, birinci satırın harfleriyle hizalanır.</li>
    </ul>
    <ul class="ic">
      <li>Van notu uzayınca ikinci satır, dairenin altına kayar.</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
İki madde de beyaz zemindedir ve en çok 18 remdir. Birincide daire, beyaz kutunun solunda, kutunun dışında durur. Cümle alt satıra inince ikinci satır dairenin hizasından değil, ilk harfin hizasından başlar. İkincide daire beyaz kutunun içindedir. İkinci satır kutunun sol kenarından, dairenin altından başlar. Daire ile metin aynı blokun içindedir. Gezintide işaret zaten `none` yapıldığı için konumun önemi kalmaz. Uzun bir durak cümlesinde `outside` daha düz bir sol kenar verir.

## Sık yapılan hata

`border-collapse` yazmadan her hücreye kalın kenarlık vermek, ızgarayı çift çizgiyle kalınlaştırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Çift çizgi</title>
    <style>
      th,
      td {
        border: 3px solid #0e4d5c;
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
“Van” ile “65” arasında iki yeşil çizgi yan yana durur. Hücrelerin dış çevresi de ayrı ayrı kalındır. Izgara, tek bir ızgara gibi okunmaz. Yazı çizgiye yakındır çünkü iç boşluk da yoktur.

Doğru tabloda birleşme ve iç boşluk vardır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek hat</title>
    <style>
      table {
        border-collapse: collapse;
      }

      th,
      td {
        border: 1px solid #0e4d5c;
        padding: 0.5rem;
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
Van ile 65 arasında tek yeşil çizgi vardır. Yazılar çizgiden içeridedir.

İkinci hata, `list-style: none` deyip `padding-left` değerini bırakmaktır. Daire kaybolur, boşluk kalır. Gezinti sayfanın solundan içeride başlar. Üçüncü hata, `tr:nth-child(even)` seçicisini `table` üzerinden, başlık satırını da sayacak biçimde kullanmaktır. Gövdeye indirmek, renklerin veri satırlarında kalmasını sağlar.

## Egzersizler

1. Bir gezintide İstanbul ve Van yan yana, işaretsiz ve soldan başlayarak dursun. Üzerine gelince alt çizgi gelsin.
2. Dört kentlik plaka tablosunda çizgiler tek hat olsun. Başlık satırı yeşil zemin ve beyaz yazı taşısın. İzmir ve Van satırları açık bej, İstanbul ve Trabzon beyaz görünsün.
3. `border-collapse` satırını silin. Çift çizgiyi görün. Satırı geri koyun. Van ile 65 arasında tek çizgi kalsın.

[← Önceki gün](../13-pseudo-classes/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../15-images/ders.md)
