# Comparison of Brain Tumor Detection in MRI Images Using Straightforward Image Processing Techniques and Deep Learning Techniques 

## ÖZET 

Beyin tümörleri, insan ölümlerinin en yaygın nedenlerinden biridir. Beyin tümörlerinin erken ve doğru teşhisi etkili bir tedavi için oldukça önemlidir. Beyin tümörlerinin tespitinde bilgisayarlı tomografi (CT) taramaları ve  Manyetik rezonans görüntüleme (MRI) kullanılır. Ancak, en etkili verileri sağlayan Manyetik rezonans görüntülemedir(MRI). 

Hayatımızın ve sektörün her alanına girmeye başlayan yapay zeka uygulamaları sağlık sektöründe de çeşitli yararlar sağlamaktadır. Bu makalede MRI verilerinden beyin tümörünün tespitinde görüntü işleme teknikleri ile  daha önceden yapılmış derin öğrenme tekniğiinin karşılaştırılması yapılmıştır.

## I. GİRİŞ


Beyin tümörü hayatı tehdit eden ölümcül bir hastalıktır. Bu hastalık merkezi sinir sistemini ciddi şekilde bozabilecek beklenmedik şekilde yükselen beyin hücreleri kümesi olarak tanımlanır. Hepimizin bildiği üzere iyi huylu ve kötü huylu olarak ikiye ayrılır. İyi huylu tümörler büyüme göstermezler ve çok büyük zararlar vermezken, kötü huylu tümörler ölüme yol açabiliyor. Bu nedenle, MRI verileri kullanılan insanlarda beyin tümörü tespiti, önemli bir araştırma alanıdır. 

Beyin tümörü tanısında çeşitli teknikler kullanılır, bunlar; bilgisayarlı tomografi (CT), Manyetik Rezonans Görüntüleme (MRI), Pozitron Emisyonu (PET) ve Biyopsidir. MRI, manyetik alanlar ve radyo dalgaları ile çalışan MRI tarayıcılarının yardımıyla insan vücudundaki anatomi ve işleyişin resimlerini elde etme stratejisidir. Bu sebeple, bu makalede MRI verileri üzerinden görüntü işleme teknikleri kullanarak beyin tümörü tespitinin yapılması amaçlanmıştır.

![brain_tumor](https://user-images.githubusercontent.com/44112634/184890614-9039ea7c-ab04-430c-ba18-aa7972a7f065.png)


## III. METODOLOJI

Bu çalışma 2 bölümden oluşuyor;
> * Görüntü İşleme teknikleri ile tümör tespiti
> * Sonuçların derin öğrenme sonucu ile karşılaştırılması

### Görüntü İşleme teknikleri ile tümör tespiti

Bu method 4 aşamadan oluşuyor;

1. Veri Toplama
2. MRI görüntülerinin ön işlemesi
3. Kenar algılama operasyonları
4. Segmentasyon ve morfolojik operasyonlar


![methodology](https://user-images.githubusercontent.com/44112634/184890656-e01da054-e72f-4e27-9012-5ad3bf1cec6e.png)


### 1. Veri Toplama

Veriseti [Kaggle](https://www.kaggle.com/) platformu üzerinden alınmıştır. .jpg formatında 3762 görüntüden oluşmaktadır. Veriseti 13 özellikten oluşmakta ve önemli olanlar mean, variance, standard deviation, contrast ve correlation gibi değerler içermektedir.

### 2. Ön İşleme

MRI görüntülerinden gürültüler(noises) temizlenmiş, RGB formatından Grayscale formatına dönüştürülmüştür.

### 3. Kenar algılama operasyonları

Sobel  ve Canny operasyonu ile kenar algılama algoritması uygulanmıştır.

![edge_det](https://user-images.githubusercontent.com/44112634/184890689-bf07985a-0461-40f1-9f1f-7d8c900f15f3.png)


### 4. Segmentasyon ve morfolojik operasyonlar

Segmentasyon görüntü işlemenin en önemli parçalarından biri. Bu çalışmada Region-based, Thresholding (boundary-based) ve Edge-based olmak üzere 3 teknik kullanılmıştır.

![thresholding](https://user-images.githubusercontent.com/44112634/184890723-a1e5cc73-4b9e-4047-85ab-21be05d58151.png)


## Görüntü İşleme Sonuçları

MATLAB platformu üzerinde sırasıyla bu işlemler gerçekleştirilmiştir;
* MRI görüntüleri grayscale görüntüye dönüştürülmüştür.
* Gürültüler mean filtresi ile kaldırılmış ve ardından contrast iyileştirilmesi yapılmıştır.
* Sobel ve CAnny kullanılarak kenar algılaması yapılmıştır.
* Son olarak global thresholding ile görüntü segmentasyonu yapılmıştır.

![segment](https://user-images.githubusercontent.com/44112634/184890754-cc94b5e2-16fd-46e5-9a47-b0e86fe4e972.png)



## SONUÇ

Bu makale, basit bir yaklaşım kullanılarak iyi sonuçlar elde edilmesine rağmen, gelişmiş derin öğrenme tekniklerinin uygulanmasının daha iyi sonuçlar elde ettiği gerçeğini ortaya koyuyor. Daha az uygulama süresi ve farklı tümör türlerinin çok sınıflı sınıflandırması gibi kompleks durumlarda derin öğrenme modeli çok daha sağlıklı sonuçlar vermektedir. Bu çalışma, bilimsel topluluk ve araştırmacılar için hızlı bir teşhis elde etmek için yardımcı olacaktır.
