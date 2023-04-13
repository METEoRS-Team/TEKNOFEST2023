#Acikhack2023


## TEKNOFEST 2023 Türkçe Doğal Dil İşleme Yarışması 

### Aşağılayıcı Söylemlerin Doğal Dil İşleme İle Tespiti

### Yükleme & Kullanım

Gerçekleştirilen çalışmaların tamamı açık kaynak olarak sunulan Google Collaboratory ortamında Python programlama dili ile geliştirilmiştir. 

Uygulamanın test edilmesi için ilk olarak Google Collaboratory ortamında hesap oluşturulması gerekmektedir. Ayrıntılı bilgi için [Colab](https://colab.research.google.com/) linkinden yararlanabilirsiniz. Daha sonra requirements.txt dosyasında bulunan gereklilikleri yükleyin. Ardından Tahmin.ipynb notebookunda test verisetinizi yükleyin.

test_set = pd.read_csv(veriseti_ismi.csv', sep="|")

Daha sonra bulut ortamından tüm kodları sırasıyla çalıştırarak model tahminlerini elde edebilirsiniz.

### Özet

Aşağılayıcı söylemlerin doğal dil işleme ile tespiti projesinde bir metnin içerisinde aşağılayıcı söylem var mı (OFFENSIVE)  yok mu (NO_OFFENSIVE ), eğer varsa Cinsiyetçi söylemler (SEXIST), Irkçı söylemler (RACIST), Küfür (PROFANITY) ve Hakaret söylemleri (INSULT) aşağılayıcı söylemlerinden hangi kategori içerisinde bulunduğunu en yüksek doğrulukla tespit etmek amaçlanmaktadır. Bu proje için aşağıdaki adımlar gerçekleştirilmiştir:
1. Yapılan literatür çalışmalarında kullanılan yöntemler analiz edilerek çalışmada kullanılacak yöntemler için ön ayak olması sağlanmıştır.
2. Paylaşılan veri seti incelenerek gerekli olan ön işleme adımlarından geçirildikten sonra öznitelik çıkarma yöntemleri ile ön işlenmiş veri setinden özellik çıkarımı yapılmıştır. 
3. Özellik çıkarımı yapılmış veri seti ile metin verilerinde genellikle en yüksek başarı gösteren makine öğrenmesi ve derin öğrenme yöntemleri ile geliştirmeler gerçekleştirilmiştir.
4. Yapılan tüm çalışmalar sonucu edinilen bilgiler karşılaştırılıp analiz edilerek en yüksek performans ve başarı oranını sağlayan yöntem seçilmiştir.
5. Geliştirilen yöntem raporlanarak açık kaynak lisanslı bir şekilde belirlenen platformlar üzerinden paylaşılmıştır.

### Veri Seti

Problemin çözümünde kullanılan veri kümesi yarışma komitesi tarafından csv dosya formatında paylaşılmıştır. Yaklaşık 12000 adet etiketli olan metin verisinden oluşmaktadır. Veri kümesi içerisinde bulunan metinler target başlığı altında  SEXIST, RACIST, PROFANITY, INSULT olmak üzere 5 farklı etiketle etiketlenmiştir. is_offensive başlığı altında OFFENSİVE:1 veya NOT OFFENSİVE:0 olmak üzere 2 farklı etiketle etiketlenmiştir.  Metin verilerinin etiket dağılımı grafiklerde görülmektedir. 
[Target Alanı Dağılımı](https://drive.google.com/file/d/1nGzMsgrVBZzdwtOTH3DHazTIR70slaK2/view?usp=sharing)

[is_offensive Alanı Dağılımı](https://drive.google.com/file/d/1jJK4-sS-_cwSc8AI96EtuKKqmM8CXce2/view?usp=sharing)
### Veri Önişleme

Yapılan keşifsel incelemeler ve deneysel çalışmalar sonucunda veri seti üzerinde
1.Noktalama işaretlerinin kaldırılması, 
2.Durak kelimelerinin kaldırılması, 
3.Nümerik karakter/sayıların kaldırılması, 
4.Boşluk karakterinin kaldırılması, 
5.Bazı Türkçe olmayan harflerin türkçe karşılıklarına çevrilmesi, 
6.İki karakterden küçük kelimelerin kaldırılması, 
7.Kelimelerin küçük harfe çevrilmesi, 
8.Kelimelerin lemmalarının bulunması

önişleme adımları kullanılmıştır.

### Öznitelik Çıkarımı - Metin Verilerinin Vektörlere Dönüştürülmesi

Proje kapsamında yapılan model denemelerinde metin verilerini girdi olarak verebilmek için sayısal vektörlere dönüştürülmüştür. Makine öğrenmesi algoritmaları için
1. BoW
2. TF-IDF
Derin Öğrenme Algoritmaları için
1. Keras Tokenizer
2. Word2Vec
3. GloVe
4. AutoTokenizer 
yöntemleri kullanılmıştır.

### Modeller

Veri ön işleme adımları ve vektörlere dönüşüm adımları gerçekleştirildikten sonra problemin çözümü için farklı makine öğrenmesi ve derin öğrenme modelleri geliştirilmiştir. Makine öğrenme algoritması olarak literatürde metin sınıflandırması için daha yüksek doğruluk veren Logistic Regression, Multinomial Naive Bayes, Support Vektor Machines, Decision Trees, K-NN, Random Forest algoritmaları üzerinde çalışmalar gerçekleştirilmiştir. Derin öğrenme algoritmaları olarak LSTM, Bi-LSTM ve BERTurk algoritmaları üzerinde çalışmalar gerçekleştirilmiştir.

Target alanı çalışmaları
Makine Öğrenmesi
| Algoritmalar | YÖNTEM | Macro avg f1-score |
| ------------- | ------------- |  ------------- |
| Lojistic Regression | BoW Vektörleri ile Deneme | 0.85 |
| Lojistic Regression | TF-IDF Vektörleri ile Deneme | 0.83 |
| Multinomial Naive Bayes | BoW Vektörleri ile Deneme | 0.83 |
| Multinomial Naive Bayes | TF-IDF Vektörleri ile deneme | 0.83|
| Support Vektor Machines | BoW Vektörleri ile Deneme | 0.78| 
| Support Vektor Machines | TF-IDF Vektörleri ile deneme|0.70|
|Decision Trees | BoW Vektörleri ile Deneme | 0.77|
| Decision Trees|TF-IDF Vektörleri ile deneme|0.76|
|K-NN|BoW Vektörleri ile Deneme|0.64|
|K-NN|TF-IDF Vektörleri ile deneme|0.56|
|Random Forest|BoW Vektörleri ile Deneme|0.47|
|Random Forest|TF-IDF Vektörleri ile deneme|0.47|


Derin Öğrenme Algoritmaları

| YÖNTEM | Önişlemeler| Train accuracy | Train loss | Val loss|val accuracy|
| -------| ---------- |  ------------- |  --------- |  ------- | -------------
|LSTM|Tüm önişlemelerle eğitim|0,8245|0,5275|0,5275|0,8245|
|LSTM|Lemma bulma adımı hariç tüm önişlemelerle eğitim|0,7437|0,7848|0,7848||0,7437|
|LSTM|Word2Vec|0,2927|1,5835|1,5835|0,2927|
|LSTM|GloVe|0,2862|1,5877|1,5839|0,2927|
|Bi-LSTM|Tüm önişlemelerle eğitim|0,9095|0,2586|0,5803|0,8312|
|Bi-LSTM|Lemma bulma adımı hariç tüm önişlemelerle eğitim|0,874|0,3262|0,8854|0,7544|
|Bi-LSTM|Word2Vec|0,874|0,3367|1,3425|0,6347|
|Bi-LSTM|GloVe|8.839|0,277|2,0943|0,65|

|Model | Önişlemeler | Doğruluk | Loss|
| -------| ---------- |  ------------- |  --------- |
|BERTurk|Tüm önişlemelerle eğitim|0.87|0,15|
|BERTurk|Lemma bulma adımı hariç tüm önişlemelerle eğitim|0.93|0,02|
|BERTurk|Tahmin yapılacak modelin eğitilmesi|0.92|0,072148|

Is_offensive alanı çalışmaları
Makine Öğrenmesi
| Algoritmalar | YÖNTEM | Macro avg f1-score |
| ------------- | ------------- |  ------------- |
| Lojistic Regression | BoW Vektörleri ile Deneme | 0.8878 |
| Lojistic Regression | TF-IDF Vektörleri ile Deneme | 0.8802 |
| Lojistic Regression | BoW Vektörleri Dengelenmiş | 0.8866 |
| Lojistic Regression | TF-IDF Vektörleri Dengelenmiş | 0.8796 |
| Multinomial Naive Bayes | BoW Vektörleri ile Deneme | 0.8950 |
| Multinomial Naive Bayes | TF-IDF Vektörleri ile deneme | 0.8799|
| Multinomial Naive Bayes | BoW Vektörleri Dengelenmiş | 0.8765 |
| Multinomial Naive Bayes | TF-IDF Vektörleri Dengelenmiş | 0.8783|
| Support Vektor Machines | BoW Vektörleri ile Deneme | 0.8308| 
| Support Vektor Machines | TF-IDF Vektörleri ile deneme|0.8280|
| Support Vektor Machines | BoW Vektörleri Dengelenmiş | 0.8086| 
| Support Vektor Machines | TF-IDF Vektörleri Dengelenmiş |0.8216|
| Decision Trees | BoW Vektörleri ile Deneme | 0.8403|
| Decision Trees|TF-IDF Vektörleri ile deneme|0.8367|
|K-NN|BoW Vektörleri ile Deneme|0.7511|
|K-NN|TF-IDF Vektörleri ile deneme|0.7087|
|Random Forest|BoW Vektörleri ile Deneme|0.7076|
|Random Forest|TF-IDF Vektörleri ile deneme|0.7083|

Derin Öğrenme Algoritmaları

| YÖNTEM | Önişlemeler| Train accuracy | Train loss | Val loss|val accuracy|
| -------| ---------- |  ------------- |  --------- |  ------- | -------------
|LSTM|Tüm önişlemelerle eğitim|0.8955|0.2176|0.4208 |0.8399|
|LSTM|Lemma bulma adımı hariç tüm önişlemelerle eğitim|0.9378 |0.1406 |0.4074 ||0.8756|
|Bi-LSTM|Tüm önişlemelerle eğitim| 0.9526 |0.1293 |0.3966 |0.8780|
|Bi-LSTM|Lemma bulma adımı hariç tüm önişlemelerle eğitim|0.1825 |0.9157 |0.4065 |0.8487|


|Model | Önişlemeler | Doğruluk | Loss|
| -------| ---------- |  ------------- |  --------- |
|BERTurk|Tüm önişlemelerle eğitim|0.95|0,002|
|BERTurk|Lemma bulma adımı hariç tüm önişlemelerle eğitim|0.94|0.01|

### Sonuçlar
Yapılan çalışmalar ve incelemeler sonucunda geliştirilen modellerden BERTurk modeli ile en yüksek doğruluklu sonuçlar vermiştir. Target ve is_offensive alanları için farklı modeller geliştirilip ağırlıkları kaydedilerek ensemble öğrenme gerçekleştirilmiştir.

Aşağılayıcı söylemler için geliştirdiğimiz ağırlık [METEoRS/berturk_model_insult](https://huggingface.co/METEoRS/berturk_model_insult/tree/main)

Is offensive için geliştirdiğimiz ağırlık  [METEoRS/berturk_model_isoffensive](https://huggingface.co/METEoRS/berturk_model_isoffensive/tree/main)

