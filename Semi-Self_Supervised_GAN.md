## Bu yazıda, 2 GAN yaklaşımının özeti yapılmaktadır: 
  ### -	Semi-Supervised GAN (SGAN)
  ### -	Self-Supervised GAN (SSGAN)

## Semi-Supervised GAN (SGAN):

Semi-Supervised learning, tahmine dayalı bir modelin gerekli olduğu ve az sayıda etiketli örnek ve çok sayıda etiketlenmemiş örneğin bulunduğu bir sorunu ifade eder.

En yaygın örnek, çok büyük bir örnek veri kümesinin bulunabileceği, ancak yalnızca küçük bir bölümünün hedef etiketlerine sahip olduğu bir sınıflandırma öngörücü modelleme problemidir. Model, küçük etiketli örnekler kümesinden öğrenmeli ve gelecekte yeni örnekleri sınıflandırmaya genelleştirmek için bir şekilde daha büyük etiketlenmemiş örnek veri kümesinden yararlanmalıdır.

Yarı Denetimli GAN veya bazen kısaca SGAN, yarı denetimli öğrenme problemlerini ele almak için Üretken Çelişki Ağı mimarisinin bir uzantısıdır.

![image](https://user-images.githubusercontent.com/76012121/186237590-79b40192-b0a0-455f-8881-a2d65f3df34e.png)

Geleneksel bir GAN'daki discriminator, belirli bir görüntünün gerçek (veri kümesinden) veya sahte (oluşturulmuş) olup olmadığını tahmin etmek için eğitilir ve labellanmamış görüntülerden özellikleri öğrenmesine olanak tanır. Ayırıcı daha sonra, aynı veri kümesi için bir classifier geliştirirken bir başlangıç noktası olarak transfer learning yoluyla kullanılabilir ve bu da denetimli tahmin görevinin GAN'ın denetimsiz eğitiminden faydalanmasına olanak tanır. 

Semi-Supervised GAN’da, discriminator model K+1 class’larını tahmin etmek için güncellenir; burada K, tahmin problemindeki class sayısıdır ve yeni bir "sahte" sınıf için ek ‘class label’ eklenir. Hem unsupervised GAN görevi hem de supervised classification görevi için discriminator modelin eş zamanlı olarak doğrudan train edilmesini içerir. Bu nedenle discriminator iki modda eğitilir: 

  ### -	Unsupervised Training:
  Discriminator, örneğin gerçek mi yoksa sahte mi olduğunu tahmin etmek için geleneksel GAN ile aynı şekilde eğitilir.
  ### -	Supervised Training: 
  Discriminator, gerçek örneklerin class label’ını tahmin etmek için eğitilir. 

Unsupervised modda training, modelin büyük bir etiketlenmemiş veri kümesinden yararlı feature extraction yeteneklerini öğrenmesine olanak tanırken supervised modda training, modelin çıkarılan özellikleri kullanmasına ve class label’larını uygulamasına izin verir. 

## Self-Supervised GAN (SSGAN): 

Son zamanlarda, sabit bir öğrenme ortamı sunarak discriminator’u yıkıcı unutmayı azaltmak için generative adversarial networks’e (GAN'lar) dönüşüm tabanlı self-supervised learning uygulanmıştır. Bununla birlikte, mevcut self-supervised GAN'lardaki kendi kendini denetleyen ayrı görevler, kendi kendini denetleyen classifier’ların generator dağılımına karşı agnostik olması nedeniyle, generator modelleme ile tutarsız bir hedefe neden olur. Bu sorunu çözmek için, veri dönüşümünün kendi kendini denetlemesi yoluyla GAN etiketlerini (gerçek veya sahte) artırarak GAN görevini self-supervised görevle birleştiren yeni bir kendi kendini denetleyen GAN fikri ortaya çıkar. 

![image](https://user-images.githubusercontent.com/76012121/186237678-c4d6bdbf-021a-4e88-850f-f8791b25a70d.png)

Spesifik olarak, orijinal discriminator ve kendi self-supervised classifier, artırılmış etiketlerin her dönüşüm altında hem generator dağılımının hem de veri dağılımının farkında olmasını öngören ve ardından generator’u optimize etmek için aralarındaki farkı sağlayan etiketle artırılmış bir discriminator’da birleştirilir. Teorik olarak, optimal generator’un gerçek veri dağılımını kopyalamak için birleşebileceği kantılanmıştır. Ampirik olarak, önerilen yöntemin, kıyaslama veri kümeleri genelinde hem generative modelleme hem de representation learning’de önceki kendi kendini denetleyen ve veri artırma GAN'larından önemli ölçüde daha iyi performans gösterdiği görülmüştür. 

![image](https://user-images.githubusercontent.com/76012121/186237758-8483aa37-7657-4ec7-b8df-ab933c919292.png)
