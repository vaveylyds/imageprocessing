# Animals with Attributes 2 Sınıflandırma Projesi

Bu proje, **Animals with Attributes 2** veri seti kullanılarak hayvan türlerini sınıflandırmak için bir Derin Sinir Ağı (CNN) modeli geliştirmeyi amaçlar. Veri işleme, model eğitimi ve değerlendirme aşamalarını içerir.

## Proje Amacı

Bu proje, derin öğrenme teknikleri kullanarak seçilen hayvan sınıflarını doğru şekilde sınıflandırmayı hedeflemektedir. Ayrıca, modelin genelleme kapasitesini değerlendirmek ve gerçek dünya verilerine karşı dayanıklılığını analiz etmek de amaçlanmıştır.

## Proje Yapısı

### 1. Veri İşleme
- **Sınıflar:** `collie`, `dolphin`, `elephant`, `fox`, `moose`, `rabbit`, `sheep`, `squirrel`, `giant+panda`, `polar+bear`.
- **Boyutlandırma:** Görseller **128x128 piksel** boyutuna yeniden boyutlandırıldı.
- **Normalizasyon:** Piksel değerleri `[0, 1]` aralığına normalize edildi.
- **Etiketleme:** `LabelEncoder` ile sınıf etiketleri sayısallaştırıldı.
- **Ayrım:** Eğitim (%70) ve test (%30) olarak veri seti bölündü.
- **Kaydedilen Dosyalar:** `x.npy` ve `y.npy`.

### 2. Veri Artırma
- `ImageDataGenerator` ile:
  - Döndürme, yakınlaştırma, yatay çevirme ve kaydırma işlemleri uygulandı.
  - Veri çeşitliliği artırılarak modelin dayanıklılığı geliştirildi.

### 3. Model Mimarisi
- **CNN Tasarımı:**
  - 4 konvolüsyon katmanı (32, 64, 128, 256 filtre).
  - Her katmandan sonra `BatchNormalization` ve `MaxPooling`.
  - Aşırı öğrenmeyi önlemek için `Dropout` katmanları.
- **Çıkış Katmanı:** Tam bağlı (512 nöron) ve sınıf sayısına uygun softmax.
- **Optimizasyon:** Adam algoritması (Learning Rate: 0.001).
- **Kayıp Fonksiyonu:** Categorical Crossentropy.
- **Early Stopping:** En iyi model ağırlıkları geri yüklendi.

### 4. Model Eğitimi ve Değerlendirme
- **Eğitim:** 20 epoch boyunca, 32 batch boyutuyla.
- **Performans:** Test doğruluğu: **%72.06**.
- Eğitim ve doğrulama süreçleri görselleştirildi.

### 5. Sonrası Değerlendirme
- **Manipüle Edilmiş Veriler:** %11.38 doğruluk.
- **Beyaz Dengesi Uygulanan Veriler:** %11.28 doğruluk.

## Ana Bulgular

- **Model Performansı:**
  - Orijinal test veri setinde iyi doğruluk (%72) elde edildi.
  - Işık manipülasyonları gibi farklı durumlarda düşük performans gözlemlendi.
  - Beyaz dengesi uygulanması performansı bir miktar artırdı.

- **Zorluklar:**
  - Doğrulama doğruluğu, eğitim doğruluğundan erken ayrıldı (overfitting belirtisi).
  - Manipüle edilmiş verilere karşı genelleme kapasitesi yetersiz kaldı.

## Gelecek Çalışmalar ve İyileştirme Önerileri

1. **Veri Artırma**
   - Eğitim sırasında parlaklık, kontrast ve renk manipülasyonları eklenebilir.
   - Histogram eşitleme veya adaptif histogram gibi gelişmiş artırma yöntemleri uygulanabilir.

2. **Model Geliştirmeleri**
   - ResNet veya EfficientNet gibi gelişmiş modeller kullanılabilir.
   - Dropout ve L2 düzenlendirici oranları optimize edilerek overfitting azaltılabilir.

3. **Genelleme ve Değerlendirme**
   - Gerçek dünya verileriyle test edilmelidir.
   - Manipüle edilmiş veriler eğitim sürecine dahil edilerek modelin dayanıklılığı artırılabilir.

## Sonuçlar Özeti

| Metrik                  | Orijinal Test Verisi | Manipüle Edilmiş Veri | Beyaz Dengesi Uygulanan Veri |
|-------------------------|----------------------|-----------------------|-----------------------------|
| Doğruluk                | %72.06              | %11.38               | %11.28                     |
| Kayıp                   | 1.00                | 141.78               | 138.91                     |

## Sonuç
Bu proje, hayvan türlerini sınıflandırmak için bir makine öğrenimi hattını başarılı bir şekilde ortaya koymuştur. Model, orijinal veri setinde iyi bir performans göstermiştir ancak veri çeşitliliği ve genelleme kapasitesini artırmak için daha fazla iyileştirme yapılabilir.

## Kaggle notebook linki: https://www.kaggle.com/code/zeynepavu/aygazgoruntuisleme
