# 12. Gün — Görünüm (Display)

Bu gün, öğenin satırı nasıl dolduracağını değiştirir. Bir başlık varsayılan olarak `block` değerindedir. Kendinden sonra gelen parçayı alt satıra iter ve kutu yatayda uzar. Bir bağlantı varsayılan olarak `inline` değerindedir. Cümlenin içinde akar, genişlik ve yükseklik çoğu zaman onu büyütemez. `inline-block` akışta kalır ama kutu ölçülerini kabul eder. `none` öğeyi sayfadan çıkarır ve boşluğunu da kapatır.

## Blok alta iner, satır içi yanda kalır

Aynı listeyi yatay dizmek için maddeler satır içi kutu yapılabilir. Esnek kutu 16. günde daha düzgün bir satır kurar. Bugün `display` değerinin farkı görülür.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Blok ve satır</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      li {
        display: inline-block;
        margin-right: 1rem;
        padding: 0.4rem 0.8rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        border-radius: 0.5rem;
      }
    </style>
  </head>
  <body>
    <h1>Kentler</h1>
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
Dört kent alt alta değil, soldan sağa yan yana durur. Her kent beyaz bir kutu, yeşil bir çerçeve ve yuvarlak köşenin içindedir. Kutuların arasında yaklaşık 1 rem boşluk vardır. Madde işaretleri, satır içi kutunun yanında tarayıcıya göre hâlâ görünebilir ve hizayı bozabilir. İşareti kaldırmak 14. günün `list-style` özelliğidir. Bugün görülen asıl fark şudur: `inline-block` sayesinde `padding` ve `border` kutuyu büyütür ve kentler aynı satırda kalır.

`display: block` aynı maddelere verilirse her kent yeniden kendi satırına iner. Kutu, yazı kadar dar kalmaz. Satırın genişliğini ister. `display: inline` verilirse kenarlık görünür ama üst ve alt iç boşluk satır yüksekliğini beklenen gibi itemez. Genişlik yazılsa da satır içi öğe o genişliğe uymaz.

## none yerini de götürür

`display: none` öğeyi görünmez yapar ve sayfa düzeni onu hiç yokmuş gibi kapatır. Ardından gelen paragraf yukarı çıkar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Gizlenen not</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .gizli {
        display: none;
      }

      p {
        background-color: #ffffff;
        padding: 0.5rem;
        margin-top: 0.5rem;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
    <p class="gizli">Bu cümle kaynakta durur, sayfada yer kaplamaz.</p>
    <p>Göl geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” başlığının altında yalnızca “Göl geniştir.” beyaz kutusu vardır. “Bu cümle kaynakta durur…” satırı ekranda yoktur. Onun yerinde boş bir şerit de yoktur. Alttaki paragraf yukarı oturmuştur. Sayfa kaynağında gizli paragraf durur. `display: none`, bir notu herkesten saklamak için güvenli bir kasa değildir. Kaynak sayfayla birlikte gelir. Bu değer, o anda gösterilmeyecek bir parçanın yer kaplamaması içindir. Bağlantıyla açılıp kapanan bir kutu JavaScript ister. Bu repo JavaScript kullanmaz.

## Görünürlük (Visibility)

`visibility: hidden` öğeyi görünmez yapar. Yerini kapatmaz. Ardından gelen paragraf aşağıda, boşluğun altında kalır. `display: none` hem görünmez yapar hem boşluğu kapatır. İkisi de kaynağı sayfadan silmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Görünürlük</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      .gorunmez {
        visibility: hidden;
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
      }

      .yer {
        visibility: visible;
        background-color: #ffffff;
        padding: 1rem;
        margin-top: 0.5rem;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p class="gorunmez">Bu satır kaynakta durur, ekranda okunmaz, yer kaplar.</p>
    <p class="yer">Kıyı bu satırdadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” başlığının altında yeşil bir şerit görünmez. O şeridin yüksekliği kadar boş bir aralık vardır. “Kıyı bu satırdadır.” bu boşluğun altında, beyaz kutudadır. Gizli cümle başlığa yapışmaz. `display: none` olsaydı beyaz kutu başlığın hemen altına çıkardı. `visibility: hidden` bir satırı hizayı bozmadan gizlemek için durur. Okunacak bir notu gizlemek için kullanılmaz. Kaynakta durduğu için ekran okuyucu onu yine okuyabilir. `display: none` okuyucunun da atladığı bir çıkarmadır. İkisinin de parola saklamakla ilgisi yoktur.

## Sık yapılan hata

Satır içi bir bağlantıya `width` ve `height` verip düğme kadar büyümesini beklemektir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dar bağlantı</title>
    <style>
      a {
        width: 12rem;
        height: 3rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }
    </style>
  </head>
  <body>
    <p><a href="#van">Van notuna git</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van notuna git” yeşil bir zeminin üstünde beyazdır. Zemin, kelimenin boyu kadardır. 12 rem genişliğinde ve 3 rem yüksekliğinde bir düğme oluşmaz. Bağlantı satır içidir. Genişlik ve yükseklik onu şişirmez.

Doğru görünüm satır içi kutudur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Geniş bağlantı</title>
    <style>
      a {
        display: inline-block;
        width: 12rem;
        padding: 0.8rem;
        background-color: #0e4d5c;
        color: #ffffff;
        text-align: center;
        text-decoration: none;
        border-radius: 0.5rem;
      }
    </style>
  </head>
  <body>
    <p><a href="#van">Van notuna git</a></p>
    <h2 id="van">Van</h2>
  </body>
</html>
```

Tarayıcıda görünen:
Bağlantı yaklaşık 12 rem genişliğinde yeşil bir kutudur. Yazı beyazdır, altı çizili değildir ve kutunun içinde ortalanır. Köşeler yuvarlaktır. Tıklanınca sayfa “Van” başlığına kayar. Yükseklik sabitlenmeden, iç boşluk kutuyu yazının çevresinde büyütür. Metin uzarsa kutu alta doğru açılır. Sabit `height` ile taşan kelime kesilmez.

## Egzersizler

1. İstanbul, İzmir, Trabzon ve Van maddelerini yan yana, beyaz ve yeşil çerçeveli kutular olarak dizin. Her biri kendi satırına inmesin.
2. Aynı listeyi `display: block` yapın. Dört kent yeniden alt alta insin. Kutular satırın genişliğine yayılsın.
3. Bir bağlantıya 12 rem genişlik verin. Satır içi kaldığı sürece kutu kelime kadar dar dursun. `inline-block` yapınca yeşil zemin 12 reme çıksın ve yazı beyaz ortalansın.

[← Önceki gün](../11-border/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../13-pseudo-classes/ders.md)
