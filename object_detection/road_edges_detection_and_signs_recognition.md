# Real Time Road Edges Detection And Road Signs Recognition

Her yıl dünya çapında 1,3 milyon insan trafik kazasında hayatını kaybediyor ve 20 ila 50 milyon arasında insan yaralanıyor. Bu soruna iyi bir çözüm, çevreyi dikkate alan makineler geliştirmek olacaktır. Bu nedenle günümüzde güvenli otomobil sürüşü, küçük projelerden büyük otomobil fabrikalarına kadar birçok alanda popüler bir konu haline geliyor. Ancak bu konu aynı zamanda birçok soruyu ve sorunu da beraberinde getirmektedir. Yolun kenarlarının genişliğini tanımlamaya, yol işaretlerini, trafik ışıklarını, yayaları ve sürüşe güvenli bir şekilde katkıda bulunan diğer nesneleri tanımaya ihtiyaç vardır. Bu görevleri çözmek için birçok yöntem vardır. Bu çalışmada yol kenarlarını, yoldaki nesneleri, trafik ışıklarını ve trafik işaretlerini tespit etmek için çözüm düşünülmüştür.

# AŞAMALAR

Makale, şerit tespiti ve işaret tespiti olmak üzere iki bölümden oluşmaktadır. Kenarları tespit etmek için yaygın olarak kullanılan ve etkili bir yöntem olan Canny Edge Detection algoritması kullanılmıştır. Daha sonra şeritler Hough Dönüşümü ile tespit edilir. Yol işaretlerini tespit etmek için genellikle yüz tanımada kullanılan SURF yöntemi kullanılmıştır.  
  
![project_steps](https://user-images.githubusercontent.com/73580507/182021929-4094f67e-c50d-42d6-8b6f-240ac778f67a.png)

## 1. CANNY KENAR ALGILAMA

Görüntünün türevini alarak kenar bulur, son derece etkin olarak kullanılan bir algoritmadır.
#### 1.1 Gauss Filtresi
Gauss filtresi görüntüleri yumuşatmak ve görüntü üzerindeki gürültüyü arındırmak için kullanılır. 
Bu işlem:
- Gauss filtre katsayısı ile görüntünün konvolüsyonu sonucu gerçekleşir.  

![gauss_filter](https://user-images.githubusercontent.com/73580507/182026646-91df464a-1b6a-4735-8f18-1f9acc7545f3.png)

### 1.2 Sobel Operatörü

Sobel operatörü bir çift 3x3 konvolüsyon maskesi kullanır. Bu maskeler görüntüdeki ani ışık yoğunluk değişimi olan yerlerin belirlenmesini sağlar. Maske ile görüntünün konvolüsyonu alınır.

- Konvolüsyon Matrisi:  
![conv_mask](https://user-images.githubusercontent.com/73580507/182027728-2f2f1f73-aaf3-4244-9bd3-7533554d5294.png)

#### UYARI: Makalede verilen konvolüsyon matrisi hatalı olabilir, aşağıdaki matrisleri referans alabilirsiniz.
![image (2)](https://user-images.githubusercontent.com/73580507/182027710-c0180390-a583-4c1e-9cab-3cb270b22ad8.png)

### 1.3 Maksimum Olmayan Bastırma(NMS)

Operatörle elde edilen kenarlar kalındır. Kenarların inceltilmesi için maksimum olmayan pikseller bastırılır. Çalışma mantığı:  Görüntü teta yönünde taranır ve pikseller yerel maksimumun parçası değillerse sıfıra ayarlanır.

- Gradyan büyüklüğü formülü:  
![gradyan](https://user-images.githubusercontent.com/73580507/182027524-d53eebe8-1863-4fab-8f37-1c77d86096ef.png)
- Gradyan yönü formülü:  
![teta](https://user-images.githubusercontent.com/73580507/182027535-3d26f889-7946-424c-80b5-8fa46e68a1be.png)

**Uygulama:**  
1.Gradyan büyüklüğü ve yönü hesaplanır.  
2.Yönler en yakın 0, 45, 90 veya 135 dereceye ayarlanır.  
3.Maksimumda olmayan tüm pikselleri bastırır.  

![max_sup](https://user-images.githubusercontent.com/73580507/182027503-fed13cf2-ce8e-4222-9abb-92fd9d399a6a.png)

### 1.4 Histerezis (İkili Eşik Yöntemi)

**Uygulama:**  
Yüksek ve düşük seviye olmak üzere iki adet eşik seviyesi belirlenir.  
1.Durum: Eğer piksel değeri düşük eşiğin altında ise, 0’a çekilir.  
2.Durum: Yüksek eşiğin üzerinde ise, 1’e çekilir.  
3.Durum: İki eşik arasında ise, bu pikselin yüksek eşiği aşan bir komşusu yoksa sıfıra çekilerek kenar resminden elenir.

## 2.HOUGH DÖNÜŞÜMÜ

Hough dönüşümü bir görüntüdeki şekilleri saptamada kullanılan bir yaklaşım yöntemidir. Görüntüdeki sıfırdan farklı noktalar hough uzayında sinüzoidallere dönüştürülür. Tersi durumunda ise, hough uzayında her bir nokta görüntüde bir düz doğruya karşılık gelir.  

![hough](https://user-images.githubusercontent.com/73580507/182027277-aa2fa0c6-f00c-45b2-a0cb-7fbca1470526.png)

## 3. SURF(Speeded-Up Robust Features)

SURF, Gauss Laplasyanının (Fast-Hessian) ikili yaklaşımını kullanır.
Algoritmanın üç ana bölümü vardır:   
1. İlgi noktası tespiti  
2. Yerel komşuluk tanımı  
3. Eşleştirme  

Özellik tanımlayıcısı, ilgilenilen nokta etrafındaki haar dalgacık yanıtının toplamına dayanır.

# VERİ SETİ

Veriler, deney sırasında gerçek koşullarda kullanılan bir kameradan elde edilmiştir.

# DONANIM

Çalışma, Intel Core i5 işlemcili, CPU @ 1.7 GHz, RAM 4 GB olan bir sistem üzerinde gerçekleştirilir.

Programlama ortamı – Visual Studio 2013, Opencv 2.4.9. 

Verileri gerçek zamanlı olarak elde etmek için aşağıdaki özelliklere sahip bir web kamerası kullanılmıştır.
- 1.5Mp
- 30 FPS
- (640x480 gerçek piksel), 1024x768 piksel aralığına zoom yapabilir.

# SONUÇLAR

## 1. Şerit Tespiti

![line](https://user-images.githubusercontent.com/73580507/182026440-6ab0d92a-85ba-45ce-b51d-88b713f7c621.png)


## 2. Levha Tespiti
![image (1)](https://user-images.githubusercontent.com/73580507/182026378-1f0c1e58-83b3-46ed-8d84-83af5bedc100.png)


### EK
- Bu makale base alınarak MATLAB ortamında hazırlanmış çalışmaya [buradan](https://github.com/suhedaras/Road-Edges-Detection-and-Road-Signs-Recognition) ulaşabilirsiniz.
