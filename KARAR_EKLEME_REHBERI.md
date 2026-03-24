# Yargıtay 4. HD – Karar Ekleme Rehberi

Bu rehber, mevcut 100 karardan 300 karara çıkma sürecinde kullanılacak standartları belirler.

---

## 1. Karar Seçim Kriterleri

Eklenecek kararlar şu niteliklere sahip olmalıdır:

- **Emsal niteliğinde** olmalı (rutin tekrar kararlar eklenmemeli)
- **Yargıtay 4. Hukuk Dairesi** kararı olmalı
- **Güncel** kararlar öncelikli (2024-2025-2026)
- Farklı hukuki konuları çeşitli şekilde kapsamalı
- Mevcut kararlarla **tekrar etmemeli** (aynı ilkeyi tekrarlayan kararlar yerine farklı yön getiren kararlar)

---

## 2. index.html'ye Karar Ekleme Şablonu

Her karar `<main class="wrap">` içine şu formatta eklenir:

```html
<article class="karar" data-sonuc="SONUC_KODU" data-tags="Etiket1|Etiket2|Etiket3">
    <span class="karar__num">NO</span>
    <div class="karar__ref">
        <span>ESAS_NO E. / KARAR_NO K. / TARIH T.</span>
        <a href="https://karararama.yargitay.gov.tr/getDokuman?id=DOKUMAN_ID" target="_blank" rel="noopener" class="karar__link"><i class="ph ph-arrow-square-out"></i> Yargıtay</a>
    </div>
    <div class="karar__top">
        <h2 class="karar__konu">KARAR BAŞLIĞI</h2>
        <span class="sonuc sonuc--SONUC_KODU">SONUC_METNI</span>
    </div>
    <p class="karar__ozet">KARAR ÖZETİ</p>
    <div class="karar__foot">
        <div class="karar__tags"><span class="tag">Etiket1</span><span class="tag">Etiket2</span><span class="tag">Etiket3</span></div>
        <a href="kararlar/NO.html" class="btn btn--filled">
            <i class="ph ph-article"></i> Kararı Gör
        </a>
    </div>
</article>
```

### Alan Açıklamaları

| Alan | Açıklama | Örnek |
|------|----------|-------|
| `data-sonuc` | Sonuç kodu: `onama`, `bozma`, `duzelt`, `red` | `data-sonuc="bozma"` |
| `data-tags` | Pipe (`\|`) ile ayrılmış etiketler | `Kasko\|Değer Kaybı\|Faiz` |
| `karar__num` | 2 haneli sıra numarası | `101` |
| `karar__ref` | Esas No / Karar No / Tarih formatı | `2025/10895 E. / 2025/14494 K. / 22.10.2025 T.` |
| `sonuc--SONUC_KODU` | CSS sınıfı: `sonuc--onama`, `sonuc--bozma`, `sonuc--duzelt`, `sonuc--red` | |
| `SONUC_METNI` | Görüntülenen metin: `Onama`, `Bozma`, `Düzelterek Onama`, `Red` | |

---

## 3. Karar Özeti Yazım Kuralları

Özet, kararın hukuki özünü aktarmalıdır. Şu kurallara uyulmalıdır:

### 3.1 İçerik
- **İlk cümle**: Davanın konusu ve tarafları (kim, ne talep ediyor)
- **Orta kısım**: Hukuki uyuşmazlığın özü, tarafların argümanları
- **Son cümle**: Yargıtay'ın kararı ve gerekçesinin özü

### 3.2 Üslup
- Hukuki terminoloji kullanılmalı (gündelik dil değil)
- 3-5 cümle uzunluğunda olmalı
- Pasif yapı tercih edilmeli ("karar bozulmuştur", "hüküm onanmıştır")
- Kanun maddeleri belirtilmeli (örn: "TBK m.51", "KTK m.109/2", "HMK m.107")
- Kararın emsal değeri olan kısmı vurgulanmalı

### 3.3 Kaçınılacaklar
- "Bu karar..." gibi meta ifadeler kullanılmamalı
- Gereksiz detaylar (taraf isimleri, tutar rakamları) özete eklenmemeli
- Çok uzun özetlerden kaçınılmalı (max ~100 kelime)

### 3.4 Örnek Özet

