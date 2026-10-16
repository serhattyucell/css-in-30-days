# 20. Gün — Form alanları (Form Controls)

Bu gün, kutunun, listenin ve düğmenin tarayıcıdan gelen görünüşünü sayfanın yazısına yaklaştırır. Form HTML’de kurulmuştu. Alanlar çoğu tarayıcıda gövdenin yazı tipini miras almaz. Küçük, gri çerçeveli ve başka bir aileyle dururlar. `font: inherit` aileyi, boyutu ve satır yüksekliğini üst öğeden alır. `box-sizing: border-box` iç boşluğu, yüzde yüz genişliğin dışına taşırmadan içeri koyar. `cursor: pointer` düğmenin üzerine gelince tıklanabilir bir işaret gösterir.

## Alan sayfayla aynı yazıyı kullanır

Etiket `display: block` olunca ad, kutunun üstüne çıkar. Kutu da blok olunca alt satıra iner ve verilen genişliğe yayılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Form görünüşü</title>
    <style>
      body {
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1rem;
      }

      form {
        max-width: 24rem;
      }

      label {
        display: block;
        margin-bottom: 0.3rem;
        font-weight: 700;
      }

      input,
      select,
      textarea {
        font: inherit;
        box-sizing: border-box;
        width: 100%;
        padding: 0.6rem;
        margin-bottom: 1rem;
        border: 2px solid #cfc8bc;
        border-radius: 0.4rem;
        background-color: #ffffff;
        color: #1e2430;
      }

      input:focus,
      select:focus,
      textarea:focus {
        border-color: #0e4d5c;
        outline: 3px solid #c47b00;
        outline-offset: 2px;
      }
    </style>
  </head>
  <body>
    <h1>İletişim</h1>
    <form action="form.html" method="get">
      <label for="ad">Ad (zorunlu)</label>
      <input id="ad" name="ad" type="text" value="Serhat" required />
      <label for="kent">Kent (zorunlu)</label>
      <select id="kent" name="kent" required>
        <option value="">Seçin</option>
        <option value="istanbul">İstanbul</option>
        <option value="izmir">İzmir</option>
        <option value="trabzon">Trabzon</option>
        <option value="van">Van</option>
      </select>
      <label for="not">Not</label>
      <textarea id="not" name="not" rows="4">Van Gölü geniştir.</textarea>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“İletişim” başlığının altında form en çok 24 rem genişliğindedir. “Ad (zorunlu)” kalın bir satırdır. Altında beyaz bir kutu vardır. İçinde “Serhat” yazar. Kutu, formun genişliğini kaplar ve yazı sayfanın Arial ailesindedir. “Kent (zorunlu)” altında açılır liste, “Not” altında dört satırlık alan vardır. Üçü de aynı çerçeve kalınlığında, açık gri kenarlı ve yuvarlak köşelidir. “Not” kutusunda “Van Gölü geniştir.” durur. Bir kutuya tıklanınca veya Sekme ile gelince kenarlık yeşile döner ve çevresinde amber çerçeve belirir. Üç alan da sola yapışık dar şeritler olarak kalmaz.

`font: inherit` yazılmazsa kutu, işletim sisteminin küçük varsayılan yüzünü kullanabilir. Gövde 1 rem iken kutu daha küçük görünür. Kenarlık ve iç boşluk da gövdeyle uyuşmaz.

## Düğme parmakla ayırt edilir

Gönder düğmesi, formun yazısına ve yeşil zemine çekilir. `cursor: pointer` fareyi el işaretine çevirir. Üzerine gelince zemin kararır. Odakta amber çerçeve kalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Düğme</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      button {
        font: inherit;
        cursor: pointer;
        padding: 0.7rem 1.2rem;
        border: 0;
        border-radius: 0.5rem;
        background-color: #0e4d5c;
        color: #ffffff;
      }

      button:hover {
        background-color: #0a3c48;
      }

      button:focus {
        outline: 3px solid #c47b00;
        outline-offset: 2px;
      }
    </style>
  </head>
  <body>
    <form action="dugme.html" method="get">
      <p>
        <label for="kent">Kent</label>
        <input id="kent" name="kent" type="text" />
      </p>
      <button type="submit">Kenti adres çubuğuna yaz</button>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Düğme tarayıcının gri, kabarık varsayılanı değildir. Koyu deniz yeşili, beyaz yazılı, yuvarlak köşeli bir kutudur. Yazı “Kenti adres çubuğuna yaz” diye tam okunur. Fare düğmenin üzerine gelince işaret el olur ve zemin biraz daha koyu yeşile döner. Sekme ile gelince amber çerçeve görünür. Düğmeye basılınca form `get` ile gider. Kent kutusuna Van yazılıysa adresin sonunda `kent=Van` benzeri bir sorgu durur. Renk, düğmenin işini değiştirmez. İş, `type="submit"` değerindedir.

