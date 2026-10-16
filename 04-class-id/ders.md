# 4. Gün — Sınıf ve kimlik (Class and ID)

Bu gün, etiketin türünden başka bir adla seçim yapar. 3. günde bütün paragraflar aynı renge giriyordu. İçlerinden biri not, biri uyarı ise türleri aynı olsa da görünüşleri ayrılabilir. Sınıf tekrar eder. Kimlik bir öğeye aittir.

## Sınıf, aynı işi gören parçaları toplar

HTML’de `class` özelliği bir veya birkaç ad taşır. CSS’te o adın önüne nokta konur. `.not` adlı kural, sınıfı `not` olan her öğeye gider.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sınıf</title>
    <style>
      p {
        color: #1e2430;
      }

      .not {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Serhat'ın notu</h1>
    <p>Bu satır sıradan bir cümledir.</p>
    <p class="not">Bu satır not olarak ayrılmıştır.</p>
    <p class="not">İkinci not da aynı sınıftadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Başlık siyah ve büyüktür. Birinci paragraf koyu mürekkeptir. “Bu satır not olarak ayrılmıştır.” ve “İkinci not da aynı sınıftadır.” koyu deniz yeşilidir. İkisi de `<p>` olduğu hâlde sınıfı olanlar yeşildir. Sınıfı olmayan paragraf mürekkepte kalır. Nokta ekranda görünmez. `class="not"` yazısı da görünmez. Görünen, renktir.

Sınıf adı küçük harfle, boşluksuz yazılır. Bir öğe birden çok sınıf taşıyabilir: `class="not kisa"`. CSS’te `.not` ve `.kisa` ayrı kurallardır. İkisi de aynı öğeye gider. Bir sınıf birçok öğede tekrar edilebilir. Notun iki paragrafı da `not` olabilir.

## Kimlik, tek bir yeri işaretler

`id` sayfada bir kez durur. CSS’te önüne `#` konur. Kimlik, sayfa içi bağlantının hedefi olarak da kullanılır. Görünüş için her satıra ayrı kimlik vermek gerekmez. Tekrar edecek görünüş sınıf olarak kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kimlik</title>
    <style>
      #vana {
        color: #0e4d5c;
      }

      .soluk {
        color: #5e6670;
      }
    </style>
  </head>
  <body>
    <h1 id="vana">Van</h1>
    <p class="soluk">Göl kıyısından bakılan not.</p>
    <p><a href="#vana">Van başlığına dön</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” koyu deniz yeşili ve büyük bir başlıktır. Altındaki paragraf soluk gri-mavidir. “Van başlığına dön” bağlantısı tarayıcının varsayılan mavisinde ve altı çizilidir. Bağlantıya tıklanınca sayfa `#vana` hedefine kayar. Aynı `id` ikinci bir başlığa konmaz. Konursa hem bağlantı hem `#vana` kuralı ilk hedefte kalır. İkinci başlık yeşil olmak zorunda değildir.

Etiket ile sınıf birlikte yazılabilir. `p.not` yalnız sınıfı `not` olan paragrafları seçer. Bir başlık aynı sınıfı taşısa bile bu daraltılmış seçiciye girmez. `.not` ise sınıfı taşıyan başlığı da paragrafı da alır.

## Zincir seçici (Chained Selector)

`p.not` etiket ile sınıfı boşluksuz birleştirir. Hem paragraf olacak hem de `not` sınıfını taşıyacaktır. Araya boşluk konursa anlam değişir. `p .not` bir paragrafın içindeki, sınıfı `not` olan çocuğu arar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Zincir</title>
    <style>
      p.not {
        color: #0e4d5c;
      }

      .kisa {
        font-size: 14px;
      }
    </style>
  </head>
  <body>
    <h1 class="not">İzmir</h1>
    <p class="not kisa">Saat Kulesi hem not hem kısa satırdır.</p>
    <p>Kordon bu sınıfta değildir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” büyük başlıktır ve siyahtır. `class="not"` taşımasına rağmen `p.not` onu seçmez çünkü başlık paragraf değildir. “Saat Kulesi hem not hem kısa satırdır.” koyu deniz yeşili ve 14 pikseldir. İki sınıf aynı öğededir. `p.not` rengi verir. `.kisa` puntoyu verir. “Kordon bu sınıfta değildir.” normal puntoda ve siyahtır. Sınıf listesinde adlar boşlukla ayrılır. CSS’te `p.not` yazısındaki nokta boşluk değildir. Nokta, sınıfın başladığı yerdir.

`.not.kisa` boşluksuz yazılırsa öğenin iki sınıfı birden taşıması gerekir. Yalnız `not` olan bir paragraf bu kurala girmez. Yalnız `kisa` olan da girmez. İkisini birden isteyen görünüşler böyle daraltılır. Kimlik zinciri de yazılabilir. `h1#vana` hem başlık hem o kimliktir. Kimlik zaten tek olduğu için ek etiket çoğu zaman gerekmez.

## Sık yapılan hata

Noktayı unutmak, sınıf adını bir etiket sanır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Noktasız sınıf</title>
    <style>
      not {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p class="not">Boğaz bu nottadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Boğaz bu nottadır.” siyahtır. Tarayıcı `<not>` adlı bir etiket arar. Sayfada öyle bir etiket yoktur. `class="not"` taşıyan paragraf seçilmemiştir. Başlık da siyahtır.

Doğru seçici noktayla başlar:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Noktalı sınıf</title>
    <style>
      .not {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p class="not">Boğaz bu nottadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Yalnızca “Boğaz bu nottadır.” koyu deniz yeşilidir. “İstanbul” siyah büyük başlık olarak kalır.

İkinci hata, `#` ile `.` işaretini karıştırmaktır. `#not` bir kimlik arar. Öğede `class="not"` varsa renk değişmez. Üçüncü hata, aynı görünüşü dört paragrafa dört ayrı `id` ile vermektir. Çalışır ama her renk değişiminde dört kural birden aranır. Tekrar eden görünüş bir sınıfta toplanır.

## Egzersizler

1. İki paragraf `not` sınıfıyla koyu deniz yeşili olsun. Sınıfsız üçüncü paragraf koyu mürekkep renginde kalsın. Yeşil kural bir kez yazılsın.
2. Sayfadaki tek `h1` için `#vana` kuralı yazın. Başlık yeşil olsun. Aynı kimliği ikinci bir başlığa koymayın. Alta bir bağlantı koyun. Tıklanınca sayfa bu başlığa gelsin.
3. Noktayı silin. Yeşil paragraf siyaha dönsün. Noktayı geri koyun. Aynı paragraf yine yeşil olsun.

[← Önceki gün](../03-selectors/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../05-color/ders.md)
