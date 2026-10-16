# 6. Gün — Yazı tipi (Fonts)

Bu gün, harfin ailesini, boyutunu, kalınlığını ve satır aralığını ayarlar. 5. günde renk değişmişti. Punto hâlâ tarayıcının varsayılanındaydı. `font-family` aileyi, `font-size` boyutu, `font-weight` kalınlığı, `font-style` yatıklığı, `line-height` satırlar arasındaki boşluğu seçer. HTML’deki `<strong>` önem taşımaya devam eder. CSS onun görünüşünü değiştirebilir. Anlam etiketinde kalır.

## Aile ve boyut

Yazı tipi adı, bilgisayarda yüklü bir aileyi ister. Ad bulunamazsa tarayıcı listedeki sonraki ada geçer. Listenin sonunda genel bir aile durur: `sans-serif` veya `serif`.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yazı tipi</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 18px;
      }

      h1 {
        font-family: Georgia, "Times New Roman", serif;
        font-size: 36px;
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p>Boğaz kenti iki yakaya ayırır. Bu paragraf gövdenin ailesini kullanır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Zemin açık kâğıttır. “İstanbul” büyük bir başlıktır, koyu deniz yeşilidir ve tırnaklı (serif) bir aileyle durur. Paragraf daha küçüktür, tırnaksız (sans-serif) bir aileyle ve koyu mürekkeple durur. 18 piksel, gövdenin boyutudur. 36 piksel, başlığın boyutudur. Başlık, gövdenin ailesini kırar çünkü kendi `font-family` değeri vardır. Paragraf gövdeden aileyi ve boyutu miras alır. Mirasın kuralı 22. günde toplanır. Bugün görülen sonuç şudur: gövdeye yazılan aile, ayrıca kural almayan paragrafa da iner.

Birden çok kelimeli ad tırnak içinde yazılır. `"Times New Roman"` böyledir. `Arial` tek kelimedir, tırnaksız da durabilir. Listede bulunmayan süslü bir adın tek başına yazılması, tarayıcıyı varsayılan aileye düşürür. Sonunda `sans-serif` durursa düşüş tırnaksız bir aileye olur. Sayfa, boş bir yazı tipi yüzünden okunmaz hâle gelmez.

## Kalınlık, yatıklık ve satır aralığı

`font-weight` 400 civarı normal, 700 civarı kalındır. `font-style: italic` harfi yatırır. `line-height` bir satırın yüksekliğini büyütür. Uzun paragraf 1.5 ile daha rahat okunur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Satır aralığı</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 18px;
        line-height: 1.5;
      }

      h1 {
        color: #0e4d5c;
        font-size: 36px;
        line-height: 1.2;
      }

      .uyari {
        font-weight: 700;
      }

      em {
        font-style: italic;
      }
    </style>
  </head>
  <body>
    <h1>Van Gölü</h1>
    <p class="uyari">Tekne saatine rüzgârdan önce bakılır.</p>
    <p>Göl geniş, kıyı uzaktır. <em>Sabah</em> ışığı doğu kıyısından gelir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü” büyük, yeşil ve satır aralığı gövdeden daha sık bir başlıktır. “Tekne saatine rüzgârdan önce bakılır.” tümüyle kalındır. Kalınlık paragrafa sınıftan gelir. Cümle `<strong>` içinde değildir. Görünüş kalındır. Anlam, HTML’de ayrıca işaretlenmiş bir önem taşımaz. Son paragrafta yalnızca “Sabah” italiktir. Gövdenin satır yüksekliği 1.5 olduğu için iki satıra taşan cümlelerde satırlar birbirine yapışmaz. Başlık tek satırda kaldığı için 1.2 değeri kolay fark edilmeyebilir. Başlık çok uzun yazılırsa satırlar 1.5’ten daha yakın durur.

`line-height: 1.5` birim almaz. Boyutun 1.5 katıdır. `24px` de yazılabilir. Oran, punto sonradan değişince de orantıyı korur. `<em>` zaten varsayılan olarak italiktir. Kural, bu varsayılanı açıkça tekrarlar. `font-style: normal` denirse `<em>` italik olmaktan çıkar. Anlam kaynakta kalır, görünüş düzleşir. Bu rehberde vurgu italik bırakılır.