`border: 0` varsayılan kabartıyı kaldırır. Odak için kenarlık silinmişse çerçeve `outline` ile kalmalıdır. İkisi birden yoksa klavye odağı görünmez.

## Yer tutucu (Placeholder)

`::placeholder` kutunun içindeki ipucunu seçer. Kutuya gerçek bir değer yazılınca ipucu kaybolur ve bu seçici görünmez olur. İpucu bir değer değildir. Gönderilince adrese gitmez. Rengi soluk bırakılır ki “Serhat” gibi gerçek bir yazıdan ayrılsın.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yer tutucu</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
        color: #1e2430;
      }

      input {
        font: inherit;
        box-sizing: border-box;
        width: 100%;
        max-width: 20rem;
        padding: 0.6rem;
        border: 2px solid #cfc8bc;
        border-radius: 0.4rem;
      }

      input::placeholder {
        color: #5e6670;
        font-style: italic;
      }
    </style>
  </head>
  <body>
    <h1>E-posta</h1>
    <form action="ipucu.html" method="get">
      <p>
        <label for="eposta">E-posta</label>
        <input id="eposta" name="eposta" type="email" placeholder="serhat@example.com" />
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Kutu boşken içinde “serhat@example.com” soluk gri-mavi ve italik durur. Yazı kutunun kenarından içeridedir. Bir harf yazılınca ipucu kaybolur. Yazılan harf koyu mürekkep ve düzdür. Kutuyu boşaltınca ipucu geri gelir. Düğme bu örnekte yoktur. Amaç, ipucunun gerçek değer gibi durmadığını görmektir. Gönderilen bir formda bu ipucu `eposta` değeri olarak gitmez. Kullanıcı bir adres yazmadıysa alan boş gider veya `required` uyarı verir.

`::placeholder` iki iki noktayla yazılır. Tek iki nokta bazı tarayıcılarda eski sözde öğe biçimidir. Bu rehber çift iki nokta kullanır. `::first-line` bir paragrafın ilk satırını, `::marker` liste işaretini seçer. İşaretin rengi `li::marker` ile değiştirilebilir. İşaretin kendisi `list-style` ile seçilir. Renk ile tür ayrı bildirimlerdir.

## Sık yapılan hata

`width: 100%` verip `content-box` bırakmak, iç boşluk yüzünden kutuyu formun dışına iter.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Taşan kutu</title>
    <style>
      form {
        width: 16rem;
        background-color: #ffffff;
      }

      input {
        width: 100%;
        padding: 1rem;
        box-sizing: content-box;
      }
    </style>
  </head>
  <body>
    <form>
      <input type="text" name="kent" value="Trabzon" />
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz form 16 remdir. Kutunun sağ kenarı formun sağından taşar. `%100` içeriğe aittir. 1 rem sağ ve sol iç boşluk dışarı eklenir.

Doğru kutu kenarlık hesabını kullanır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sığan kutu</title>
    <style>
      form {
        width: 16rem;
        background-color: #ffffff;
        padding: 1rem;
      }

      input {
        font: inherit;
        box-sizing: border-box;
        width: 100%;
        padding: 0.6rem;
        border: 2px solid #cfc8bc;
      }
    </style>
  </head>
  <body>
    <form>
      <input type="text" name="kent" value="Trabzon" />
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” yazan kutu, beyaz formun iç kenarlarında biter. Sağa taşmaz. Yazı, formun ailesindedir.

## Egzersizler

1. Ad, kent listesi ve not alanı alt alta, aynı genişlikte ve sayfanın yazı tipinde görünsün. Etiketler kalın ve kutunun üstünde dursun. Odaktaki kutunun çevresinde amber çerçeve olsun.
2. Gönder düğmesi yeşil zemin ve beyaz yazı taşısın. Fare üzerine gelince işaret el olsun ve zemin koyulaşsın. Düğme gri kabartılı varsayılanında kalmasın.
3. Kutuyu `content-box` ve `width: 100%` yapın. Sağa taştığını görün. `border-box` yapınca aynı iç boşluk formun içinde kalsın.

[← Önceki gün](../19-media/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../21-position/ders.md)
