# 21. Gün — Konum (Position)

Bu gün, bir öğeyi akıştaki yerinden bilerek ayırır. Ondan önceki günlerde kutu, kardeşlerinin arasında kendi sırasında duruyordu. `position: relative` öğeyi yerinde bırakır ve gerekirse oradan biraz kaydırır. Kaydırdığı yer boş kalmaz. `position: absolute` öğeyi akıştan çıkarır. Yerini kapatır. Konumu, `relative` olan en yakın üst öğeye göre hesaplanır. Böyle bir üst yoksa sayfaya göre durur. `top`, `right`, `bottom` ve `left` kaymanın yönünü verir. `z-index` üst üste binenlerin hangisinin önde duracağını sayar. Konumlanmamış sıradan bir paragrafta `z-index` sırayı değiştirmez.

## Rozet, figürün köşesine oturur

Rozet, figürün içinde köşeye alınacaksa figür `relative` olur. Rozet `absolute` olur. `top` ve `right` figürün iç kenarından ölçülür.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Köşe rozeti</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      figure {
        position: relative;
        margin: 0;
        max-width: 24rem;
      }

      img {
        max-width: 100%;
        height: auto;
        border-radius: 0.5rem;
        background-color: #e7e2d8;
      }

      .rozet {
        position: absolute;
        top: 0.5rem;
        right: 0.5rem;
        margin: 0;
        padding: 0.3rem 0.6rem;
        background-color: #0e4d5c;
        color: #ffffff;
        border-radius: 0.4rem;
        font-size: 0.875rem;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
    <figure>
      <img src="van-golu.jpg" alt="Van Gölü kıyısı" />
      <p class="rozet">Van</p>
      <figcaption>Van Gölü, kente kıyıdan bakılınca.</figcaption>
    </figure>
  </body>
</html>
```

Tarayıcıda görünen:
Fotoğraf varsa yuvarlak köşeli bir görsel, yoksa bej bir kutu ve “Van Gölü kıyısı” yazısı durur. Kutunun sağ üst köşesine yakın, yeşil zeminde beyaz “Van” rozeti oturur. Rozet, alt yazının üstünde ayrı bir satır olarak figürün altında belirmez. Fotoğrafın üstündedir. Alt yazı görselin altında, soluk bir satır olarak kendi akışında kalır. Rozet yer kaplamadığı için alt yazıyı aşağı itmez. `top` ve `right` figüre göredir. Figürdeki `position: relative` silinirse rozet sayfanın sağ üstüne kayabilir. Üst öğe konumlu olmadığı için hesap sayfaya düşer.

## relative yerini korur

Göreli kaydırma, öğeyi görünür yerinden oynatır ama kardeşler eski boşluğa göre dizilmeye devam eder.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Göreli kayış</title>
    <style>
      body {
        font-family: Arial, Helvetica, sans-serif;
        background-color: #f4f1ea;
      }

      .kayik {
        position: relative;
        top: 0.5rem;
        left: 1rem;
        background-color: #ffffff;
        padding: 0.5rem;
      }
    </style>
  </head>
  <body>
    <p>İstanbul</p>
    <p class="kayik">İzmir</p>
    <p>Trabzon</p>
  </body>
</html>
```

Tarayıcıda görünen:
“İstanbul” solda başlar. “İzmir” beyaz bir kutu içinde, kendi sırasının yaklaşık yarım rem altında ve 1 rem sağındadır. “Trabzon”, İzmir hiç kaymamış gibi İzmir’in eski yerinin altındadır. Kaymış kutu Trabzon’un üzerine binebilir. Göreli konum, boşluğu kapatmaz. Bir notu hafifçe kaydırmak için kullanılır. Sayfanın köşesine sabitlemek için kullanılmaz.

`z-index` burada gerekir çünkü İzmir, Trabzon’un üstüne biner. Büyük sayı öne gelir. İkisi de konumlanmış olmalıdır. Esnek kutu veya ızgara çocuğu da `z-index` kabul eder. Sıradan, `position` değeri `static` olan bir paragraf kabul etmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Önde duran kutu</title>
    <style>
      body {
        font-family: Arial, Helvetica, sans-serif;
      }

      .alt {
        position: relative;
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
      }

      .ust {
        position: relative;
        z-index: 1;
        margin-top: -1rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
        padding: 1rem;
      }
    </style>
  </head>
  <body>
    <p class="alt">Van</p>
    <p class="ust">Göl geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil “Van” şeridinin alt kısmının üstüne beyaz “Göl geniştir.” kutusu biner. Beyaz kutu öndedir. Yazısı yeşilin altında kaybolmaz. `z-index: 1` beyaz kutuyu öne alır. Negatif üst kenar boşluğu onu yukarı çeker. `z-index` silinirse kaynak sırası geçerlidir. Sonra gelen beyaz kutu çoğu zaman yine öndedir. Sayı, sıra yetmediğinde hangi kutunun önde kalacağını açıkça söyler.

## Yapışkan konum (Sticky)

`position: sticky` öğeyi akışta tutar. Kaydırma, öğenin `top` değerine gelince onu görünür alanın o hizasında bırakır. Üst öğe bitince yapışkan öğe de gider. `fixed` ise sayfa kayınca da pencereye yapışık kalır. Üst öğenin sonu onu bırakmaz. Uzun bir notta ara başlık `sticky` ile bölümün içinde kalır. Bütün site şeridi `fixed` yapılırsa gövde, şeridin altında kalmasın diye üstten iç boşluk ister.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yapışkan başlık</title>
    <style>
      body {
        margin: 0;
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      h2 {
        position: sticky;
        top: 0;
        margin: 0;
        padding: 0.6rem 1rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }

      p {
        margin: 0;
        padding: 1rem;
        min-height: 40vh;
      }
    </style>
  </head>
  <body>
    <h2>İstanbul</h2>
    <p>Boğaz bölümü uzundur. Sayfa kaydırılınca bu başlık bir süre üstte kalır.</p>
    <h2>Van</h2>
    <p>Göl bölümü başlayınca İstanbul başlığı yukarı çıkar, Van başlığı üste yapışır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfa açılınca “İstanbul” yeşil bir şerit ve beyaz yazıdır. Altındaki paragraf en az pencerenin yüzde 40’ı kadardır. Sayfa aşağı kaydırılınca İstanbul şeridi pencerenin tepesine yapışır. Kaydırma Van bölümüne gelince Van şeridi İstanbul’un yerine geçer. İstanbul yukarı doğru kaybolur. İki başlık pencerenin tepesinde üst üste birikmez. Her biri kendi bölümünün akışındadır. `top: 0` yapışmanın pencerenin en üstünde olacağını söyler. `top: 1rem` denirse şerit tepeden 1 rem aşağıda durur.

`position: fixed` aynı şeridi sayfanın tepesine kilitler ve ikinci başlık gelince de bırakmaz. Gövde metni şeridin altından kayar. Yapışkan başlık, bölüm bitince görevi bırakır. Sabit şerit, site gezintisi her zaman görünsün diye kullanılır. Bu notta bölüm başlığı yapışkandır.

## Sık yapılan hata

`absolute` bir rozeti `relative` olmayan bir sayfada köşeye koymak, onu fotoğrafa değil tarayıcının sayfasına yapıştırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sayfaya kaçan rozet</title>
    <style>
      .rozet {
        position: absolute;
        top: 0;
        right: 0;
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 0.4rem;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p class="rozet">İzmir</p>
    <p>Saat Kulesi altta kalır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil “İzmir” rozeti belgenin sağ üst köşesine gider. Başlığın yanında, kule notunun üstünde durması gerekirken sayfanın tepesine yapışır. Başlık ile “Saat Kulesi altta kalır.” birbirine yaklaşır çünkü rozet akışta yer tutmaz.

Doğru belgede rozetin babası konumlanır ve ölçü, o babadan alınır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Babaya bağlı rozet</title>
    <style>
      article {
        position: relative;
        max-width: 20rem;
        padding: 1rem;
        background-color: #ffffff;
        border: 2px solid #0e4d5c;
      }

      .rozet {
        position: absolute;
        top: 0.4rem;
        right: 0.4rem;
        margin: 0;
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 0.2rem 0.5rem;
      }
    </style>
  </head>
  <body>
    <article>
      <h1>İzmir</h1>
      <p class="rozet">35</p>
      <p>Saat Kulesi bu kartın içindedir.</p>
    </article>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz kartın sağ üstünde yeşil “35” rozeti durur. “İzmir” başlığı kartın içindedir. Rozet sayfanın tepesine kaçmaz. 35, İzmir’in plaka kodudur ve kartın köşesinde okunur.

## Egzersizler

1. Bir figürün sağ üstüne yeşil “Van” rozeti koyun. Rozet fotoğrafın üstünde dursun. Alt yazı fotoğrafın altında kalsın. Figürdeki `relative` silinince rozetin sayfanın köşesine gittiğini görün. `relative` geri gelince rozet yeniden fotoğrafa otursun.
2. “İzmir” paragrafını `relative` ile biraz sağa ve aşağı kaydırın. Alttaki “Trabzon” eski yerinden kımıldamasın. Kaymış kutu gerekirse Trabzon’un üzerine binsin.
3. Üst üste binen iki kutuda beyaz olanın `z-index` değeri önde dursun. `z-index` satırını konumsuz bir paragrafa taşıyın. Sıranın değişmediğini görün.

[← Önceki gün](../20-forms/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../22-cascade/ders.md)
