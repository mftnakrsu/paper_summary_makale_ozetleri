# Comparison of Faster-RCNN, YOLO, and SSD for Real-Time Vehicle Type Recognition


Dünya nufüsü ve paralelinde araç sayısı arttıkça, sosyal yapı karmaşıklaştıkça ve yeni ulaşım sistemi ortaya çıkıyor. Çeşitli araçlar, yolllar ve otoparklarda belirdi. Her biri araç tipine  ve kapasitesine göröe sınıflandırılabilir. Yol sürüş ücretleri ve otopark ücretleri araca göre farklılık göstermektedir. olası çevresel koşulları azaltmak için kirliliği ve yol kaynaklarını verimli kullanmaktır. Eğer otomatik araç tipi tanıma mümkündür, yol ücretlerini veya park yönetim ücretlerini toplamak
uygun olabilir. bu makale bu nedenle geliştirilmiştir. Korea Expressway Corporation araçlarının tanınması için yazılmıştır.

# 1.2 Kullanılan algoritmalar

- Faster R-CNN
- YOLO
- SSD

# Veriseti

|Labeling Name|TRAIN set |TEST set|
|--|----|---|
|car |1447 |276|
|mini_van| 244 |55|
|big_van |33 |8|
|mini_truck| 516 |163|
|truck| 94| 27|
|compact| 286 |39|

# Donanım : 

- GeForce RTX 2080ti.

# Result

### Performance of YOLO v4 model
|Label |Average Precision |True Positive|False Positive|
|--|----|---|-|
|car |98.08% |273|25|
|mini_van| 94.93% |53|5|
|big_van |100.0% |8|0|
|mini_truck| 99.04% |162|4|
|truck| 98.52%| 27|5|
|compact| 98.59% |36|1|

### Performance of Faster R-CNN model
|Label |Average Precision |True Positive|False Positive|
|--|----|---|-|
|car |93.2% |262|17|
|mini_van| 87.2% |52|41|
|big_van |100.0% |8|1|
|mini_truck| 99.7% |164|16|
|truck| 100.0%| 27|2|
|compact| 80.3% |25|10|

### Performance of SSD model
|Label |Average Precision |True Positive|False Positive|
|--|----|---|-|
|car |92.7% |257|34|
|mini_van| 84.3% |29|1|
|big_van |87.5% |7|0|
|mini_truck| 97.9% |151|0|
|truck| 94.9%| 21|5|
|compact| 85.8% |32|15|

### FPS of Deep Learning Models

|| YOLO v4 |SSD|Faster R-CNN|
|--|----|---|-|
|FPS|82.1|105.14|36.32|


### FPS of Deep Learning Models

|Models|F1 Score |Precision |Recall|mAP|
|--|----|---|-|-|
|YOLO|0.96|0.93|0.98|98.19|
|SSD|0.88|0.90|0.87|90.56|
|Faster R-CNN|0.90|0.86|0.94|93.40|

Sonuçlarda görüldüğü gibi, two stage detection algoritmalarından olan Faster R-CNN 93.40%, one stage detection algoritmalarından olan YOLO v4 98.19%, SSD ise 90.56 doğruluk değeri elde edilmiştir. Her ne kadar Faster R-CNN in doğruluk değeri yüksek olsa da hız bakımından YOLO'nun gerisinde kalmıştır. SSD'nin de keza FPS'i fazla olmasına rağmen doğruluk değeri bakımından diğer algoritmaların gerisinde kalmıştır. Bu sebeple Korea Expressway Corporation araçları için en uygun model YOLO v4 olarak seçilir. 
