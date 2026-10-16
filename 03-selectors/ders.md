# 3. Gün — Seçiciler (Selectors)

Bu gün, kuralın hangi parçaya gideceğini daraltır. 2. günde `h1` ve `p` bütün başlıkları ve bütün paragrafları boyuyordu. Sayfada iki yeşil olunca hepsinin aynı olması gerekmez. Seçici, belgenin bir bölgesini işaret eder.

## Etiket seçicisi türün tamamını alır

Etiket seçicisi, o addaki her öğeye uygulanır. Virgül, aynı bildirimi birkaç türe birden verir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Etiket seçicisi</title>
    <style>
      h1,
      h2 {
        color: #0e4d5c;
      }

      p {
        color: #1e2430;
      }
    </style>
  </head>
  <body>
    <h1>Dört kent</h1>
    <h2>İstanbul</h2>
    <p>Boğaz kenti iki yakaya ayırır.</p>
    <h2>Van</h2>
    <p>Van Gölü geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Dört kent” en büyük başlıktır ve koyu deniz yeşilidir. “İstanbul” ile “Van” ondan küçüktür, yine aynı yeşildir. İki paragraf koyu mürekkep rengine yakındır, neredeyse siyahtır ama başlığın yeşili değildir. Virgül sayesinde yeşil kural bir kez yazılmıştır. İki başlık düzeyi onu paylaşır. Paragraf bu grupta yoktur.

Seçiciye küçüktür ve büyüktür işareti konmaz. CSS içinde `<h1>` yazılmaz. İşaretler HTML’dedir. Stil dosyasında ad, süssüz `h1` olarak durur.

## Boşluk, içindekini seçer

İki seçici arasına boşluk konursa ikinci seçici, birincinin içinde aranır. Buna alt öğe seçicisi denir. `nav a` yalnızca gezintinin içindeki bağlantıları seçer. Sayfadaki diğer bağlantılar dışarıda kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Alt öğe</title>
    <style>
      nav a {
        color: #0e4d5c;
      }

      p a {
        color: #0c5c8a;
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
    <p>
      Ayrıntı
      <a href="https://example.com">Example Domain</a>
      sayfasındadır.
    </p>
    <h2 id="istanbul">İstanbul</h2>
    <h2 id="van">Van</h2>
  </body>
</html>
```

Tarayıcıda görünen:
Listenin içindeki “İstanbul” ve “Van” bağlantıları koyu deniz yeşilidir ve tarayıcının alt çizgisini taşır. Paragrafın içindeki “Example Domain” başka bir mavidir, yine altı çizilidir. İkisi de `<a>` olduğu hâlde renkleri ayrıdır. `nav a` birinci grubu, `p a` ikinci grubu seçer. `a` tek başına yazılsaydı bütün bağlantılar aynı renge düşerdi.

Boşluk hiyerarşi kurar. `nav` ile `a` bitişik yazılırsa bu, `nava` adlı bir etiket aramak anlamına gelir. Böyle bir etiket olmadığı için kural hiç uygulanmaz.

## Çocuk, bir alt düzeyi seçer

`>` işareti, yalnız bir basamak içeri girer. Torunları almaz. `nav > a` gezintinin doğrudan çocuğu olan bağlantıyı seçer. Listenin içine gömülmüş bağlantıyı seçmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Çocuk seçici</title>
    <style>
      nav > a {
        color: #0e4d5c;
      }

      nav li a {
        color: #0c5c8a;
      }
    </style>
  </head>
  <body>
    <nav>
      <a href="#ust">Başa dön</a>
      <ul>
        <li><a href="#izmir">İzmir</a></li>
        <li><a href="#trabzon">Trabzon</a></li>
      </ul>
    </nav>
    <h2 id="ust">Üst</h2>
    <h2 id="izmir">İzmir</h2>
    <h2 id="trabzon">Trabzon</h2>
  </body>
</html>
```

Tarayıcıda görünen:
“Başa dön” koyu deniz yeşilidir. “İzmir” ve “Trabzon” bağlantı mavisindedir. Üçü de `<nav>` içindedir. Yeşil olan, gezintinin doğrudan çocuğudur. Mavi olanlar listenin içindedir. `nav a` yazılsaydı üçü de aynı kurala girerdi. `>` bu ikisini ayırır.

## Kardeş seçici (Sibling Selector)

`h2 + p` yalnızca bir başlığın hemen ardından gelen paragrafı seçer. Araya başka bir öğe girerse seçim olmaz. `h2 ~ p` ise aynı ebeveynde, başlıktan sonra gelen bütün paragrafları seçer. Çocuk seçici `>` aşağı iner. Kardeş seçici yan yana duran öğeler arasında kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kardeşler</title>
    <style>
      h2 + p {
        color: #0e4d5c;
        font-weight: 700;
      }

      h2 ~ p {
        background-color: #ffffff;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
    <p>Bu paragraf bir başlık ikinin önündedir.</p>
    <h2>Göl</h2>
    <p>Bu paragraf başlığın hemen ardındadır.</p>
    <p>Bu paragraf da başlıktan sonra gelir ama bitişik değildir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” siyah büyük başlıktır. Onun altındaki ilk paragraf da siyahtır ve beyaz zemin almaz. O paragraf `h2` etiketinden önce durduğu için iki kardeş seçici de onu almaz. “Göl” orta boy bir başlıktır. Hemen altındaki “Bu paragraf başlığın hemen ardındadır.” hem kalın hem koyu deniz yeşilidir hem de beyaz zemindedir. `+` onu kalın ve yeşil yapar. `~` onu beyaza boyar. Son paragraf beyaz zemindedir ama kalın ve yeşil değildir. `~` onu kapsar, `+` kapsamaz. Çünkü arada başka bir paragraf vardır.

Başlığın içindeki bir bağlantı kardeş değildir. O, çocuktur. `h2 + a` bir başlığın dışındaki bağlantıyı arar. Başlığın içindeki bağlantı `h2 a` veya `h2 > a` ile seçilir.

## Sık yapılan hata

Seçiciyi HTML etiketi gibi yazmak, kuralı yok saydırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İşaretli seçici</title>
    <style>
      <h1> {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” siyah kalır. Stil bölgesi, seçiciyi okuyamaz. Küçüktür işareti kuralın başını bozar. Sonraki özellik de uygulanmaz. Ekranda bir uyarı satırı çıkmayabilir. Sonuç, varsayılan siyah başlıktır.

Doğru seçici adın kendisidir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Düz seçici</title>
    <style>
      h1 {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” koyu deniz yeşilidir.

İkinci hata, boşluğu unutup `nav a` yerine `nava` yazmaktır. Gezinti içindeki bağlantı mavi varsayılanında kalır. Üçüncü hata, virgülün yerine boşluk koymaktır. `h1 h2` “başlık bir ve başlık iki” demek değildir. “Bir `h1` içindeki `h2`” demektir. Başlık iki, başlık birin içinde değilse kural hiçbir yere gitmez.

## Egzersizler

1. `h1` ve `h2` aynı koyu deniz yeşilini paylaşsın. Kural bir kez yazılsın. Paragraf koyu mürekkep renginde kalsın.
2. Gezintideki bağlantılar yeşil, paragrafın içindeki bağlantı mavi görünsün. İki bağlantı türü de `<a>` olsun. Renkleri ayrı kalsın.
3. Seçiciye bilerek `<h1>` yazın. Başlık siyah kalsın. İşaretleri kaldırın. Başlık yeşil olsun.

[← Önceki gün](../02-stylesheet/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../04-class-id/ders.md)
