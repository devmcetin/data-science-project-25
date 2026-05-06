# Data Science Project 25 — TatlıDükkanı Satış Dashboard

**Modül**: Power BI Temelleri (Module 301) • **Süre**: 2-3 saat
**Dersler**: Ders 1 (PowerBI Nedir?) sonrası

---

## 🎯 Proje Senaryosu

İstanbul'da 5 şubesi olan **TatlıDükkanı** zincirinde **junior data analyst** olarak işe başladın. Yöneticin "geçen yılla bu yılı karşılaştıran tek sayfalık bir satış dashboard'u" istiyor — yarın yönetim kuruluna sunulacak.

Bu projede **Ders 1'de gördüğümüz 7 farklı chart tipini** kullanarak satış verilerinden bilgi çıkaracaksın.

---

## 📊 Veri Setleri

`veri-setleri/` klasöründe 2 CSV var (toplam 730 satır):

| Dosya | Satır | Açıklama |
|-------|-------|----------|
| `tatlidukkani_2024.csv` | 365 | 2024 yılı tüm satışlar |
| `tatlidukkani_2025.csv` | 365 | 2025 yılı tüm satışlar (karşılaştırma) |

**Sütunlar**:
```
Tarih, Sube, Musteri_ID, Urun_Kategorisi, Urun_Adi,
Miktar, Birim_Fiyat, Toplam_Tutar, Musteri_Tipi, Odeme_Yontemi
```

**Kategoriler**: Pasta, Kurabiye, İçecek, Dondurma, Kek
**Şubeler**: Beşiktaş, Kadıköy, Şişli, Bakırköy, Üsküdar
**Müşteri tipleri**: Üye (%10 indirim alır), Misafir
**Ödeme yöntemleri**: Nakit, Kredi Kartı, Banka Kartı, Yemek Kartı

---

## 📋 Görevler

Power BI Desktop'ta aşağıdaki **7 chart**'ı içeren tek bir dashboard yap:

### 1. **Bar / Column Chart** — Şubelere Göre Toplam Satış
- X ekseni: Sube
- Y ekseni: SUM(Toplam_Tutar)
- 2024 + 2025 toplam ya da yıl bazında karşılaştırma

### 2. **Line Chart** — Aylık Satış Trendi
- X ekseni: Ay (Tarih'ten ay çıkar)
- Y ekseni: SUM(Toplam_Tutar)
- 2024 vs 2025 — iki seri (legend)

### 3. **Pie / Donut Chart** — Ödeme Yöntemi Dağılımı
- Dilimler: Odeme_Yontemi
- Yüzdelikler görünsün

### 4. **Ribbon Chart** — Kategori Sıralamasının Aylık Değişimi
- Eksen: Ay
- Değer: SUM(Toplam_Tutar)
- Lejand: Urun_Kategorisi
- Yaz aylarında dondurma yükselişi, kışın içecek görsel olsun

### 5. **Scatter Plot** — Şube × Müşteri Davranışı
- X ekseni: AVG(Miktar) per müşteri
- Y ekseni: SUM(Toplam_Tutar) per müşteri
- Renk: Sube (5 farklı renk)
- Outlier'lar (en çok harcayan) göze çarpsın

### 6. **Funnel Chart** — Müşteri Tipi Hunisi
- Aşamalar: Tüm sipariş → Misafir → Üye → Üye + Premium kategoriler
- Üyelerin daha çok harcadığını göster

### 7. **KPI Card'lar** — 3 Önemli Metrik
- **Toplam Ciro 2025**: SUM(Toplam_Tutar) where Tarih in 2025
- **Ortalama Sipariş**: AVERAGE(Toplam_Tutar)
- **Tekrar Eden Müşteri Oranı**: 2024 ve 2025'te alışveriş yapan müşteri sayısı

---

## 📦 Proje Kurulumu

```bash
git clone <your-fork-url>
cd data-science-project-25
```

Power BI Desktop'a yükleme:
- **Get Data → Text/CSV** → `tatlidukkani_2024.csv` ve `tatlidukkani_2025.csv`'yi tek tek yükle
- Transform Data → sütun tiplerini kontrol et (Tarih → Date, sayılar → Decimal)
- (Opsiyonel) İki tabloyu birleştir: **Append Queries** → tek tablo `tatlidukkani_tum`

---

## 📤 Submission — Pumble'dan Ekran Görüntüsü Gönder

1. **Dashboard'u tek sayfada topla** — 7 chart yan yana sığsın
2. **Tüm dashboard'un ekran görüntüsünü al** (full screen, 1080p+)
3. **Pumble'a gönder** → kanal: `#proje-teslim`
4. Mesaj formatı:
   ```
   DS-25 Submission
   Repo: <senin GitHub fork URL'in>
   Ek: dashboard.png
   ```
5. Eğitmen kontrol edip "geçti" işaretler — Kaizu'da skor 100 görünür

---

## ✅ Başarı Kriterleri

Eğitmen kontrol edecek:
- [ ] 7 chart hepsi var ve doğru veri
- [ ] 2024 vs 2025 karşılaştırması yapılabiliyor
- [ ] Dashboard tek sayfada toplu (overlapping yok)
- [ ] Renk seçimi tutarlı (tek bir tema)
- [ ] Slicer (Sube veya Urun_Kategorisi) eklenmiş ve interaktif
- [ ] Mevsimsellik göze çarpıyor (yaz dondurma, kış içecek)

---

## 💡 İpuçları

- **Tema seç**: Power BI'ın hazır temalarından bir tatlı dükkanı için pastel renkler iyi durur
- **Append Queries**: 2024 + 2025'i tek tabloda birleştirip "Yıl" kolonu ile filter edebilirsin
- **Tarih hierarchy**: Power BI otomatik Year/Quarter/Month hierarchy oluşturur — line chart'ta drill-down kullan
- **Conditional formatting**: KPI kartlarında 2024'e göre büyüme yüzdesi (yeşil/kırmızı) göster

---

## 🚫 Dikkat

- `veri-setleri/` içindeki CSV'leri değiştirme
- `.pbix` dosyasını commit etmene gerek yok (büyük dosya, .gitignore'da exclude)
- Eğitmen kabul kriterleri: görsel kalite + doğru veri analizi
