# Comparison of Yolo, SSD, Faster RCNN for Real Time Tennis Ball Tracking for Action Decision Networks

## 1.1  Öz
Tenis topunun vurulduktan sonra izleyeceği yörüngeyi tahmin etmek, topun hızını, çıktığı maksimum yükseklik vb. parametreleri bulmak aynı zamanda Yolo,SSD ve faster RCNN kıyaslaması.

Tenis topunun hızını bulmak için servis atıldıktan sonra atışın ilk 4 noktası alınır ve 4 nokta arasındaki *öklid mesafesi* hesaplanır.


$$ ServisHızı=   {öklidmesafesi / GeçenZaman}$$
Bunun gibi bazı parametreleri hesaplayıp kullanıcı arayüzüyle sonuçları görselleştirmiş ve farklı nesne tespit modellerini kıyaslanmıştır.
## 1.2 Kullanılan Algoritmalar
	- YOLO
	- Faster R-CNN
	- SSD

## 1.3 Veriseti
Custom veriseti kullanılmış olup veriseti boyutu hakkında detay verilmemiştir. Tenis kortunda insan boyuna yakın yükseklikte yerleştirilen tripoddan farklı açılarda bilinmeyen sayıda resim ve video çekilmiş.


## Donanım:
- NVIDIA GTX 1660 Ti

## Sonuç
![image](/imgs/tennis_ball_tracking_result.png)

3 algoritmanın kıyaslanmasında SSD daha verimli ve hesaplama hızına göre kıyaslandığında daha yüksek doğruluğa sahip model olmuş.
