# DroneTespit 🚁

Bu proje, Ocak 2025 tarihli Örüntü Tanıma dersi projesidir. Görüntü tabanlı **örüntü tanıma** teknikleriyle dronların tespit edilmesini amaçlamaktadır. Çalışmada farklı görüntü işleme yöntemleri ve makine öğrenmesi algoritmaları bir araya getirilmiştir.  

## Özet
Projede özellikle **Destek Vektör Makineleri (SVM)** ve **Random Forest (RF)** algoritmaları kıyaslanmıştır. Kullanılan veri seti ve problem özelinde **SVM daha yüksek doğruluk ve genelleme başarısı göstermiştir**. RF algoritması ise güçlü bir ensemble yöntem olmasına rağmen, eğitim sürecinde **overfitting (aşırı öğrenme) riski** taşımış ve test verisinde daha düşük performans sergilemiştir.  

Sonuç olarak, bu proje kapsamında **kazanan algoritma SVM** olmuştur.  

## Veri Seti
- **Pozitif görüntü sayısı:** 4012  
- **Negatif görüntü sayısı:** 3010  
- **Toplam görüntü:** 7022  
- Görüntü boyutları: (150, 150)  
- Sınıf dağılımı: [3010, 4012]  
- Dataset Releases kısmındadır. Pozitif ve Negatif verileri çekip istediğiniz klasöre koyarak çalışabilirsiniz.

## Ön İşleme ve Öznitelik Çıkarımı
- **Gaussian Blur:** Gürültü azaltma ve daha temiz kenar bilgisi elde etme.  
- **HOG (Histogram of Oriented Gradients):** Kenar ve şekil bilgisi çıkarımı.  
  - İlk öznitelik boyutu: 1764  
  - PCA sonrası boyut: 500 (korunan varyans: %94.54)  
- **LBP (Local Binary Patterns):** Doku bilgisi çıkarımı.  
  - Öznitelik boyutu: 18  
- **HOG + LBP birleştirme:** Toplam öznitelik boyutu: 518  
- **SMOTE:** Sınıf dengesizliğini gidermek için azınlık sınıfına sentetik örnekler eklenmiştir.  

## Eğitim / Doğrulama / Test Sonuçları

|              Model              | Train Accuracy | Validation Accuracy | Test Accuracy |
|---------------------------------|----------------|---------------------|---------------|
| **SVM (rbf)**                   | 0.987          | 0.946               | **0.952**     |
| **RF (100 ağaç, max_depth=10)** | 0.991          | 0.918               | 0.909         |

## Sonuç
- **SVM:** Daha iyi genelleme, yüksek doğruluk, test setinde %95.2 başarı.  
- **RF:** Eğitim verilerinde (%99.1) ile overfit eğilimi göstermiştir. Testte overfit olasılığı güçlenmiştir.  
- **Ön işleme adımları (Gaussian Blur, HOG, LBP, PCA, SMOTE)** model başarısını artıran kritik bileşenlerdir.  

Bu nedenle, proje ve veri seti özelinde **SVM tercih edilmiştir**.
