Generative Adversarial Networks (GAN) fikri 2014 yılında Ian Goodfellow tarafından ortaya atılmıştır. 

# GAN Architecture

Yapısına bakıldığında iki adet neural network kullanıldığını görmekteyiz. Bunlar: Generator ve Discriminator olarak adlandırılır. Çalışma prensibi aşağıdaki örnek üzerinden anlatılabilir:

![image](https://user-images.githubusercontent.com/76012121/186233244-bcb1337d-9826-4a79-b800-8cee67bbdaea.png)

Gerçek para alabildiğimiz bir banka veya ATM ve sahte para üreten bir sahtekar olduğu varsayılsın. Buradan polisin eline iki farklı para tipi geçer. Fake ve gerçek olan. Polis, önceden gerçek paranın nasıl olduğunu bileceği için sahte olanı gerçeğinden ayırt edebilecektir ve buna göre bir çıktı verecektir. Bu feedback’e göre sahtekar, polisi kandırabilmek için daha gerçekçi fake paralar üretmeye başlayacaktır. Bu döngü, polisin sahte olanı gerçeğinden ayırt edemediği ana kadar devam eder ve süreç tamamlanır. 
GAN’ın genel yapısına bakıldığında da durum buna benzerdir. Yukarıdaki örnekteki sahtekarın yerini Generator, polisin yerini Discriminator ağı alır. Output, binary mode’dadır ve eğer sahteyse 0, gerçekse 1 sonucunu verir. Bu süreç sonunda verilen input çeşidi kadar istenilen büyüklükte dataset meydana gelir. 

![image](https://user-images.githubusercontent.com/76012121/186233302-0b4eddec-dbd0-4d79-9fc0-a2f599513a59.png)

Discriminator ağ, verdiği olasılık değerleri ile olması gereken değerler arasındaki fark olan loss değeri kullanılarak eğitilir. Örneğin Discriminator ağ gerçek bir resme 0.7 değerini vermişse 1–0.7 = 0.3 hata yapmıştır. Tam tersi olarak sahte bir resme 0.7 değeri vermişse de 0.7–0 = 0.7 hata yapmıştır. Discriminator ağın değerleri eğitim sırasında her iterasyonda bu hata değerlerini 0’a indirecek şekilde güncellenir. Generator ağ ise tam tersi olarak kendi ürettiği sahte resimlerin gerçeğe yakın olmasını yani 1 olarak değerlendirilmesini ister. Eğer kendi ürettiği resmi Discriminator ağ 0.6 olarak değerlendirmişse, Generator ağ 1–0.6=0.4 hata yapmıştır. Generator Ağ da her iterasyonda bu hatayı 0’a indirmeyi ister. Bu şekilde eğitim süreci ilerledikçe Discriminator ağ, gerçek ve sahte resimleri ayırt etme işinde daha başarılı olur. Generator ağ ise daha gerçekçi sahte resimler üretir. Eğitim süreci bittiğinde elimizde gerçeğinden ayırt edilemeyecek kalitede resimler üreten bir üretici sistem kalır. 

# Bu sistemin mümkün olan kullanım alanları nelerdir?

GAN yaklaşımı ile asla varolmamış insan yüzleri, hayvanlar, doğa fotoğrafları, haritalar, araç dizaynları, kıyafetler üretilebilir; siyah beyazdan renkli resme çevirme, çizimleri gerçekçi boyama, uydu fotoğrafından haritaya dönüştürme, bölümlendirilmiş planlardan bina veya sokak tasarımına dönüştürme gibi alanlarda çalışmalar yapılabilir. 
DeepFake metodu ile eski sanat eserlerinin canlandırması yapılabilir. 
Ancak en heyecan verici teknolojiler Nvidia bünyesinde gerçekleşmektedir. Öyle ki; GauGAN (Gaussian GAN) türüyle, kullanıcı çizimine göre manzara görüntüleri yaratma gibi bir teknolojileri bulunmaktadır. 
Bunun yanısıra, oyunlardaki gündüz sahnelerinden alınan numunelerle gece sahnelerini üretme üzerine de çalışmaları bulunmaktadır. 
