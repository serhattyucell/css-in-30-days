# 1. Gün — Giriş (Introduction)

Bu gün, CSS’in ne işe yaradığını ve ilk kuralın sayfayı nasıl değiştirdiğini kurar. HTML, bir parçanın başlık mı paragraf mı olduğunu söyler. CSS, o parçanın hangi renkte, hangi puntoda ve ne kadar boşlukla duracağını söyler. Bugün yalnızca bir kural vardır. Yerleşim, kutu ve esnek satır sonraki günlerindir.

## Görünüşü kural söyler

Bir CSS kuralı, seçici ile bildirimden oluşur. Seçici hangi parçanın değişeceğini, bildirim ise o parçada hangi özelliğin hangi değeri alacağını yazar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İlk kural</title>
    <style>
      h1 {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Van Gölü</h1>
    <p>Göl geniştir. Bu cümle henüz bir kural almamıştır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “İlk kural” yazar. “Van Gölü” büyük ve kalındır. Rengi tarayıcının varsayılan siyahı değildir. Koyu bir deniz yeşilidir. Altındaki paragraf siyah kalır ve normal puntodadır. `<style>` kelimesi, `h1` ve `color` ekranda yazı olarak durmaz. Sayfada çerçeve, şerit ve sütun yoktur.

Kural, küme parantezinin içine yazılır. `color`, özelliktir. `#0e4d5c`, değerdir. İkisinin arasında iki nokta üst üste vardır. Satırın sonundaki noktalı virgül, bildirimin bittiğini söyler. `h1` seçicisi, belgedeki her birinci düzey başlığı seçer. Paragrafı seçmez. Bu yüzden yalnızca başlığın rengi değişir.

`<style>` etiketi `<head>` içinde durur. İçindeki yazı bir cümle değildir. Tarayıcı onu komut diye okur. Stil etiketinin dışına, gövdeye aynı satırlar düz metin diye konursa komut olmazlar.

Başlığın büyük ve kalın durması da bir stildir. Onu yazan kişi değil, tarayıcının kendi varsayılan sayfasıdır. CSS yazılınca yalnızca yazılan özellik değişir. `color` denmiş, `font-size` denmemiştir. Punto, varsayılan başlık puntosunda kalır.

## İkinci kural paragrafı ayırır

Aynı `<style>` içinde ikinci bir kural, başka bir etiketi değiştirir. Kurallar alt alta durur. Biri diğerinin parantezinin içinde olmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki kural</title>
    <style>
      h1 {
        color: #0e4d5c;
      }

      p {
        color: #5e6670;
      }
    </style>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Saat Kulesi meydanın ortasındadır.</p>
    <p>Kordon kıyı boyunca yürür.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” koyu deniz yeşilidir ve büyük başlıktır. İki paragraf da soluk gri-mavi bir tondadır. İkisi de aynı kuralı paylaşır çünkü ikisi de `p` etiketidir. Başlık gri değildir. Paragraflar yeşil değildir. Her kural kendi seçicisinde kalır.

Dosya `ilk-stil.html` adıyla kaydedilir. Uzantı `.html` olur. Açmak için dosyaya çift tıklanır, tarayıcı penceresine sürüklenir veya tarayıcının Dosya menüsünden Aç komutu kullanılır. Adres çubuğu `file:///` ile başlar. Kural değişince dosya kaydedilir ve sayfa yenilenir. Yenileme yapılmazsa ekranda eski renk durur.

## Bildirim (Declaration)

Bir kuralın içinde birden çok bildirim durabilir. Her bildirim bir özelliğin adını, iki nokta üst üsteyi, değeri ve noktalı virgülü taşır. Bozuk bir bildirim yalnız kendini düşürür. Aynı küme parantezindeki sağlam bildirimler uygulanır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bildirimler</title>
    <style>
      h1 {
        color: #0e4d5c;
        font-size: 32px;
        font-weight: thick;
      }

      p {
        color: #1e2430;
      }
    </style>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p>Boğaz, kendi bildirimini alır. Başlığın bozuk satırı bu paragrafı boyamaz.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“İstanbul” koyu deniz yeşili ve yaklaşık 32 pikseldir. Kalınlığı, `thick` yüzünden ayrıca artmaz. `font-weight` için `thick` geçerli bir değer değildir. Tarayıcı o bildirimi yok sayar. `color` ve `font-size` aynı kuralda durduğu için ikisi de çalışır. Paragraf koyu mürekkeptir, 32 piksel değildir ve yeşil değildir. Başlığa yazılmış geçersiz bir değer, paragrafın rengine sıçramaz.

Varsayılan sayfa da bir stil dosyasıdır. Tarayıcı, CSS yazılmadan başlığı büyük ve kalın çizer. Yazılan bildirim yalnızca kendi özelliğini değiştirir. `font-size` yazılmamış bir paragrafta punto, tarayıcının paragraf puntosunda kalır. Sayfa kaynağında bildirimlerin hepsi durur. Ekranda özellik adları görünmez.

## Sık yapılan hata

Kuralı `<style>` dışına yazmak, onu sayfada görünen bir metin yapar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dışarıda kalan kural</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>
      h1 { color: #0e4d5c; }
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” siyah bir başlıktır. Altındaki satırda `h1 { color: #0e4d5c; }` cümle gibi, olduğu gibi okunur. Başlık yeşil olmaz. Tarayıcı, paragrafın içindeki bu yazıyı komut saymaz.

Doğru belgede kural baş bölgededir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İçeride duran kural</title>
    <style>
      h1 {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>Kıyı bu sayfadadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” koyu deniz yeşilidir. Paragrafta kural metni yoktur. “Kıyı bu sayfadadır.” siyah ve normal puntodadır.

İkinci hata, noktalı virgülü unutup sonraki özelliği aynı bildirime yapıştırmaktır. `color: #0e4d5c font-size: 32px;` tek bir bozuk bildirim olur. Tarayıcı o bildirimi atar. Başlık yeşil de olmaz, 32 piksel de olmaz. Her bildirim kendi noktalı virgülünü alır. `font-size` bu günün konusu değildir. Noktalı virgül unutulunca bir sonraki geçerli satırın da aynı bildirime karışabileceği görülür.

## Egzersizler

1. `ilk-stil.html` kurun. Sekmede “Van”, sayfada büyük “Van Gölü” koyu deniz yeşili görünsün. Altındaki paragraf siyah kalsın. Kural ekranda yazı olarak durmasın.
2. Aynı dosyaya ikinci bir kural ekleyin. Paragrafın rengi soluk gri-mavi olsun. Başlık yeşil kalsın. İkinci bir paragraf yazın. O da aynı soluk renkte dursun.
3. Kuralı bilerek paragrafın içine yazın. Başlığın siyah kaldığını ve kuralın sayfada okunduğunu görün. Sonra kuralı `<style>` içine geri alın. Başlık yeniden yeşil olsun, kural metni ekrandan kalksın.

[İçindekiler](../README.md) · [Sonraki gün →](../02-stylesheet/ders.md)
