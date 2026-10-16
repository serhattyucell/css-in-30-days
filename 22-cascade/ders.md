# 22. Gün — Kademe ve özgüllük (Cascade and Specificity)

Bu gün, aynı öğeye iki kural birden değince hangisinin kalacağını söyler. Önceki günlerde bir renk bazen yazılmadan değişiyordu. Kaynak sırası, özgüllük ve önem ayrı terazilerdir. Aynı özgüllükte alttaki kural kazanır. Sınıf, etiket seçicisinden baskındır. Kimlik, sınıftan baskındır. HTML’deki `style` özelliği, normal bir stil dosyası kuralından baskındır. `!important` bu sırayı bozar ve sonraki düzeltmeyi zorlaştırır. Yorum, `/*` ile `*/` arasında durur ve sayfada görünmez.

## Alttaki eşit kural kazanır

İki `p` kuralı aynı seçicidir. Tarayıcı ikisini de okur. Aynı özellik için sonuncuyu tutar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kaynak sırası</title>
    <style>
      p {
        color: #0c5c8a;
      }

      p {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <p>Trabzon kıyısı.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon kıyısı.” koyu deniz yeşilidir. Mavi kural kaynakta durur ama aynı özellik yeniden yazıldığı için yeşil onu ezer. İki renk karışmaz. Bir özellik ya bir değerde ya diğerindedir.

Yorum, rengin neden değiştiğini kaynakta tutar ve ekrana çıkmaz:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yorum</title>
    <style>
      /* Deniz yeşili, sayfanın başlık rengidir. */
      h1 {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Van</h1>
    <p>Göl geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” yeşil bir başlıktır. “Deniz yeşili…” cümlesi ekranda yoktur. Paragraf siyahtır. Yorumun içinde bir kural yazılırsa o kural da uygulanmaz. Not, stili kapatmaz. Yalnızca kaynağı okuyan kişiye kalır. `//` CSS’te yorum değildir. O satır bildirimi bozabilir.

## Sınıf etiketi, kimlik sınıfı yener

Özgüllük bir puan gibi düşünülür. Etiket seçici bir puan, sınıf on puan, kimlik yüz puan değildir ama daha baskındır. Sayı tam olarak şöyle okunur: kimlik sayısı, sınıf sayısı, etiket sayısı. `#vana` bir kimliktir. `.not` bir sınıftır. `p` bir etikettir. Kimlik, sınıftan büyüktür. Sınıf, etiketten büyüktür. Kaynakta etiket alttaysa bile sınıf kazanır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Özgüllük</title>
    <style>
      #vana {
        color: #0e4d5c;
      }

      .not {
        color: #5c4575;
      }

      p {
        color: #0c5c8a;
      }
    </style>
  </head>
  <body>
    <p id="vana" class="not">Van Gölü geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü geniştir.” koyu deniz yeşilidir. Paragraf hem `p` hem `not` hem `vana` taşır. Mavi etiket kuralı en alttadır. Yine de yeşil kimlik kazanır. Mor sınıf, mavi etiketi yenerdi. Kimlik sınıfı da yener. HTML’de `style="color: #c47b00"` yazılırsa bu satır içi bildirim, normal stil dosyasındaki kimliği de geçer. Renk amber olur. Satır içi stil, tek bir öğeyi dosyadan koparır. Tekrar edecek renk sınıf olarak kalır.

`!important` bir bildirimin yanına yazılırsa o bildirim, normal özgüllüğü aşar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Zorunlu bildirim</title>
    <style>
      p {
        color: #0c5c8a !important;
      }

      #vana {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <p id="vana">İzmir</p>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” mavidir. Kimlik yeşil istese de mavi bildirim `!important` taşır. Bu, kazancı garanti eder ve sonraki yeşil düzeltmenin neden tutmadığını gizler. Kent notunda `!important` kullanılmaz. Kazanması istenen kural, doğru seçiciyle yazılır. Zorunlu bildirim, ancak başka türlü ezilen bir tarayıcı stili için son çare olarak düşünülür. Bu rehberdeki örneklerin geri kalanında yoktur.

## İlk değer ve miras (Initial and Inherit)

`inherit` özelliği ebeveynin hesaplanmış değerine çeker. `initial` özelliğin CSS’teki ilk değerine döner. `unset` miras alan bir özelliği `inherit`, miras almayanı `initial` yapar. `color` ve yazı tipi miras alır. `margin`, `padding` ve `border` miras almaz. Her paragrafın kendi kenar boşluğu vardır. Ebeveynin çerçevesi çocuğa geçmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Miras ve ilk değer</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #0e4d5c;
        font-family: Arial, Helvetica, sans-serif;
      }

      .kutu {
        border: 2px solid #0e4d5c;
        padding: 1rem;
      }

      .duz {
        color: initial;
      }

      .cerceve {
        border: inherit;
      }
    </style>
  </head>
  <body>
    <article class="kutu">
      <p>İzmir bu yazıyı gövdeden alır.</p>
      <p class="duz">Van, rengi özelliğin ilk değerine bırakır.</p>
      <p class="cerceve">Trabzon, çerçevenin mirasını ister.</p>
    </article>
  </body>