> Trafik kazasından kaynaklanan tazminat davasında, 2918 sayılı Kanun'un 109/2. maddesi gereğince cezayı gerektiren fiillerde daha uzun (8 yıl) zamanaşımı süresinin uygulanacağı belirtilmiştir. Kısmi dava olarak açılan davada, kaza tarihinden itibaren sekiz yıllık süre geçtikten sonra yapılan ıslahın zamanaşımına uğradığı, mahkemece davayı kısmi dava olarak nitelendirip zamanaşımı def'ini kabul etmemesinin hatalı olduğu gerekçesiyle ıslah edilen kısım yönünden karar bozulmuştur.

---

## 4. Etiket Sistemi (ÇOK ÖNEMLİ)

Etiketler, kullanıcıların karar bulmasının **ana yolu**dur. Doğru etiketleme hayati önem taşır.

### 4.1 Mevcut Etiket Kategorileri ve Etiketler

#### Kaza Türü
| Etiket | Ne Zaman Kullanılır |
|--------|-------------------|
| `Yaya Kazası` | Yaya çarpması, yaya geçidi kazaları |
| `Motosiklet Kazası` | Motosiklet sürücüsü veya yolcusu dahil |
| `Bisiklet Kazası` | Bisiklet sürücüsü dahil |
| `Otobüs/Minibüs` | Toplu taşıma araçları dahil |
| `İş Makinesi` | Traktör, kepçe, forklift vb. |
| `Tek Taraflı Kaza` | Karşı taraf yok, tek araç |
| `Zincirleme Kaza` | 3+ araç dahil |
| `Ölümlü Kaza` | Kaza sonucu ölüm var |
| `Çocuk Mağdur` | 18 yaş altı mağdur |
| `Pert Total` | Aracın pert/total olması |

#### Kusur
| Etiket | Ne Zaman Kullanılır |
|--------|-------------------|
| `Emniyet Kemeri` | Emniyet kemeri takılmamış, müterafik kusur |
| `Alkollü Sürücü` | Sürücü alkollü |
| `Ehliyetsiz Sürücü` | Ehliyeti yok veya uygun sınıf değil |
| `Kask Kullanmama` | Motosiklet/bisiklet kaskı yok |
| `Kırmızı Işık` | Kırmızı ışık ihlali |
| `Hız İhlali` | Aşırı hız / hız sınırı aşımı |
| `Müterafik Kusur` | Zarar görenin birlikte kusuru (TBK m.52) |
| `Hatır Taşıması` | Karşılıksız/hatır için taşıma |
| `Plakasız/Tescilsiz` | Plakasız veya tescilsiz araç |
| `Hakkaniyet İndirimi` | TBK m.51 kapsamında tazminat indirimi |

#### Tazminat
| Etiket | Ne Zaman Kullanılır |
|--------|-------------------|
| `Destekten Yoksun Kalma` | Ölüm sonucu DYK tazminatı |
| `Sürekli İş Göremezlik` | Kalıcı maluliyet tazminatı |
| `Geçici İş Göremezlik` | Tedavi süresindeki iş göremezlik |
| `Manevi Tazminat` | Manevi tazminat talebi/hesabı |
| `Maddi Tazminat` | Genel maddi tazminat |
| `Tedavi Gideri` | Hastane, ilaç, tedavi masrafları |
| `Bakıcı Gideri` | Bakım ve bakıcı giderleri |
| `Cenaze Gideri` | Cenaze masrafları |
| `Değer Kaybı` | Araç değer kaybı |
| `Gelir Kaybı` | Gelir/kazanç kaybı |

#### Sigorta
| Etiket | Ne Zaman Kullanılır |
|--------|-------------------|
| `ZMSS` | Zorunlu mali sorumluluk sigortası dahil |
| `Kasko` | Kasko sigortası dahil |
| `Sigorta Tahkim` | Sigorta Tahkim Komisyonu / İtiraz Hakem Heyeti kararı |
| `SGK Rücu Davası` | SGK'nın rücu davası |
| `Sigorta Rücu Davası` | Sigorta şirketinin rücu davası |
| `İtirazın İptali` | İcra takibine itirazın iptali |

#### Hesaplama & Rapor
| Etiket | Ne Zaman Kullanılır |
|--------|-------------------|
| `Aktüerya Hesabı` | Aktüerya hesaplama yöntemi tartışması |
| `Maluliyet Raporu` | Maluliyet oranı/rapor uyuşmazlığı |
| `Bilirkişi Çelişkisi` | Bilirkişi raporları arası çelişki |
| `ÇÖZGER Raporu` | Çocuklar için özel gereksinim raporu |

