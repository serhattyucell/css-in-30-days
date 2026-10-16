# 27. Gün — Küçük sayfa: kıyaslama tablosu (Comparison Table)

Bu gün, dört kenti aynı ölçülerle okutan tabloya çizgi, zemin ve dar ekran davranışı verir. Yeni bir özellik yoktur. Birleşen kenarlık, başlık zemini, çift satırın beji ve yatay kaydırma 14. ve 10. günlerdendir. Plakalar 34, 35, 61 ve 65 olarak kalır. Çizgi süs için çift katına çıkarılmaz.

## Tek ızgara, kaydırılabilir dar ekran

Belge `kiyas.html` adıyla kaydedilir. Tablo 40 rem sütunun içinde durur. Çok dar pencerede `overflow: auto` ızgarayı sayfanın geri kalanını taşırmaz. Sayfa dikey okunur, tablo yatay kayar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kıyaslama</title>
    <style>
      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        background-color: #f4f1ea;
        color: #1e2430;
        font-family: Arial, Helvetica, sans-serif;
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
        max-width: 44rem;
        margin: 0 auto;
        padding: 1.5rem 1rem 3rem;
      }

      .tablo-alani {
        overflow: auto;
        background-color: #ffffff;
        border-radius: 0.5rem;
      }

      table {
        border-collapse: collapse;
        width: 100%;
        min-width: 32rem;
      }

      caption {
        text-align: left;
        font-weight: 700;
        color: #0e4d5c;
        padding: 0.8rem;
      }

      th,
      td {
        border: 1px solid #cfc8bc;
        padding: 0.6rem 0.8rem;
        text-align: left;
      }

      thead th {
        background-color: #0e4d5c;
        color: #ffffff;
      }

      tbody th {
        background-color: #ffffff;
      }

      tbody tr:nth-child(even) th,
      tbody tr:nth-child(even) td {
        background-color: #e7e2d8;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Kıyaslama</h1>
    </header>
    <main>
      <p>Dört kent aynı üç soruyla okunur: bölge, su, plaka.</p>
      <section class="tablo-alani">
        <table>
          <caption>Dört kentin bölgesi, suyu ve plakası</caption>
          <thead>
            <tr>
              <th scope="col">Kent</th>
              <th scope="col">Bölge</th>
              <th scope="col">Su</th>
              <th scope="col">Plaka</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <th scope="row">İstanbul</th>
              <td>Marmara Bölgesi</td>
              <td>İstanbul Boğazı</td>
              <td>34</td>
            </tr>
            <tr>
              <th scope="row">İzmir</th>
              <td>Ege Bölgesi</td>
              <td>Ege Denizi</td>
              <td>35</td>
            </tr>
            <tr>
              <th scope="row">Trabzon</th>
              <td>Karadeniz Bölgesi</td>
              <td>Karadeniz</td>
              <td>61</td>
            </tr>
            <tr>
              <th scope="row">Van</th>
              <td>Doğu Anadolu Bölgesi</td>
              <td>Van Gölü</td>
              <td>65</td>
            </tr>
          </tbody>
        </table>
      </section>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yeşil şeritte beyaz “Kıyaslama” vardır. Gövde ortaya alınmıştır. Açıklama paragrafının altında beyaz bir tablo durur. Adı “Dört kentin bölgesi, suyu ve plakası” sola yaslı, kalın ve yeşildir. Sütun başlıkları beyaz yazı ve yeşil zemindir. İstanbul satırı beyaz, İzmir açık bej, Trabzon beyaz, Van açık bejdir. Kent adları da o satırın zeminini alır. 34 İstanbul’un, 35 İzmir’in, 61 Trabzon’un, 65 Van’ın sağındadır. Hücreler arasında tek açık gri çizgi vardır. Yazı çizgiye yapışmaz.

Pencere tablonun 32 remin altına inince sayfanın tamamı sağa taşmaz. Beyaz alanın altında veya sağında kaydırma çıkar. Kaydırınca plaka sütunu görünür. Geniş pencerede kaydırma gerekmez. Dört sütun bir arada okunur.

## Başlık satırı yapışır (Sticky Header)

Uzun tabloda sütun adları kaybolmasın diye `thead th` yapışkan yapılır. `top: 0` satırı, kaydırılan kabın tepesinde tutar. Yapışkanlığın çalışması için kaydırma, sayfanın değil tablonun kabının üzerinde olmalıdır. Kabın yüksekliği sınırlıdır ve `overflow: auto` açıktır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yapışkan başlık</title>
    <style>
      body {
        background-color: #f4f1ea;
        font-family: Arial, Helvetica, sans-serif;
      }

      .tablo-alani {
        max-height: 9rem;
        overflow: auto;
        background-color: #ffffff;
      }

      table {
        border-collapse: collapse;
        width: 100%;
      }

      th,
      td {
        border: 1px solid #cfc8bc;
        padding: 0.5rem;
        text-align: left;
      }

      thead th {
        position: sticky;
        top: 0;
        background-color: #0e4d5c;
        color: #ffffff;
      }
    </style>
  </head>
  <body>
    <section class="tablo-alani">
      <table>
        <thead>
          <tr>
            <th>Kent</th>
            <th>Plaka</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>İstanbul</td><td>34</td></tr>
          <tr><td>İzmir</td><td>35</td></tr>
          <tr><td>Trabzon</td><td>61</td></tr>
          <tr><td>Van</td><td>65</td></tr>
        </tbody>
      </table>
    </section>
  </body>
</html>
```

Tarayıcıda görünen:
Beyaz alan yaklaşık 9 rem yüksektir. “Kent” ve “Plaka” yeşil zeminde beyazdır. Dört satır sığmazsa kutunun içinde kaydırma çıkar. Aşağı kaydırınca İstanbul yukarı gider. “Kent” ve “Plaka” tepede kalır. Satırlar başlığın altında akmaya devam eder. Başlığın zemini saydam olursa alttaki plaka yazısı başlığın içinden görünür. Bu yüzden yapışkan hücrenin `background-color` değeri doludur.

## Sık yapılan hata

`min-width` verip kabı `overflow: auto` yapmamak, dar pencerede bütün sayfayı yatay kaydırır. Şerit de sağa kaçar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Taşan sayfa</title>
    <style>
      table {
        min-width: 40rem;
        border-collapse: collapse;
      }

      th,
      td {
        border: 1px solid #0e4d5c;
      }
    </style>
  </head>
  <body>
    <table>
      <tr>
        <th>Van</th>
        <td>65</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
Dar pencerede tarayıcının kendi yatay çubuğu bütün belgeyi kaydırır. “Van” ve “65” arasında çizgi vardır ama sayfa başlığı da kaymanın içindedir.

Doğru belgede kaydırma tablonun kabındadır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sığan sayfa</title>
    <style>
      .tablo-alani {
        overflow: auto;
      }

      table {
        min-width: 32rem;
        border-collapse: collapse;
        width: 100%;
      }

      th,
      td {
        border: 1px solid #cfc8bc;
        padding: 0.5rem;
      }
    </style>
  </head>
  <body>
    <section class="tablo-alani">
      <table>
        <tr>
          <th>Van</th>
          <td>Doğu Anadolu Bölgesi</td>
          <td>Van Gölü</td>
          <td>65</td>
        </tr>
      </table>
    </section>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfa yerinde kalır. Dar pencerede kaydırma, tabloyu saran kutudadır. 65, Van satırının sağında durur ve kaydırılınca görünür.

## Egzersizler

1. `kiyas.html` dosyasında İstanbul 34 ve İstanbul Boğazı, İzmir 35 ve Ege Denizi, Trabzon 61 ve Karadeniz, Van 65 ve Van Gölü aynı satırda dursun. Başlık satırı yeşil ve beyaz olsun. Çift satırlar bej olsun.
2. Çizgiler tek hat olsun. Yazı çizgiden içeride dursun. Tablonun adı kalın, yeşil ve solda görünsün.
3. Pencereyi daraltın. Sayfanın tamamı sağa kaçmasın. Tablo kabının içinde yatay kaydırma çıksın. Plaka sütunu kaydırınca görünsün.

[← Önceki gün](../26-contact-form/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../28-faq/ders.md)
