#  Customer Churn Prediction & Revenue Impact Modeling

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![CatBoost](https://img.shields.io/badge/CatBoost-Machine_Learning-orange.svg)
![SHAP](https://img.shields.io/badge/SHAP-Explainable_AI-red.svg)
![Business-Value](https://img.shields.io/badge/ROI-Revenue_Protection-green.svg)

##  Executive Summary: "Protecting the Bottom Line"
Müşteri kaybı (churn), sadece bir veri problemi değil, doğrudan bir gelir problemidir. Bu proje; **CatBoost**, **SHAP (Explainable AI)** ve **Finansal Tahminleme** yöntemlerini kullanarak abonelik tabanlı bir işletmede churn nedenlerini belirlemeyi ve potansiyel gelir kaybını minimize etmeyi hedefler.

**Temel Bulgular:**
* **Risk Altındaki Gelir:** Aylık bazda yaklaşık **$213,429** tutarında tekrarlayan gelir (MRR) risk altındadır.
* **CLV Artışı:** Churn oranındaki sadece **%5'lik** bir iyileşme, Müşteri Yaşam Boyu Değeri'ni (CLV) **$244**'ten **$256.89**'a çıkarmaktadır.
* **Kritik Sinyaller:** En güçlü churn göstergeleri; aylık kontratlar, fiber optik kullanımı ve teknik destek eksikliğidir.



## 1.  İş Problemi (Business Problem)
Abonelik modellerinde mevcut bir müşteriyi elde tutmak, yeni bir müşteri kazanmaktan **5 ila 25 kat daha ucuzdur.** Bu proje şu sorulara yanıt arar:
1. Hangi müşteriler ayrılma riski taşıyor?
2. Ayrılma kararını tetikleyen temel faktörler neler?
3. Bu kaybın şirkete finansal maliyeti nedir ve nasıl önlenebilir?



## 2.  Veri Seti ve EDA (Exploratory Data Analysis)
Veri seti; demografik bilgiler, servis detayları ve finansal metrikleri içermektedir. Yapılan analizlerde öne çıkan başlıklar:

* **Tenure (Bağlılık Süresi):** İlk 6 ay, churn riskinin en yüksek olduğu "kritik eşik" dönemidir.
* **Kontrat Tipi:** Aylık kontratlı müşteriler, yıllık kontratlılara göre devasa oranda daha fazla churn etmektedir.
* **Fiyat Hassasiyeti:** Churn eden müşterilerin ortalama aylık ödemeleri daha yüksektir.



## 3.  Modelleme Stratejisi & CatBoost
Verideki kategorik değişkenlerin yoğunluğu ve dengesiz sınıf dağılımı nedeniyle **CatBoost** algoritması tercih edilmiştir.

* **Preprocessing:** `TotalCharges` sayısal tipe çevrildi, kayıp veriler temizlendi ve sınıf dengesizliği (Imbalance) `Class Weights` ile yönetildi.
* **Neden CatBoost?** Kategorik verileri işleme hızı, overfitting direnci ve yüksek tahmin gücü.

### Model Performansı:
| Metric | Score |
| :--- | :--- |
| **AUC-ROC** | ~0.84 |
| **Recall (Churn Class)** | **0.80** (Kritik: Kaçırmamamız gereken müşteriler) |
| **Accuracy** | 0.74 |



##  4. Explainable AI (SHAP Analizi)
Modelin "kara kutu" olmaması için SHAP değerleri kullanılmıştır. 

* **Global Önem:** Churn'ü tetikleyen ilk 3 özellik: **Contract Type, Internet Service ve Tenure.**
* **Local Explanation:** Bireysel bazda her müşteri için modelin neden "Churn" dediği force-plot'lar ile analiz edilebilir (Örn: Yüksek ücret + Destek hizmeti yok = Churn Riski).



##  5. Finansal Tahminleme (Revenue Impact)
Model çıktıları doğrudan dolar bazlı bir iş raporuna dönüştürülmüştür:
* **Beklenen Churn Sayısı:** 2,920 Kullanıcı
* **Riskteki Aylık Gelir:** $213,429
* **Öneri Sonrası Senaryo:** Churn %5 azaltılırsa toplam portföy değerinde ciddi bir compounding etkisi gözlemlenmiştir.



##  6. Aksiyon Planı ve Öneriler
1. **Kontrat Dönüşümü:** Aylık abonelere yıllık paketler için özel indirimler sunulmalı.
2. **Onboarding Optimizasyonu:** İlk 6 aydaki müşterilere yönelik "Hoşgeldin ve Destek" kampanyaları artırılmalı.
3. **Teknik Destek Paketleri:** Online güvenlik ve teknik destek hizmetleri, churn'ü düşürdüğü için bu servisler "bundle" paketlere dahil edilmeli.
4. **Fiber Optik Segmenti:** Bu gruptaki yüksek churn oranını düşürmek için sadakat ödülleri veya hız güncellemeleri planlanmalı.



##  Proje Yapısı
```text
churn-prediction-revenue-impact/
│
├── notebooks/
│   └── Churn_Prediction.ipynb  # EDA, CatBoost ve SHAP süreçleri
│
├── data/
│   └── Customer_Churn DataSet.csv                # Örnek veri seti (Maskelenmiş)
│
└── README.md
