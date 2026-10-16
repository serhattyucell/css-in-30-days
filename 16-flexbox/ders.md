# 16. Gün — Esnek kutu (Flexbox)

Bu gün, bir sıradaki kardeşleri esnek bir satıra dizer. 12. gündeki `inline-block` öğeleri yan yana koyuyordu ama aralık ve satır kaydırma dağınık kalıyordu. `display: flex` üst öğeye yazılır. Esneyen, çocuklardır. Üst öğe esnek kutu, çocuklar esnek öğe olur. `flex-direction` ana eksenin yatay mı dikey mi olacağını seçer. `gap` çocukların arasına boşluk koyar. Boşluk, kutunun dış kenarına eklenmez.

## Satır, üst öğede kurulur

Gezinti listesi esnek kutu olunca maddeler yatayda dizilir. `list-style` ve sol iç boşluk, işaret kalıntısını temizler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Esnek gezinti</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
        margin: 0;
      }

      header {
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
      }

      nav ul {
        display: flex;
        gap: 1rem;
        list-style: none;
        padding: 0;
        margin: 0.5rem 0 0;
      }

      nav a {
        color: #ffffff;
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
    <header>
      <h1>Serhat'ın kent notları</h1>
      <nav>
        <ul>
          <li><a href="#istanbul">İstanbul</a></li>
          <li><a href="#izmir">İzmir</a></li>
          <li><a href="#trabzon">Trabzon</a></li>
          <li><a href="#van">Van</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <h2 id="istanbul">İstanbul</h2>
      <p>Boğaz bu bölümde.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfanın üstü koyu deniz yeşili bir şerittir. “Serhat'ın kent notları” beyaz ve büyüktür. Altında İstanbul, İzmir, Trabzon ve Van yatay bir sırada, beyaz ve çizgisiz durur. Aralarında yaklaşık 1 rem boşluk vardır. Daire yoktur. Satır, şeridin solundan başlar. Bir ada Sekme ile gelinince amber çerçeve belirir. Şeridin altında kâğıt zemin ve “İstanbul” başlığı vardır. Esnek olan, `ul` listesidir. Her `li` o listenin çocuğudur. `display: flex` bir bağlantıya yazılırsa kardeşler esneyemez. Esneyen kutu, kardeşlerin babasıdır.

`flex-direction: column` aynı listeyi yeniden alt alta dizer. Boşluk, bu kez dikey aralıktır. Varsayılan `row` yatay sırayı kurar. Yazı sağdan sola dizilecekse ayrıca `row-reverse` vardır. Kent adlarının okunma sırası İstanbul’dan Van’a doğru olacağı için bu sayfada `row` kalır.

## Çocuklar aralığı paylaşır

`gap: 1rem` iki çocuk arasına 1 rem koyar. Üç aralık, üç boşluktur. Dört çocuğun arasında üç aralık vardır. Kenarlardaki 1 rem, şeridin kendi `padding` değerinden gelir. `gap` şeridin kenarına dış boşluk eklemez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Aralık</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      ul {
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        list-style: none;
        padding: 0;
      }

      li {
        background-color: #ffffff;
        border-left: 4px solid #0e4d5c;
        padding: 0.6rem 0.8rem;
      }
    </style>
  </head>
  <body>
    <h1>Duraklar</h1>
    <ul>
      <li>İstanbul</li>
      <li>Trabzon</li>
      <li>Van</li>
      <li>İzmir</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Dört beyaz satır alt altadır. Her satırın solunda 4 piksel yeşil çizgi vardır. Satırların arasında yaklaşık yarım rem kâğıt görünür. Bu aralık `margin` ile tek tek yazılmamıştır. Esnek kutunun `gap` değeridir. Son maddenin altında fazladan bir gap boşluğu birikmez. Boşluk yalnızca komşuların arasındadır.

## Sıra (Order)

`order` esnek çocuğun görünen sırasını değiştirir. HTML sırası kaynakta kalır. Varsayılan `order` değeri `0`dır. Daha küçük sayı sola, daha büyük sayı sağa gider. Aynı sayıdaki kardeşler kaynak sırasını korur. Klavye ve ekran okuyucu çoğu zaman HTML sırasını izler. Görünen sıra ile okunan sıra ayrılırsa kent listesi şaşırtır. Bu yüzden `order` bir numarayı gizlemek için değil, tek bir istisna için kullanılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Görünen sıra</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      ul {
        display: flex;
        gap: 1rem;
        list-style: none;
        padding: 0;
      }

      .son {
        order: 1;
      }
    </style>
  </head>
  <body>
    <h1>Sıra</h1>
    <ul>
      <li>İstanbul</li>
      <li class="son">Van</li>
      <li>İzmir</li>
      <li>Trabzon</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Soldan sağa “İstanbul”, “İzmir”, “Trabzon”, sonra “Van” durur. Kaynakta Van ikinci maddedir. `order: 1` onu, `order` değeri `0` olan kardeşlerin sağına iter. Aralarında 1 rem boşluk vardır. Madde işareti yoktur. Sekme tuşuyla gezinince odak, kaynaktaki sırayı izleyebilir: İstanbul, Van, İzmir, Trabzon. Göz ise Van’ı en sonda görür. Bu ayrım uzun bir gezintide yorar. Durakların okuma sırası HTML’de yazılır. `order` o sırayı süslemek için ters yüz etmez.

## Sık yapılan hata

`display: flex` değerini çocuklara yazmak, sırayı hiç kurmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yanlış kutu</title>
    <style>
      li {
        display: flex;
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
“İstanbul” ve “Van” alt alta, madde işaretleriyle durur. Her madde kendi içinde esnek kutudur. İçlerinde tek bir metin olduğu için yan yana dizilecek kardeş yoktur. Liste, esnek kutu olmadığı için maddeleri alt alta bırakır.

Doğru belgede esnek olan listedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Doğru kutu</title>
    <style>
      ul {
        display: flex;
        gap: 1rem;
        list-style: none;
        padding-left: 0;
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
İstanbul ve Van aynı satırda, aralarında 1 rem boşlukla, işaretsiz durur.

## Egzersizler

1. Yeşil bir üst şeritte beyaz bir başlık ve onun altında yatay dört kent bağlantısı görünsün. Daire olmasın. Aralık 1 rem olsun.
2. Aynı dört kenti `flex-direction: column` ile alt alta, solunda yeşil çizgi olan beyaz satırlar olarak dizin. Satırlar arasındaki boşluk yarım rem olsun ve son satırın altına aynı boşluk eklenmesin.
3. `display: flex` kuralını `li` üzerine alın. Kentler alt alta kalsın. Kuralı yeniden `ul` üzerine koyun. Kentler yan yana gelsin.

[← Önceki gün](../15-images/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../17-flex-alignment/ders.md)
