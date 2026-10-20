# 🌍 Karbon Emisyon Tahmini ve Şirket Segmentasyonu

Bu proje, tarihsel üretim ve emisyon kayıtlarından **toplam karbon emisyonunu tahmin etmeyi** ve kuruluşları **operasyonel emisyon profillerine göre gruplamayı** amaçlayan bir Python/Jupyter Notebook çalışmasıdır.

## 🎯 Projenin kapsamı

- **Emisyon tahmini:** Yıl, üretim miktarı, ürün türü ve kuruluş türünü kullanarak `total_emissions_MtCO2e` değişkenini **XGBoost Regressor** ile tahmin etme.
- **Veri hazırlama:** Eksik değerleri doldurma, kategorik değişkenleri `LabelEncoder` ile sayısallaştırma ve eğitim/test ayrımı (%80/%20).
- **Değerlendirme:** R² metriği ve gerçek/tahmin edilen değerlerin saçılım grafiği.
- **Segmentasyon:** Gaz yakma, havalandırma, kaçak metan ve tesisin yakıt kullanımına ilişkin emisyon özelliklerini `StandardScaler` ile ölçekleyip **K-Means** ile kümeleme.
- **Küme sayısı analizi:** Elbow yöntemi ve silhouette skoru; notebook'ta hem `k=3` hem `k=2` deneyleri var.

## 🛠️ Teknolojiler

Python · Jupyter Notebook · Pandas · NumPy · Scikit-learn · XGBoost · Matplotlib · Seaborn

## 📁 Dosya yapısı

```text
Karbon-Emisyonu-Yapay-Zeka/
├── yapay_zeka.ipynb
├── emissions_high_granularity.csv
├── Sirket_Segmentasyon_Sonuclari.csv
├── requirements.txt
├── .gitignore
└── README.md
```

| Dosya | İşlev |
|---|---|
| `yapay_zeka.ipynb` | Veri analizi, XGBoost regresyonu, K-Means ve grafikler |
| `emissions_high_granularity.csv` | Kaynak emisyon/üretim kayıtları |
| `Sirket_Segmentasyon_Sonuclari.csv` | Notebook'ta oluşturulmuş segmentasyon çıktısı |
| `requirements.txt` | Gerekli Python paketleri |

## 🚀 Kurulum

1. Projeyi indirin veya klonlayın.
2. Proje klasöründe terminal açın.
3. Bağımlılıkları kurun:

```bash
python -m pip install -r requirements.txt
```

4. Jupyter Notebook'u başlatın:

```bash
jupyter notebook yapay_zeka.ipynb
```

5. Hücreleri sırasıyla çalıştırın. CSV dosyaları notebook ile **aynı klasörde** olmalıdır.

## 📊 Kaydedilmiş sonuçlar

Notebook çıktısında regresyon modeli için **R² = %98,72** (yaklaşık **0,9872**) yer alıyor. Bu değer notebook'un kayıtlı çalıştırmasına aittir; bu GitHub paketini oluştururken eğitim yeniden çalıştırılmamıştır. Veri setinde **15.797** satır ve %80/%20 eğitim/test bölünmesi kullanılmıştır.

Kümeleme bölümünde silhouette sonuçları arasında `k=2` için yaklaşık **0,955**, `k=3` için **0,837** kayıtlıdır. Notebook önce 3 kümeli, daha sonra 2 kümeli alternatif bir deneme içermektedir; sonuç CSV'si ara aşamada üretilmiştir. Küme etiketleri uzman görüşü olmadan doğrudan çevresel risk derecesi sayılmamalıdır.

## ⚠️ Sınırlamalar ve notlar

- Bu çalışma **deneyseldir**; gelecekteki emisyonlar için dış doğrulama yapılmamıştır.
- Kategorik kodlama ve tek eğitim/test bölünmesi sonucunda genelleme gücü farklı veri kaynaklarında değişebilir.
- Notebook'taki küme isimleri (`Düşük Riskli`, `Yüksek Metan Salan` vb.) analitik etiketlerdir; düzenleyici veya bilimsel bir risk sertifikası değildir.
- Veri kaynağının kullanım/atıf koşulları GitHub'da yayınlamadan önce ayrıca doğrulanmalıdır. CSV içindeki `source` sütunu kayıt bazında kaynak açıklamaları içerir; bu tek başına veri setinin lisansını göstermez.

## 👨‍💻 Geliştirici

[Muhammet Ali Bayrak](https://github.com/MuhammetAliBayrak61)

---
**Durum:** Notebook tabanlı makine öğrenmesi ve kümeleme analizi. Ayrı bir web uygulaması veya API bulunmuyor.