## Kısaltma (Shorthand)

`font` kısaltması, stil, kalınlık, boyut, satır yüksekliği ve aileyi tek bildirimde toplar. Sıra bozulursa bildirim yok sayılır. Boyut ile aile zorunludur. Aile en sonda durur. Satır yüksekliği boyutun yanında, eğik çizgiden sonra yazılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yazı kısaltması</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font: 18px/1.6 Arial, Helvetica, sans-serif;
      }

      h1 {
        color: #0e4d5c;
        font: 700 36px/1.2 Georgia, "Times New Roman", serif;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>Kıyı notu 18 piksel, 1.6 satır aralığı ve tırnaksız bir aileyle durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” 36 piksel, kalın, 1.2 satır aralığında ve tırnaklı bir ailededir. Rengi koyu deniz yeşilidir. `font` kısaltması rengi değiştirmez. Renk ayrı bir bildirimdir. Paragraf 18 pikseldir, satırları ferahdır ve tırnaksızdır. Kısa bir satır tek satırda kaldığı için 1.6 değeri, cümle alt satıra düşünce ayırt edilir.

Kısaltma, yazılmayan alt özellikleri ilk değerine döndürebilir. Gövdeye önce `font-weight: 700` verilip sonra `font: 18px/1.6 Arial, sans-serif` yazılırsa kalınlık normal ağırlığa döner. Kısaltma kalınlığı bildirmediyse kalınlık mirası değil, özelliğin ilk değeri geçerli olur. Bu yüzden kısaltmadan sonra gelen ayrı bir `font-weight` satırı, kalınlığı yeniden kurmanın güvenli yeridir. Uzun haller, hangi parçanın değiştiğini daha kolay gösterir. Kısaltma, bütün yazı ayarı bir kez kurulacaksa kullanılır.

## Sık yapılan hata

Boşluklu yazı tipi adını tırnaksız yazmak, aileyi iki ayrı ada böler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kırık aile</title>
    <style>
      body {
        font-family: Times New Roman, serif;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Saat Kulesi bu paragraftadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Kural çoğu tarayıcıda geçersiz sayılır. “Times” bir ad, “New” başka bir ad gibi okunur. Sayfa, tırnaklı Times ailesine geçmez. Tarayıcının varsayılan ailesi kalır. Bildirim yok sayıldığı için `serif` yedeği de işlemez. Bütün liste düşer.

Doğru listede boşluklu ad tırnak içindedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sağlam aile</title>
    <style>
      body {
        font-family: Georgia, "Times New Roman", serif;
        font-size: 18px;
        line-height: 1.5;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Saat Kulesi bu paragraftadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Başlık ve paragraf tırnaklı bir aileyle durur. Georgia yüklüyse Georgia görünür. Değilse Times New Roman, o da yoksa genel serif ailesi gelir. Boyut 18 piksel, satır aralığı rahattır.

İkinci hata, `font-weight: bold` ile `font-style: bold` karıştırmaktır. Kalınlık `font-weight` özelliğindedir. `font-style` italik ve normal bilir. `font-style: bold` yok sayılır. Harf kalınlaşmaz.

## Egzersizler

1. Gövde Arial ailesinde, 18 piksel ve 1.5 satır aralığında dursun. “Van Gölü” 36 piksel ve Georgia ailesinde, koyu deniz yeşili görünsün. Paragraf gövdenin ailesini kullansın.
2. Bir paragrafın tamamı kalın olsun. Aynı sayfada bir kelime italik kalsın. Kalın paragraf bir başlık kadar büyük olmasın.
3. `"Times New Roman"` adının tırnaklarını kaldırın. Aile değişmezse veya varsayılana düşerse tırnağı geri koyun. Tırnaklı aile yeniden görünsün.

[← Önceki gün](../05-color/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../07-text/ders.md)
