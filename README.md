PROJE HAKKINDA



Bu proje girilen bir metnin ingilizce  ya da almanca olduğunu belirleyip ekrana yazan C dilinde yazılmış bir algoritmadır.

Ana fonksiyon ile birlikte toplam 6 fonksiyondan oluşan bu projede her bir fonksiyon void tipinde yazılmıştır ve geriye değer döndürmemektedir. 
Yazılan kodda yapılacak ilk işlem ekrana bir metin girdikten sonra filter_str() fonksiyonu çağrılarak filtreleme işlemi gerçekleştirilir.
Bu fonksiyon metnin içindeki boşluk ve harf karakterlerinin dışındaki elemanların yerini boşluk karakteri ile değiştirir.
Bu işlemin ardından ana fonksiyon içerisinde üç fonksiyon çağırma adımı daha gerçekleşir. 
calculate_frequencies_bi() fonksiyonu çağrılarak matrix_bigram_strings dizisindeki elemanların frekansı,
calculate_ frequencies _ tri() fonksiyonu çağrılarak  da matrix_trigram_strings dizisindeki elemanların frekansı hesaplanır ve frequencies dizisine atanır. Bu iki fonksiyonda yapılan işlemler pointer kullanılarak yapıldığı için frequencies dizisi üzerinde ilerde yapılacak olan işlemler uygun hale gelmiştir. 
Diğer fonksiyon calculate_distances ise frequencies dizisini parametre olarak alır ve bu dizi  ingilizce ve almanca dilinin frekans değerlerini tutan 
frequency_eng ve frequency_germ dizileri arasında oklid uzaklığı hesaplamak üzere ana fonksiyon tarafından çağrılır.



Biraz daha detay verecek olursak calculate_frequencies_bi() fonksiyonu tarafından metindeki elemanları matrix_bigram_strings dizisinde arama işlemi gerçekleştirilir.
İki boyutlu olan bu dizi on elemanlıdır ve her elemanı durdurucu karakter ile birlikte üç elemana sahiptir. 
Bu fonksiyonda matrix_bigram_strings  dizisi ile girilen metindeki artarda gelen iki karakter sırayla karşılaştırılır. 
Eğer istenilen eşitlik elde edilirse  sayac adlı değişken ile sayım işlemi yapılır. Bu şekilde matrix_bigram_strings  dizisindeki her bir elemanın sayısı bulunmuş olur. 
Her bir elemanın metindeki toplam sayısı bulunduktan sonra yüzdesi hesaplanır (Ben burada yüzdeyi hesaplamak için her iç döngü sonunda elde edilen sayac degiskenini 100.0 ile çarpıp metnin toplam sayısına bölüm işlemini gerçekleştirdim). 
Bu elde edilen yüzde değerleri metindeki matrix_bigram_strings dizi elemanlarının frekans değerleridir. 
Bu değerler daha sonra frequencies dizisine atanır. 
Tüm bu matrix_bigram_strings dizi elemanlarının frekans hesaplama işlemleri yine iki boyutlu ve on elemanlı fakat her bir elemanı durdurucu karakter ile dört elemanlı olan matrix_trigram_strings dizisi için de geçerlidir.



Frekans değerlerini belirlenip frequencies dizisine atandıktan sonra ana fonksiyon tarafından calculate_distances  fonksiyonu çağrılır. 
Bu fonksiyon  parametre olarak frequencies dizisi ile eleman sayısını alır. 
Önceden de belirttiğimiz ingilizce ve almanca dili frekans değerleri ile frequencies dizisi elemanları arasında oklid uzaklığı hesaplanacaktır. 
İngilizce için düşünürsek frequency_eng ile  frequencies dizisinin aynı indisli elemanları arasındaki fark alınır. 
Sonra bu değerlerin karesi alındıktan sonra float olarak tanımladığımız a değişkenine toplayarak atama işlemi gerçekleşir.
Her bir indis için aynı işlem gerçekleştirilir ve en sonunda elde ettiğimiz a değerinin kökü alınır. 
Bu değer  ingilizce ile metin arasındaki uzaklıktır. 
İngilizce ile almanca arasında uzaklık karşılaştırması yapabilmek için bu değer uzaklık değerlerini tutacak olan iki elemanlı distances dizisinin 0.indisine atanır.   
Almanca için de aynı işlemler gerçekleştirilir. Burada ise uzaklık değerini b adlı değişken tutar.Sonra bu değer Distances dizisinin 1.indisine atanır.





Sona doğru gelindiğinde calculate_distances fonksiyonu tarafından detect_lang() fonksiyonu çağrılır.
Bu fonksiyon parametre olarak distances dizisini alarak iki elemanını karşılaştıracaktır. 
Metin ile ingilizce arasındaki uzaklık olan ilk elemanın ile almanca arasındaki uzaklık olan ikinci elemanın büyüklük küçüklük sıralaması yapılacak ve en az uzaklık değerine sahip değere göre ekrana “ingilizce” veya “almanca” yazılacaktır
.
