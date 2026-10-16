# 2. Gün — Stil dosyası (Stylesheet)

Bu gün, kuralları HTML belgesinin içinden çıkarıp ayrı bir dosyaya koyar. 1. günde `<style>` aynı dosyanın başındaydı. Tek bir deneme için o yeter. Aynı görünüş birkaç sayfada kullanılacaksa kurallar bir `.css` dosyasında durur. Sayfa o dosyayı adıyla çağırır.

## Sayfa, stil dosyasını bağlar

`<link>` etiketi, belgenin başında durur ve dışarıdaki stil dosyasının yolunu verir. `rel="stylesheet"`, bu dosyanın bir stil sayfası olduğunu söyler. `href`, dosyanın adıdır.

Önce `stil.css` kaydedilir. İçinde HTML etiketi yoktur:

```css
h1 {
  color: #0e4d5c;
}

p {
  color: #5e6670;
}
```

Tarayıcıda görünen:
`stil.css` tek başına açılırsa renkli bir sayfa çıkmaz. Ekranda `h1` ve `p` kuralları düz metin olarak okunur. Deniz yeşili veya gri bir başlık yoktur.

Aynı klasöre `sayfa.html` kaydedilir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağlı stil</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <h1>İstanbul</h1>
    <p>Boğaz kenti iki yakaya ayırır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
`stil.css` tarayıcıda açılırsa kurallar düz metin olarak okunur. Renkli bir sayfa çıkmaz. Sayfa `sayfa.html` dosyasıdır. O açılınca sekmede “Bağlı stil” yazar. “İstanbul” koyu deniz yeşilidir ve büyük başlıktır. Paragraf soluk gri-mavidir. Ekranda `<link>` ve dosya adı görünmez. 1. gündeki `<style>` ile aynı görünüş, bu kez iki dosyadan gelir.

`<link>` kapanışlı bir etiket çifti değildir. `<head>` içinde, `<title>` sonrasında durması yeter. `href="stil.css"`, iki dosya aynı klasördeyse yalnızca addır. Stil dosyası başka klasördeyse yol yazılır. Ad büyük harfle `Stil.css` diye kaydedilmişse ve `href` küçük harfle yazılmışsa birçok sistemde dosya bulunmaz. Sayfa, stilsiz varsayılan hâline döner: başlık siyah, paragraf siyah.

## Aynı dosya iki sayfayı boyar

Bir stil dosyası, onu bağlayan her belgeye aynı kuralları uygular. İkinci bir HTML dosyası aynı `href` ile açılır.

`ikinci.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İkinci sayfa</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>Kent Karadeniz kıyısındadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” da koyu deniz yeşilidir. Paragraf soluk gri-mavidir. `stil.css` içindeki `h1` kuralı bir kez yazılıdır. İki sayfa da onu okur. `stil.css` içinde `#0e4d5c` değeri değiştirilip dosya kaydedilince ve iki sayfa da yenilenince iki başlık birden yeni renge döner. Her HTML dosyasını tek tek boyamak gerekmez.

`<style>` ile `<link>` aynı belgede bir arada da durabilir. Bu rehberin kısa örnekleri, kopyalanması kolay olsun diye çoğu gün tek dosyada `<style>` kullanır. Gün bitince kuralın asıl yeri, paylaşılan stil dosyasıdır.

## Sonra gelen dosya (Source Order)

Aynı seçici iki kez yazılıysa, sayfada sonra okunan bildirim aynı özelliği ezer. İki `<style>` bloğu da, iki `<link>` de bu sırayı kullanır. İlk dosya silinmez. Yalnızca çakışan özellikte ikinci değer kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki sıra</title>
    <style>
      h1 {
        color: #0c5c8a;
        font-size: 32px;
      }
    </style>
    <style>
      h1 {
        color: #0e4d5c;
      }
    </style>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>İkinci blok yalnız rengi yeniden yazar.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” koyu deniz yeşilidir ve 32 pikseldir. Birinci blok maviyi ve puntoyu birlikte vermişti. İkinci blok yalnızca rengi yeşile çeker. Punto ikinci blokta yazılmadığı için 32 piksel yerinde kalır. Paragraf siyahtır. İki stil bloğu ekranda ayrı bir başlık üretmez. Tarayıcı onları sırayla uygular.

Ayrı dosyalarda da aynı şey olur. `ilk.css` başlığı mavi, `son.css` başlığı yeşil yapıyorsa HTML’de `son.css` daha altta bağlanır. Sayfa yenilenmeden eski dosya önbellekte kalabilir. Renk değişince her iki dosya kaydedilir ve tarayıcı yenilenir. Çakışmayan özellikler, birinci dosyadan gelmeye devam eder.

## Sık yapılan hata

`rel` yazılmadan veya `href` yalnızca dosya adı sanılarak yanlış bağ kurmak, stili sessizce yok sayar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kopuk stil</title>
    <link href="stil.css" />
  </head>
  <body>
    <h1>Van</h1>
    <p>Göl geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” siyah bir başlıktır. Paragraf da siyahtır. `stil.css` klasörde dursa bile sayfa onu stil sayfası olarak yüklemez. `rel="stylesheet"` olmadığı için tarayıcı ilişkinin türünü bilmez. Ekranda bir hata cümlesi de çıkmayabilir. Eksiklik, renklerin hiç değişmemesinden anlaşılır.

Doğru bağ:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağlı sayfa</title>
    <link rel="stylesheet" href="stil.css" />
  </head>
  <body>
    <h1>Van</h1>
    <p>Göl geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
`stil.css` 1. kuraldaki renkleri taşıyorsa “Van” koyu deniz yeşili, paragraf soluk gri-mavidir.

İkinci hata, CSS dosyasının içine `<style>` etiketi yazmaktır. Stil dosyası ham kural taşır. `<style>` bir HTML etiketidir. CSS dosyasında o etiket durursa ilk kural bozulabilir ve renkler uygulanmaz. Üçüncü hata, `href` başına gereksiz bir eğik çizgi koymaktır. `/stil.css`, klasörün içini değil, diskin kökünü arar. Dosya aynı klasördeyse adres `stil.css` olarak kalır.

## Egzersizler

1. `stil.css` ve `sayfa.html` kurun. Sayfada “İzmir” koyu deniz yeşili, altındaki cümle soluk gri-mavi görünsün. HTML dosyasının içinde `<style>` olmasın.
2. `not.html` adlı ikinci bir sayfa aynı `stil.css` dosyasını bağlasın. “Van” başlığı da aynı yeşil olsun. Stil dosyasında yeşili değiştirip iki sayfayı da yenileyin. İki başlık birden yeni renge dönsün.
3. `rel="stylesheet"` satırını silin. Başlık siyah kalsın. Özelliği geri koyun. Yeşil renk geri gelsin.

[← Önceki gün](../01-introduction/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../03-selectors/ders.md)
