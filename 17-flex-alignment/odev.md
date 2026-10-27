# Ödev — 17. güne kadar (4) · zor + eğlenceli

Bu ödev, 1–17. günleri zorlar. Önceki kafe / pansiyon / kitapçı ödevlerinden farklıdır. Grid, medya sorgusu, form ve konum **yasak**. Çözüm dersin içinde yoktur.

Dosya adı: `corap-muzesi.html`  
Stil `<style>` içinde dursun.

## Konu

**Ulusal Çorap Müzesi** — Serhat’ın uydurma ama ciddiye alınan müzesi. Sergiler dört kentten “efsane çorap” gösterir. Sayfa gerçek bir müze sitesi gibi dursun; şaka metin, ciddi CSS.

## Renk paleti

| Rol | Hex |
| --- | --- |
| Sayfa zemini | `#f6f0e8` |
| Kart zemini | `#ffffff` |
| Ana renk | `#6b2d5c` |
| Koyu şerit / footer | `#2d1b28` |
| Vurgu | `#e8a838` |
| Metin | `#1f1520` |
| İkincil | `#6e5c66` |
| Kenarlık | `#d9cfc4` |
| Tablo çift satır | `#efe6db` |
| Sergi — İstanbul | `#6b2d5c` |
| Sergi — İzmir | `#c45c26` |
| Sergi — Trabzon | `#2f6b4f` |
| Sergi — Van | `#3d5a80` |

## Zorunlu bölümler

### 1. Üst bar (iki iş birden)
- Solda müze adı (istersen `#logo`).
- Ortada veya sağda 4 menü maddesi (flex + `gap`).
- Sağda sarı “Açık” rozeti.
- Tüm satır: `justify-content: space-between`, `align-items: center`.
- Rozet biraz yukarı/aşağı kaymasın; dikey ortalı olsun.

### 2. Bilet şeridi (hero, ters düzen)
- **Sol:** sarı kutu — “Bilet al” linki + kısa fiyat notu.
- **Sağ:** büyük başlık + bir cümle.
- Yani vurgu kutusu solda; metin sağda. (`space-between`, `flex-wrap`, `align-items: center`)
- Önceki ödevlerin kapak düzenini aynen kopyalama.

### 3. Sergi kartları (iç içe flex — asıl zorluk)
Dört kart: İstanbul, İzmir, Trabzon, Van. Dışarıda flex + `gap` + `flex-wrap`.

Her kartın **içinde** de flex olsun, `flex-direction: column`:
1. Üstte renkli şerit (kent rengi)
2. Çorap adı (sınıf ile)
3. 1 komik cümle
4. Alt satır: solda yıl / sağda “İncele” — bu satır ayrı bir flex (`space-between`)

**Ek kural:** Van kartında `align-self: flex-end` kullan (kardeşlerinden farklı hizalansın). Dış kabın `align-items: stretch` veya `flex-start` olduğunu göster.

### 4. Ziyaret planı (yan yana, oran farklı)
- Sol kutu `flex: 2` — müze görseli + kısa metin.
- Sağ kutu `flex: 1` — “Bugün” listesi (işaretsiz, dikey flex): 3 madde (ör. tur saati, sesli rehber, kafe).
- `gap`, `align-items: stretch`.

### 5. Koleksiyon etiketleri
Yatay flex, `flex-wrap`, işaretsiz liste. En az 5 etiket (Yün, Çizgili, Tek, Kayıp çift, Kışlık…). Dolu zeminli olsun.

### 6. Bilet fiyatları tablosu
Üç sütun: bilet türü, fiyat, not.  
`border-collapse`, koyu başlık, çift satır farklı zemin. En az 4 satır (Öğrenci, Yetişkin, Aile, Serhat dostu…).

### 7. Footer (üç parça)
Flex + `space-between` + `align-items: center`:
- sol: müze adı  
- orta: kısa adres uydurması  
- sağ: “© Serhat”  
Daralınca `flex-wrap` ile alta insinler.

## Kullanılması gerekenler (hepsi)

| Gün | Zorunlu |
| --- | --- |
| 02–04 | sınıf + en az bir kimlik |
| 05 | palet |
| 06–07 | yazı tipi, metin |
| 08 | `rem` / `em` ağırlıklı |
| 09–11 | padding, margin, border |
| 12 | `display` |
| 13 | `:hover` (en az menü veya “İncele”) |
| 14 | liste + tablo (3 sütun) |
| 15 | görsel sığdırma veya renkli kutu |
| 16–17 | `flex`, `gap`, `flex-wrap`, `justify-content`, `align-items`, **`flex-direction: column`**, **`align-self`**, **`flex: 1` / `flex: 2`** |

## Eğlence kuralı

Metinler komik olabilir; CSS ciddidir. “asdf” ve lorem yok. Kentler ve Serhat kalsın.

## Önizleme

[onizleme.html](onizleme.html)

## Bitince kontrol

- Bilet şeridinde sarı kutu **solda** mı?
- Kartların içinde column flex var mı?
- Van kartı `align-self` ile ayrışıyor mu?
- Ziyaret planında `flex: 2` / `flex: 1` belli mi?
- Tabloda 3 sütun ve şeritli satırlar var mı?
- Footer üç parçalı mı?

[← 17. gün](ders.md) · [İçindekiler](../README.md)
