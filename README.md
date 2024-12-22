# imageprocessing

# **Hayvan Görüntüleri Sınıflandırma Projesi**

Bu proje, **Animals with Attributes 2** veri seti kullanılarak farklı hayvan sınıflarını sınıflandırmak için derin öğrenme tabanlı bir çözüm geliştirmeyi amaçlamaktadır. Projede, veriler işlenmiş, CNN modeli eğitilmiş ve manipüle edilmiş test setleriyle modelin performansı değerlendirilmiştir.

---

## **Proje Hedefi**

- **CNN Temellerini Anlamak**: Convolutional Neural Networks (CNN) kullanarak farklı hayvan türlerini sınıflandırmak.
- **Manipülasyonlara Dayanıklılık**: Modelin manipüle edilmiş test setleri üzerindeki dayanıklılığını değerlendirmek.
- **Renk Sabitliği Algoritmasının Etkisi**: Gray World algoritmasını uygulayarak modelin başarısına olan etkisini analiz etmek.

---

## **Adımlar**

### 1. **Veri Setinin Hazırlanması**
- **Kullanılan Sınıflar**: `collie`, `dolphin`, `elephant`, `fox`, `moose`, `rabbit`, `sheep`, `squirrel`, `giant+panda`, `polar+bear`.
- **Resim Seçimi**:
  - Her sınıf için ilk 650 resim seçildi.
  - Resimler `(128x128)` piksel boyutuna yeniden boyutlandırıldı ve normalize edildi.
- **Veri Bölünmesi**:
  - Eğitim ve test setleri, %70 eğitim ve %30 test olacak şekilde ayrıldı.
  - Etiketler One-Hot Encoding formatına dönüştürüldü.

---

### 2. **Veri Artırma (Augmentation)**
Eğitim setinin çeşitliliğini artırmak için aşağıdaki teknikler kullanıldı:
- Döndürme (`rotation_range=30`)
- Yatay kaydırma (`width_shift_range=0.3`)
- Dikey kaydırma (`height_shift_range=0.3`)
- Yakınlaştırma (`zoom_range=0.3`)
- Yatay çevirme

---

### 3. **CNN Modelinin Eğitilmesi**
- **Model Mimarisi**:
  - 4 adet konvolüsyon bloğu (Conv2D, MaxPooling2D, BatchNormalization).
  - Fully Connected (Dense) katmanlar ve Dropout ile aşırı öğrenmeyi önleme.
- **Ağırlıkların Optimizasyonu**: Adam optimizasyon algoritması kullanıldı.
- **Loss Function**: Categorical Crossentropy
- **Eğitim Süreci**:
  - Epoch: 20
  - Early Stopping kullanılarak en iyi ağırlıkların korunması sağlandı.

---

### 4. **Model Performansı**
- **Orijinal Test Seti**: Model, eğitim sırasında test seti üzerinde değerlendirilmiştir.
- **Manipüle Edilmiş Test Seti**: Işık parlaklığı manipülasyonları uygulanmıştır.
- **Renk Sabitliği Uygulanmış Test Seti**: Gray World algoritması ile renk sabitliği sağlanmıştır.

---

## **Sonuç**
- Manipüle edilmiş test setlerinde modelin doğruluk oranında düşüş gözlemlendi. Ancak, renk sabitliği algoritması bu düşüşü kısmen azalttı.
- Eğitim setinde veri artırma ve düzenleme işlemleri modelin genel başarısını artırmıştır.
- Modelin farklı manipülasyonlara dayanıklılığını artırmak için daha ileri yöntemler geliştirilebilir.

---

## **Gelecekteki İyileştirme Önerileri**
1. **Daha Derin Ağlar**: Daha karmaşık CNN mimarileri ile doğruluk artırılabilir.
2. **Veri Çeşitliliği**: Eğitim setine daha fazla manipüle edilmiş veri eklenebilir.
3. **Renk Sabitliği**: Daha gelişmiş renk sabitliği algoritmaları (ör. Retinex) denenebilir.

---


## **Grafiklerle Eğitim Süreci**
Bu grafikler, modelin eğitim ve doğrulama doğruluğu ile kaybını göstermektedir.

- **Doğruluk (Accuracy)**:
  - Eğitim doğruluğu, her epoch'ta düzenli olarak artmıştır.
  - Doğrulama doğruluğu dalgalanma göstermiştir.
- **Kayıp (Loss)**:
  - Eğitim kaybı sürekli düşmüş, doğrulama kaybında dalgalanmalar gözlenmiştir.

---

Bu proje, derin öğrenme modellerinin manipülasyonlara dayanıklılığını incelemek ve geliştirmek için temel bir adım olmuştur.


## **Gelecekteki İyileştirme Önerileri**
1. **Daha Derin Ağlar**: Daha karmaşık CNN mimarileri ile doğruluk artırılabilir.
2. **Veri Çeşitliliği**: Eğitim setine daha fazla manipüle edilmiş veri eklenebilir.
3. **Renk Sabitliği**: Daha gelişmiş renk sabitliği algoritmaları (ör. Retinex) denenebilir.
    

## **Not: Proje Durumu**
Bu proje, verilen süre içerisinde tamamlanamamış olsa da, önemli aşamalar üzerinde çalışılmış ve birçok temel adım başarıyla gerçekleştirilmiştir. Şu ana kadar yapılan çalışmalar:

1. Veri setinin hazırlanması ve sınıflandırılması.
2. Veri artırma işlemleri ile eğitim setinin zenginleştirilmesi.
3. Convolutional Neural Network (CNN) modeli tasarımı ve eğitimi.
4. Manipüle edilmiş test setlerinin hazırlanması.
5. Renk sabitliği algoritmasının uygulanması ve test sürecinin başlatılması.

**Eksik Kalan Adımlar**:
- Manipüle edilmiş ve renk sabitliği uygulanmış test setleriyle model performansının tam analizi.
- Sonuçların detaylı bir şekilde raporlanması ve görselleştirilmesi.


Kaggle Notebook Linki: https://www.kaggle.com/code/zeynepavu/image