</html>
```

Tarayıcıda görünen:
Yazının çevresinde tek bir yeşil çerçeve vardır. “İzmir bu yazıyı gövdeden alır.” koyu deniz yeşilidir. Gövdenin `color` değeri paragrafa inmiştir. Ayrı bir `color` yazılmamıştır. “Van, rengi özelliğin ilk değerine bırakır.” tarayıcının ilk yazı rengine, çoğu yerde siyaha döner. Yeşil miras kesilir. “Trabzon, çerçevenin mirasını ister.” cümlenin kendi çevresinde ikinci bir yeşil çerçeve vardır. `border` normalde çocuğa inmez. `border: inherit` bu inişi bilinçli olarak açar. Kenar boşluğu ve iç boşluk hâlâ Trabzon paragrafının kendi değerleridir. Çerçeve miras alınınca kutu, hem yazının hem cümlenin çerçevesini gösterir.

`unset` Van paragrafına `color: unset` olarak yazılsaydı renk yine miras kalırdı. Çünkü `color` miras alan bir özelliktir. `unset` çerçevesiz bir paragrafta kenarlığı ilk değere, yani `none` değerine çeker. Hangi özelliğin miras aldığı, `unset` ile `initial` arasındaki farkı belirler.

## Sık yapılan hata

Eğik çizgiyle yorum yazmak, o bildirimden sonrasını bozar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bozuk yorum</title>
    <style>
      h1 {
        color: #0e4d5c; // başlık
        background-color: #ffffff;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon”un zemini beyaz olmayabilir. `// başlık` geçerli bir yorum olmadığı için o satır ve bazen bir sonraki bildirim düşer. Yeşil renk duruyorsa ilk satır noktalı virgülden önce tamamlanmıştır. Beyaz zemin yoksa ikinci satır bozulmuştur. Sonuç tarayıcıya göre değişir. Güvenilir olan, çift bölü kullanmamaktır.

Doğru yorum CSS yorumudur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Düzgün yorum</title>
    <style>
      h1 {
        color: #0e4d5c; /* başlık */
        background-color: #ffffff;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” yeşil yazı ve beyaz zeminle durur. “başlık” kelimesi ekranda yoktur.

İkinci hata, bir rengi tutturmak için her kurala `!important` eklemektir. Sonra yeni bir istisna da `!important` ister. Sayfa bir zorunluluk yığınına döner. Sınıf yetmiyorsa seçici daraltılır. `p.not` hem paragraf hem sınıf ister. Zorunlu bildirim eklenmez.

## Egzersizler

1. Aynı `p` seçicisine önce mavi, sonra yeşil verin. Paragraf yeşil görünsün. Yeşil kuralı mavi kuralın üstüne alın. Paragraf maviye dönsün.
2. Bir paragrafa hem etiket hem sınıf hem kimlik rengi yazın. Kazanan, kimliğin rengi olsun. Sınıf, etiket rengini geçsin. Kimlik silinince sınıfın rengi görünsün.
3. `//` ile bir not yazın. Alttaki zemin kuralının düşüp düşmediğine bakın. Notu `/* */` içine alın. Hem renk hem zemin uygulansın. `!important` kullanmadan kimliğin etiketi yendiği bir örnek kurun.

[← Önceki gün](../21-position/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../23-readable/ders.md)
