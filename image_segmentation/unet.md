# U-Net Özet

Derin öğrenme (DL) tabanlı semantik segmentasyon yöntemi, son yıllarda görüntü bölütlemede en
gelişmiş performansı sağlamaktadır. Daha spesifik olarak, bu teknikler tıbbi görüntü sınıflandırma,
segmentasyon ve algılama görevlerine başarıyla uygulanmıştır. Bu makalede, U-Net'e dayalı bir
Tekrarlayan Evrişimli Sinir Ağı (RCNN) ve bir Tekrarlayan Artık U-Net modellerine dayalı Evrişimli Sinir Ağı
(RRCNN) anlatılmaktadır. Bu iki metod sırasıyla RU-Net ve R2U-Net olarak adlandırılır.

  * RRCNN kullanımının çeşitli avantajlarından ilki, artık (residual) birim derin mimariler eğitmek için
  daha uyumludur.  
  * İkincisi, tekrarlayan artık evrişim katmanları ile özellik birikimi, segmentasyon görevleri için daha
  iyi özellik temsili sağlar.  
  * Üçüncüsü, tıbbi görüntü segmentasyonu için daha iyi performansa sahip aynı sayıda ağ
  parametresiyle daha iyi U-Net mimarileri tasarlamamızı sağlar.
  
  ![The-architecture-of-Unet](https://user-images.githubusercontent.com/57320216/179573984-d77a1328-c191-4bf1-be99-fc35bbff297f.png)


Bu çalışmada değerlendirilen dört farklı mimari vardır.
![fdff](https://user-images.githubusercontent.com/57320216/179574715-c4bccdcf-5de9-4e2e-8bcb-0526e28a8de5.png)


İlk olarak, UNet'in birincil versiyonunda bulunan kırpma ve kopyalama yöntemine alternatif olarak ileri
konvolüsyon katmanları ve özellik birleştirme içeren U-Net uygulanmıştır. Bu modelin temel evrişim
birimi Şekil 4(a)'da gösterilmektedir. İkinci olarak, genellikle artık U-net (ResU-Net) olarak adlandırılan ve
Şekil 4(c)'de gösterilen, artık bağlantıya sahip ileri evrişimli katmanlara sahip U-Net kullanılır. Üçüncü
mimari, Şekil 4(b)'de gösterildiği gibi ileri tekrarlayan konvolüsyonel katmanlara sahip U-Net'tir ve RUNet olarak adlandırılır. Son mimari ise Şekil 4(d)'de gösterildiği gibi artık bağlantıya sahip tekrarlayan
konvolüsyon katmanlarına sahip U-Net'tir ve R2U-Net olarak adlandırılır. Katlanmamış RCL katmanlarının
zaman adımına göre resimsel gösterimi Şekil 5'te gösterilmektedir. Burada t=2 (0 ~ 2), bir tek
konvolüsyon katmanı ve ardından iki ardışık tekrarlayan konvolüsyon katmanı içeren tekrarlayan
konvolüsyonel işlemi ifade eder. Bu uygulamada, hem RUNet hem de R2U-Net modelleri için kodlama
biriminden kod çözme birimine özellik haritalarına birleştirme uygulanmıştır.


Önerilen yöntem; Retina görüntülerinde kan damarı segmentasyonu, Cilt kanseri segmentasyonu ve
Akciğer lezyonu segmentasyonu kıyaslayıcı verisetleri üzerinde test edilmiştir.

## Verisetlerinin Tanınması

### 1) Retinadaki Kan Damarı Segmentasyonu  
Bu tanı için 3 adet popüler veriseti bulunmaktadır: DRIVE, STARE ve CHASH_DB1. DRIVE veri seti, eğitim
için 20 örnek ve test için kalan 20 örnek olmak üzere toplam 40 renkli retina görüntüsünden
oluşmaktadır. Her orijinal görüntünün boyutu 565×584 pikseldir. İkinci dataset STARE, 20 renkli görüntü
içerir ve her görüntünün boyutu 700×605 pikseldir. Örnek sayısının az olması nedeniyle, her görüntünün
test edildiği ve kalan 19 örnek üzerinde eğitimin gerçekleştirildiği “birini dışarıda bırak” (leave-one-out)
yöntemi kullanılmıştır.
### 2) Cilt Kanseri Segmentasyonu  
Bu veri seti toplam 2000 örnek içermektedir. 1250 training örneğinden, 150 validation örneğinden ve
600 test örneğinden oluşur. Her örneğin orijinal boyutu 700×900’dır ve bu makalenin uygulaması için
256×256'ya yeniden ölçeklendirilmiştir.
### 3) Akciğer Segmentasyonu  
534 adet labellanmış 2D ve 3D BT görüntülerinden oluşur. Bu çalışmada, görüntülerin %70'i training için,
kalan %30'u ise test için kullanılmıştır. Orijinal görüntü boyutu 512×512, ancak bu uygulama için
görüntüler 256×256 piksel olarak yeniden boyutlandırılmıştır. 
