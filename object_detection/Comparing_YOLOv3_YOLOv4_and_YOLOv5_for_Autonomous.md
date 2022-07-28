# Comparing YOLOv3, YOLOv4 and YOLOv5 for Autonomous Landing Spot Detection in Faulty UAVs


## Öz

Günümüzde kentsel yerleşimlerde insansız hava aracının arıza yapması büyük bir problemdir. Bu problemi aşmak için 3 aşamalı bir plan izlenir: 

İHA arızasının tespiti ➡️ potansiyel iniş noktalarının tespiti ➡️ insansız hava aracının bulunan iniş noktasına yönlendirilmesi. 

Bu yüzden makalenin ana konusu uçuş arızasının yaşanması durumunda güvenli iniş noktalarını nesne tespiti(object detection) ile tespit etmek. Aynı zamanda nesne tespiti üzerine güncel derin öğrenme yaklaşımlarını sınamak. Sistemi gerçekleyebilmek için testleri hem gömülü cihazda hem de RTX ekran kartına sahip bir bilgisayarda denenmiş.


## Kullanılan Algoritmalar
- YOLOv3
- YOLOv4
- YOLOv5l

## Eğitim ve Model Detayları

|Model ismi|Backbone| Framework |Optimizer | lr | momentum| 
|--|--|--|--|--|--|
|YOLOv3	 |Darknet53|Darknet|SGD | 0.001| 0.9|
|YOLOv4	|CSPdarknet53|Darknet|SGD | 0.001| 0.9|
|YOLOv5l |CSPdarknet53|Pytorch| SGD | 0.001 | 0.9|

## Veriseti
[DOTA](https://captain-whu.github.io/DOTA/tasks.html) adı verilen Google Earth, GF-2 and JL-1 uydularıdan alınan, toplamda 11 bin fotoğraf barındıran geniş bir verisetiyle eğitim ve test gerçekleşmiş. Verisetinin en güncel hali 18 sınıf ve RGB, gri tonlamada fotoğraflar bulundurmaktadır. Veriseti bir tek nesne tespitine değil, segmentasyon, poz tahmini gibi konulara da hizmet etmektedir.


## Kullanılan Donanım
Eğitim için Google Colab'de Tesla P100-PCIE-16GB GPU'su kullanılmış. 
Test kısmında 1.1'de bahsedildiği üzere 2 farklı donanım kullanılıyor.
|Donanım ismi |GPU|CPU|RAM| 
|--|--|--|--|
|PC|NVIDIA® GeForce® RTX 2070 SUPERTM Turing| 10th Gen. Intel® CoreTM i7-10750H|32GB|
|Jetson Xavier NX|NVIDIA Volta architecture with 384 NVIDIA®CUDA® cores|6-core NVIDIA Carmel ARM®v8.2 | 8GB|

## Sonuç

![img](/imgs/YOLO-comparison-for-UAV.png)


Yapılan teslerin sonucunda YOLOv3'de yüksek precision düşük recall değerleri görülmüş. YOLOv4 ve YOLOv5l'de ise daha dengeli precision ve recall değerleri gözlemlenmekte. Doğruluk v5, v4, v3 şeklinde giderken FPS de ters orantılı şekilde v5'den v3'e azalmaktadır. Makalenin yazarları en yüksek doğruluğa sahip olduğu için YOLOv5l modelini seçmeyi tercih etmişler.