# Solder void detection of bottom terminated components on printed circuit board for low-resolution x-ray images

Son yıllarda elektronik endüstrisinin gelişmesiyle beraber baskılı devre kartlarının ve elektronik komponentlerin önemi de
hızla artmıştır. Kartların üzerinde kullanlan kurşunsuz lehim beraberinde
çeşitli problemleri getirmiştir. Ana problemlerden birisi ise
lehim bağlantılarında ortaya çıkan boşluk sorunudur. (void) Lehim içi boşluklar reflow lehimleme sürecinde lehim
içerisinde ortaya çıkan gazların sıkışması nedeniyle
oluşmaktadır.

## 1. Problem 

- düşük çözünürlüklü/karşıtlı imgeler,
- farklı boyutlarda oluşan lehim boşlukları
- homojen parlaklıkla dağılmamış imgeler
- aynı noktada örtüşen farklı tip lehim boşlukları

## 2. Pipeline

- X-Işını Görüntüleme Sistemi ile X-Ray görüntüsünün çıkarılması
- Lehim Boşluklarının Tespiti

### 2.1 X-Işını Görüntüleme Sistemi ile X-Ray görüntüsünün çıkarılması

X-ışını cihazları; radyasyon yayan ve elektrikten aldığı güç
ile x-ışını üreten bir X-ışını jeneratörüne sahip cihazlardır. Cihaz içinde x ışın kaynağı ve bu
kaynağın karşısında ışınları algılayan bir detektör ve kamera
grubu bulunmaktadır.

### 2.2 Lehim Boşluklarının Tespiti  
Temel olarak kullanılan teknikler şunlardır : 

* 1) Sobel Kenar Bulma Algoritması
* 2) Histogram Eşitleme
* 3) Genişletme
* 4) Eşikleme

Önerilen method ise :

* Real time Image 
* Histogram Eşitleme
* Sobel Algoritması
* Erozyon Filtresi
* Boşluk Doldurma
* Dilate Işlemi
* Matris İşlemleri
* Segmented Image

## 3. Result  
![image](https://user-images.githubusercontent.com/57320216/184603651-056be015-2d05-4d13-9649-394c9b6d9b43.png)