#### Usul Hukuku
| Etiket | Ne Zaman Kullanılır |
|--------|-------------------|
| `Zamanaşımı` | Zamanaşımı süresi tartışması |
| `Belirsiz Alacak` | HMK m.107 belirsiz alacak davası |
| `Islah` | Islah işlemi, süresi, geçerliliği |
| `Vekalet Ücreti` | Vekalet ücreti hesabı/uyuşmazlığı |
| `Kesinlik Sınırı` | Temyiz/istinaf kesinlik sınırı |
| `Usuli Kazanılmış Hak` | Bozma sonrası kazanılmış hak |
| `Faiz` | Faiz başlangıcı, türü, hesabı |
| `Tasarrufun İptali` | Muvazaalı işlem iptali |

### 4.2 Etiketleme Kuralları

1. **Her karara en az 2, en fazla ~10 etiket** eklenmelidir
2. **Ana konuyu yansıtan etiketler** mutlaka olmalı
3. **İlişkili tüm konular** etiketlenmeli (örn: motosiklet kazası + kask kullanmama + müterafik kusur + sürekli iş göremezlik + maluliyet raporu + ZMSS + sigorta tahkim + faiz)
4. `Faiz` etiketi, faiz konusunun kararın esasına etki ettiği durumlarda kullanılmalı (her karara otomatik eklenmemeli)
5. `Vekalet Ücreti` etiketi, vekalet ücreti hesabında özel bir durum varsa kullanılmalı
6. Etiketler **mevcut listeden** seçilmelidir – yeni etiket eklenecekse sidebar'a da eklenmeli

### 4.3 Yeni Etiket Ekleme

Yeni bir etiket gerekiyorsa:

1. `index.html`'deki sidebar'a uygun gruba `<button>` ekle
2. Sayıyı `0` olarak başlat (JS dinamik güncelleyecek)
3. Bu rehbere yeni etiketi dokümante et

```html
<button class="sidebar__item" onclick="filterByTag('Yeni Etiket',this)" data-tag="Yeni Etiket">
  <span>Yeni Etiket</span>
  <span class="sidebar__count">0</span>
</button>
```

---

## 5. Detay Sayfası (kararlar/NO.html) Şablonu

Her karar için `kararlar/` klasöründe bir detay HTML dosyası oluşturulmalıdır. Mevcut dosyalardan birini şablon olarak kullanın (örn: `kararlar/1.html`).

Detay sayfası şunları içermeli:
- Künye bilgisi (Esas No, Karar No, Tarih)
- Yargıtay karar arama linki
- Konu başlığı ve özet
- Meta bilgiler (Daire, Sonuç, Esas No, Karar Tarihi)
- Kararın tam metni

---

## 6. Sidebar Sayılarını Güncelleme

Etiket sayıları artık JavaScript tarafından **dinamik olarak** hesaplanıyor. Bu nedenle sidebar'daki `sidebar__count` içindeki sabit sayılar sadece ilk yükleme için referans olup, filtre kullanıldığında otomatik güncellenir.

Yeni kararlar eklendikçe sidebar'daki başlangıç sayılarını da güncel tutmak iyi bir pratiktir ama zorunlu değildir.

---

## 7. stats Bölümünü Güncelleme

`index.html`'in üstündeki istatistik bölümü de güncellenmelidir:

```html
<div class="stats">
    <div class="stats__item"><div class="stats__val">300</div><div class="stats__label">Karar</div></div>
    <div class="stats__item"><div class="stats__val">XX</div><div class="stats__label">Onama</div></div>
    <div class="stats__item"><div class="stats__val">XX</div><div class="stats__label">Bozma</div></div>
    <div class="stats__item"><div class="stats__val">XX</div><div class="stats__label">Düz. Onama</div></div>
    <div class="stats__item"><div class="stats__val">XX</div><div class="stats__label">Red</div></div>
</div>
```

---

## 8. Kontrol Listesi (Her Karar İçin)

- [ ] Doğru `data-sonuc` kodu girildi mi?
- [ ] `data-tags` ve görünen `.tag` span'ları **birebir aynı** mı?
- [ ] Karar özeti 3-5 cümle ve hukuki terminoloji içeriyor mu?
- [ ] Konu başlığı kararın özünü yansıtıyor mu?
- [ ] Yargıtay doküman linki doğru mu?
- [ ] Esas No / Karar No / Tarih formatı doğru mu?
- [ ] Detay sayfası (`kararlar/NO.html`) oluşturuldu mu?
- [ ] En az 2 etiket eklendi mi?
- [ ] Etiketler mevcut listeden mi seçildi?
