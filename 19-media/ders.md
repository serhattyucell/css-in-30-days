# 19. Gün — Medya sorguları (Media Queries)

Bu gün, pencerenin genişliğine göre başka bir kural seçer. 18. günde iki sütun dar pencerede eziliyordu. `@media` bir koşuldur. Koşul doğruysa içindeki kurallar geçerli olur. Yanlışsa o blok yok sayılır. `max-width: 36rem` pencere bu genişlikte veya daha darsa anlamına gelir. Sorgunun içine, yalnızca değişen özellik yazılır. Ortak renk ve yazı tipi dışarıda, bir kez durur.

## Dar pencerede tek sütun

Geniş pencere iki sütun görür. Sorgu, dar pencerede sütun şablonunu `1fr` yapar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Daralan ızgara</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
        margin: 1rem;
      }

      ul {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1rem;
        list-style: none;
        padding: 0;
      }

      li {
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        border-radius: 0.5rem;
        padding: 1rem;
      }

      @media (max-width: 36rem) {
        ul {
          grid-template-columns: 1fr;
        }
      }
    </style>
  </head>
  <body>
    <h1>Dört kent</h1>
    <ul>
      <li>İstanbul</li>
      <li>İzmir</li>
      <li>Trabzon</li>
      <li>Van</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Pencere 36 remden genişken İstanbul ile İzmir yan yana, Trabzon ile Van alt satırda yan yanadır. Pencere daraltılınca veya telefon görünümü seçilince dört kent alt alta iner. Her kart satırın tamamını kaplar. Çerçeve, beyaz zemin ve 1 rem aralık aynı kalır. Yalnızca sütun sayısı değişir. Sayfa yenilenmeden, pencere sürüklendikçe iki hâl arasında geçilir.

36 rem, kök 16 piksel ise yaklaşık 576 pikseldir. Eşik, “bu cümle tek sütunda da okunur” diye seçilir. Çok büyük bir eşik, masaüstünde de tek sütun bırakır. Çok küçük bir eşik, dar pencerede iki sütunu tutmaya devam eder.

## Gezinti alt satıra iner

Aynı sorguda esnek satır da `column` olabilir. Üst şerit, dar ekranda başlığı ve bağlantıları alt alta dizer.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Daralan şerit</title>
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
        padding: 1rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }

      h1 {
        font-size: 1.3rem;
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

      @media (max-width: 36rem) {
        header {
          flex-direction: column;
          align-items: flex-start;
        }
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
  </body>
</html>
```

Tarayıcıda görünen:
Geniş pencerede “Kent notları” solda, bağlantılar sağda, ikisi de şeridin dikey ortasındadır. Pencere 36 rem ve altına inince başlık üstte, İzmir ve Van onun altında soldan başlar. Bağlantılar kendi aralarında yatay kalır çünkü `column` şeride verilmiştir, listenin kendisine değil. Şerit yeşil, yazılar beyazdır. Dar hâlinde sağa yapışık bir gezinti kalmaz. Parmakla tıklanacak satır, sola yaslı durur.

`min-width: 36rem` ters koşuldur. Pencere en az 36 rem ise içindeki kurallar geçer. İki yazım da doğrudur. Bu rehber ortak hali dar olmayan pencereye yazar, `max-width` ile daraltmayı üstüne ekler. Böylece tek sütun, ek kuraldır. Asıl kural, geniş sayfanın kuralıdır.

## İki koşul (Media Condition)

Koşullar `and` ile bağlanır. İkisi de doğruysa blok uygulanır. `min-width` en az şu kadar geniş demektir. `max-width` en çok şu kadar demektir. İkisi birlikte bir aralık kurar. Aralık, orta boy bir pencereye özel bir hizayı bırakmak içindir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Aralık koşulu</title>
    <style>
      body {
        margin: 0;
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      p {
        padding: 1rem;
        background-color: #ffffff;
      }

      @media (min-width: 30rem) and (max-width: 50rem) {
        p {
          background-color: #0e4d5c;
          color: #ffffff;
        }
      }
    </style>
  </head>
  <body>
    <p>İzmir. Zemin yalnız orta genişlikte yeşildir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Pencere 30 remden darsa paragraf beyaz ve koyu mürekkeptir. 30 rem ile 50 rem arasındaysa zemin koyu deniz yeşili, yazı beyaz olur. 50 remden genişse yeniden beyaz zemin ve koyu yazı gelir. Sayfa yenilenmez. Pencere sürüklenince üç hâl de görülür. `and` yerine virgül yazılırsa bu, “veya” anlamına gelir. `@media (max-width: 30rem), (min-width: 50rem)` dar veya çok geniş pencerede uygulanır, ortada uygulanmaz. Virgül ile `and` aynı koşul değildir.

Yazdırma için `@media print` vardır. Ekrandaki yeşil şerit kâğıtta mürekkep yer. Bu rehberin sayfaları ekran için yazılır. Baskı kuralı, ekran düzeninin kopyası olarak eklenmez.

## Sık yapılan hata

Sorgunun parantezini veya küme parantezini eksik bırakmak, yalnızca dar ekran kuralını değil, sonraki kuralları da düşürebilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kırık sorgu</title>
    <style>
      ul {
        display: grid;
        grid-template-columns: 1fr 1fr;
      }

      @media max-width: 36rem {
        ul {
          grid-template-columns: 1fr;
        }
      }
    </style>
  </head>
  <body>
    <ul>
      <li>İstanbul</li>
      <li>Van</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Pencere ne kadar daralırsa daralsın İstanbul ile Van çoğu zaman yan yana kalır. `@media` ile koşul arasında parantez yoktur. Sorgu okunmaz. İki sütun kuralı durduğu için ezilen satır sürer.

Doğru sorguda koşul parantez içindedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sağlam sorgu</title>
    <style>
      ul {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1rem;
        list-style: none;
        padding: 0;
      }

      @media (max-width: 36rem) {
        ul {
          grid-template-columns: 1fr;
        }
      }
    </style>
  </head>
  <body>
    <ul>
      <li>İstanbul</li>
      <li>Van</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Geniş pencerede iki kent yan yanadır. 36 rem ve altında alt alta inerler.

İkinci hata, rengi ve yazı tipini sorgunun içine kopyalayıp dışarıda bırakmamaktır. Dar ve geniş hâl bir yerde ayrışır. Ortak kural dışarıda yazılır. Sorgu yalnızca değişen satırı taşır.

## Egzersizler

1. Dört kent, geniş pencerede iki sütun, 36 rem ve altında tek sütun görünsün. Çerçeve ve aralık iki hâlde de aynı kalsın. Pencereyi sürükleyince sütun sayısı değişsin.
2. Yeşil şeritte başlık genişken solda, gezinti sağda dursun. Dar pencerede başlık üstte, bağlantılar altta soldan başlasın.
3. `@media` satırından parantezleri kaldırın. Daraltınca tek sütun oluşmasın. Parantezleri geri koyun. Tek sütun geri gelsin.

[← Önceki gün](../18-grid/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../20-forms/ders.md)
