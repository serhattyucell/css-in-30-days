# 26. Gün — Küçük sayfa: iletişim formu (Contact Form)

Bu gün, ileti formunu sayfanın yazısına ve kutularına bağlar. 25. gündeki liste okunuyordu. Bugün kutular, liste ve düğme aynı sütunda, aynı aileyle durur. Yeni bir özellik yoktur. `font: inherit`, `border-box`, odak çerçevesi ve yeşil düğme 20. günde kurulmuştu. Form hâlâ bir sunucuya mektup göndermez. `get` ile yazılanlar adres çubuğuna düşer.

## Sütun, etiket ve düğme

Belge `iletisim.html` adıyla kaydedilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İletişim</title>
    <style>
      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1rem;
        line-height: 1.5;
      }

      header {
        background-color: #0e4d5c;
        color: #ffffff;
        padding: 1rem;
      }

      h1 {
        margin: 0;
        font-size: 1.7rem;
      }

      main {
        max-width: 28rem;
        margin: 0 auto;
        padding: 1.5rem 1rem 3rem;
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

      button {
        font: inherit;
        cursor: pointer;
        padding: 0.7rem 1.1rem;
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
    <header>
      <h1>İletişim</h1>
    </header>
    <main>
      <p>Bu form ileti yollamaz. Gönderilince yazılanlar adres çubuğunda görünür.</p>
      <form action="iletisim.html" method="get">
        <label for="ad">Ad (zorunlu)</label>
        <input id="ad" name="ad" type="text" value="Serhat" required />
        <label for="eposta">E-posta (zorunlu)</label>
        <input id="eposta" name="eposta" type="email" required />
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
        <button type="submit">İletiyi adres çubuğuna yaz</button>
      </form>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şeritte beyaz “İletişim” vardır. Altında açıklama ve form, ortada, en çok 28 rem genişliğindedir. “Ad (zorunlu)” kalın ve kutunun üstündedir. Kutuda “Serhat” yazar. Kutu beyaz, açık gri kenarlı, yuvarlak köşeli ve sütun kadar geniştir. E-posta kutusu boştur. Kent listesi “Seçin” ile açılır. Dört kent İstanbul, İzmir, Trabzon ve Van’dır. Not alanı dört satırdır ve içinde “Van Gölü geniştir.” durur. Üç alan da sayfanın Arial yazısındadır. Bir alana Sekme ile gelince kenarlık yeşil olur, çevresinde amber çerçeve belirir.

Düğme gri kabartı değildir. Yeşil zemin, beyaz “İletiyi adres çubuğuna yaz” yazısı ve yuvarlak köşe vardır. Fare el işaretine döner. Zemin koyulaşır. E-posta boş veya kent “Seçin” iken basılırsa sayfa yenilenmez. Tarayıcı uyarı verir. E-posta `serhat@example.com` ve kent Van olunca adres `ad`, `eposta`, `kent` ve `not` değerlerini taşır. Şerit ve kutular yerinde kalır.

## İpucu (Placeholder)

E-posta kutusu boşken `::placeholder` soluk ve italik bir örnek adres gösterir. Adres yazılınca ipucu kaybolur. İpucu gönderilmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İpucu</title>
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
        max-width: 22rem;
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
    <form action="iletisim.html" method="get">
      <p>
        <label for="eposta">E-posta</label>
        <input id="eposta" name="eposta" type="email" placeholder="serhat@example.com" />
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Kutu boşken “serhat@example.com” soluk ve yatık durur. Harf yazılınca o yazı kaybolur. Kutudaki gerçek harfler koyu ve düzdür. Kutu temizlenince ipucu geri gelir. Form bu örnekte gönder düğmesi olmadan durur. Amaç, ipucunun değer sanılmamasıdır. `serhat@example.com` adres çubuğuna ancak kutu elle doldurulursa yazılır.

## Sık yapılan hata

Etiketi satır içi bırakıp kutuyu yüzde yüz yapınca ad, kutunun solunda sıkışır ve kutu alta taşabilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yana sıkışan etiket</title>
    <style>
      input {
        width: 100%;
      }
    </style>
  </head>
  <body>
    <form>
      <label for="ad">Ad</label>
      <input id="ad" name="ad" type="text" />
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Ad” ile kutu aynı satırda yarışır. Kutu yüzde yüz olduğu için satır taşar veya etiket üstte kalmadan sağa itilir. Odak çerçevesi de tarayıcının varsayılanındadır.

Doğru düzende etiket bloktur ve kutu `border-box` ile sığar:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Üstte duran etiket</title>
    <style>
      label {
        display: block;
        font-weight: 700;
      }

      input {
        font: inherit;
        box-sizing: border-box;
        display: block;
        width: 100%;
        padding: 0.6rem;
        border: 2px solid #cfc8bc;
      }
    </style>
  </head>
  <body>
    <form>
      <label for="ad">Ad</label>
      <input id="ad" name="ad" type="text" value="Serhat" />
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Ad” üstte ve kalındır. “Serhat” altındaki kutudadır. Kutu satırı taşmaz.

## Egzersizler

1. `iletisim.html` içinde ad, e-posta, kent ve not alt alta, aynı genişlikte ve sayfa yazısıyla görünsün. Etiketler kalın ve kutunun üstünde dursun. Sütun 28 remde, ortaya alınmış olsun.
2. Düğme yeşil ve beyaz olsun. Fare el şeklini alsın. Kent seçilmeden adres değişmesin. Van seçilince adresin sonunda `kent=van` görünsün.
3. Etiketi satır içi bırakın. Ad ile kutu sıkışsın. Etiketi blok yapın. Ad yeniden kutunun üstüne çıksın. Odakta amber çerçeve görünsün.

[← Önceki gün](../25-stop-list/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../27-comparison-table/ders.md)
