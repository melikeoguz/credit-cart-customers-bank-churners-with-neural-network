

NÖRON AĞLARINA GİRİŞ

KREDİ KARTI

MÜŞTERİ KAYBI

TAHMİNİ

• 170201058 - Berfin Kösemen

• 170201028 – Melike Oğuz

• 170201061 - İsmail Güler

• 160201132 – Alain Patrick Ndigande

• 170201008 – Fatma Değirmenci





Proje Amacı

Gerçekleştirilen projenin adı Kredi Kartı

Müşteri Kaybı Tahmini'dir. Yapay sinir

ağları kullanılarak, proje kapsamında

müşterilere ait özelliklerin, müşterilerin

bankadan ayrılıp ayrılmayacağını tahmin

etmesidir.

Proje İçeriği

\1. Veri Seti

\2. Veri Görselleştirme

\3. Veri Ön İşleme

\4. Yapay Sinir Ağları

\5. Modelin Hazırlanması ve Eğitimi





Gerekli kütüphaneler

uProjedeki verilerin görselleştirilebilmesi, random değerlerin oluşturulabilmesi,

datasetin okunabilmesi gibi olaylar için birtakım kütüphaneler gerekmektedir. Bu

kütüphaneler:

u • pandas

u • numpy

u • matplotlib

u • seaborn

u • random

u • math

u • sklearn.preprocessing'dir.





u **Pandas:** Veri işlemesi ve analizi için Python programlama dilinde yazılmış olan bir yazılım

kütüphanesidir. Bu kütüphane temel olarak zaman etiketli serileri ve sayısal tabloları işlemek için

bir veri yapısı oluşturur ve bu şekilde çeşitli işlemler bu veri yapısı üzerinde gerçekleştirilebilir

olur.

u **NumPy:** Python programlama dili için bir kütüphanedir. NumPy büyük, çok boyutlu diziler ve

matrisler için destek eklerken, bu dizilerde çalışmak için yüksek düzeyli matematiksel

fonksiyonların geniş bir koleksiyonudur.

u **Matplotlib:** Python programlama dili ve onun sayısal matematik uzantısı NumPy için bir çizim

kitaplığıdır. Tkinter, wxPython, Qt veya GTK gibi genel amaçlı GUI araç takımlarını kullanarak

çizimleri uygulamalara yerleştirmek için nesne tabanlı bir API sağlar.

u **Seaborn:** Matplotlib tabanlı bir Python veri görselleştirme kitaplığıdır. Çekici ve bilgilendirici

istatistiksel grafikler çizmek için üst düzey bir arayüz sağlamaktadır.

u **Sklearn.preprocessing:** Veri ön işleme kısmı için gerekli metotların yapılması için kullanılan

kütüphanedir. Projemizde, label encoding kısmı için kullanılmaktadır.

u Label Encoding, kategorik değişkenleri işlemek için popüler bir kodlama tekniğidir. Bu teknikte,

her bir veriye alfabetik sıralamaya göre benzersiz bir tam sayı atanır.





Veri Seti

u

u

**Marital\_Status** : Evlilik Durumu (Married, Single, Divorced,

Unknown)

**Income\_Category** : Gelir Kategorisi(40K, 40K - 60K, 60K - 80K,

80K-120K)

u Veri seti 23 özelliğe sahip ancak

korelasyonlarından görüleceği gibi hepsi

model performansına aynı etki

sağlamıyor.

u

u

u

**Card\_Category** : (Blue, Silver, Gold, Platinum)

**Months\_on\_book** : Banka ile ilişki dönemi

u Veri setinde 10127 müşteri bulunmakta,

her müşterinin yaş maaş, evlilik durumu,

kredi kartının limiti ,

**Total\_Relationship\_Count** : Müşteri tarafından tutulan toplam

ürün

u

u

u

u

u

u

**Months\_Inactive\_12\_mon** : Son 12 ayda etkin olmayan ay

**Months\_Inactive\_12\_mon** : Son 12 ayda etkin olmayan ay sayısı

**Contacts\_Count\_12\_mon** : Son 12 ayda Kişilerin

kredi kartinin kategorisi gibi, yaklaşık 23

özelikler var.

**Credit\_Limit** : Kredi Kartında Kredi Limiti

u

**CLIENTNUM :** Müşteri numarası (Unique değerdir)

**Total\_Revolving\_Bal** : Kredi Kartındaki Toplam Döner Bakiye

u

**Attrition\_Flag :** Dahili olay değişkeni (Hesap kapatılırsa 1

açık ise 0)

**Avg\_Open\_To\_Buy**: Satın Almak İçin Açık Kredi Limiti (Son 12

ayın ortalaması)

u

u

u

u

**Customer\_Age :** Müşteri yaşı

**Gender :** Cinsiyet (Female, Male)

**Dependent\_count :** Bağımlıların sayısı

u

**Total\_Amt\_Chng\_Q4\_Q1**: İşlem Tutarındaki Değişiklik (1.

Çeyreğe göre 4. Çeyrek)

u

u

u

**Total\_Trans\_Amt**: Toplam İşlem Tutarı (Son 12 ay)

**Total\_Trans\_Ct**: Toplam İşlem Sayısı (Son 12 ay)

**Education\_Level :** Müşterilerin eğitim seviyesi (high

school, college graduate, etc.)

**Total\_Ct\_Chng\_Q4\_Q1**: İşlem Sayısındaki Değişim (4. Çeyreğe

göre 4. Çeyrek)

u

**Marital\_Status :** Evlilik Durumu (Married, Single,

Divorced, Unknown)

u

**Avg\_Utilization\_Ratio** : Ortalama Kart Kullanım Oranı





Veri Görselleştirme

**Eğitim Durumu**





**Gelir Kategorisi**





**Evlilik Durumu**





**Kredi Kartı Türü**





**Attiration**





Veri Ön İşleme

u İşlemlere başlamadan önce gereksiz verilerin veri setinden kaldırılması için

öncelikle veri ön işleme aşamaları yapılmaktadır. Böylelikle elde edilen ham veri,

daha başarılı bir tahmin işleminin yapılmasını sağlamaktadır.

u Veri setini okumak için pandas kütüphanesi kullanılmaktadır. pd.read\_csv

komutu ile veri setinin var olduğu dosya yolu girilmelidir. Hangi verilerin

olduğunu görüntülemek için ise atanılan veri listesine veri.head() diyerek

baştan ilk 5 adet veri ekrana bastırılır.





...

u Bu işlemler tamamlandıktan sonra null değer dönen bir sütun var ise veri

setini bozmaması adına bu sütunların silinmesi gerekmektedir. Silinme işlemi

veri.drop([], axis = 1) yazılarak gerçekleştirilir.

u Veri setini ekrana bastırdığımızda,

Naive\_Bayes\_Classifier\_Attrition\_Flag\_Card\_Category\_Contacts\_Count\_12\_mo

n\_Dependent\_count\_Education\_Level\_Months\_Inactive\_12\_mon\_1' ve

u 'Naive\_Bayes\_Classifier\_Attrition\_Flag\_Card\_Category\_Contacts\_Count\_12\_mo

n\_Dependent\_count\_Education\_Level\_Months\_Inactive\_12\_mon\_2 adlı iki

değerin null değerler döndürdüğünü fark ettik. Bu yüzden bu sütunlar

kaldırılmıştır.





Sütunleri kaldırıldıktan sonra 2. önişlemenin aşamada Veri

Türlerinin Sorgulanır.





Veri Türleri

u

u

u

u

u

u

u

u

u

u

u

u

u

u

u

u

u

u

u

u

u

0 CLIENTNUM

int64

object

int64

1 Attrition\_Flag

2 Customer\_Age

3 Gender

object

Veri setinde bulunan özelliklerin veri tiplerini

sorgulamak için hazır info() metodu

kullanılmaktadır.

4 Dependent\_count

5 Education\_Level

6 Marital\_Status

7 Income\_Category

8 Card\_Category

9 Months\_on\_book

int64

object

object

object

object

int64

Sorgulama işleminin sonucuna göre veri

setimizde toplamda;

10 Total\_Relationship\_Count int64

11 Months\_Inactive\_12\_mon int64

12 Contacts\_Count\_12\_mon int64

dtypes: float64(5), int64(10),

object(6)

memory usage: 1.4+ MB

13 Credit\_Limit

float64

int64

14 Total\_Revolving\_Bal

15 Avg\_Open\_To\_Buy

float64

float64

int64

int64

float64

16 Total\_Amt\_Chng\_Q4\_Q1

17 Total\_Trans\_Amt

18 Total\_Trans\_Ct

19 Total\_Ct\_Chng\_Q4\_Q1

20 Avg\_Utilization\_Ratio float64





Veri Ön İşlemenin 2. Aşaması

u Veri türleri sorgulanmasının ardından hala sıfır değer dönen parametrelerin olup olmadığının sorgulanması

için isnull().sum() metodu kullanılır. Bu metot kullanılarak veri seti sorgulandığında null değer dönen bir

parametrenin olmadığı saptanmıştır.

u Bilindiği üzere makine öğrenme ve derin öğrenme gibi işlemlerin yapılacağı zaman string değerde olan veri

türlerine integer değer ataması yapılmalıdır. Çünkü makine bu verileri anlamlaştırmak ister ve string

değerler ile işlem yapamaz. Bu işleme **label encoding** işlemi denilmektedir. Label encoding işleminin

uygulanması için object türündeki veriler belirli işlemlerden geçilerek list haline çevrilir ve değer ataması

yapılır.

Projemizde örnek vermek gerekirse marial\_status sütununda 4 adet durum artık integer değerler ile ifade

edilmiştir.

u Married ->1

u Single -> 2

u Unknow ->3

u Divorced ->4





String Değerlerin Integer Değere

Dönüştürülmesi

u Encode işleminin ardından str\_column\_to\_int metodunda verinin indeksleme

işlemi yapılır. Bir dict() oluşturulduktan sonra aynı kelimeye(sözcüğe) aynı

indis verilecek şekilde fonksiyon tanımlanır.

u Bu aşamanın yapılma sebebi ise normalizasyon aşamasına geçilirken kolaylık

sağlanmasıdır.





Normalize İşlemi

u Encode işlemininden gelen sonuçları, dataset\_minmax fonksyona verilerek tüm

özelliklerin min ve max değerleri hesaplanır ve liste tutulur.

u Bu işlelden sonra normalize\_dataset fonksyon yardımıyle, veriyi 0 ile 1 arasında

sınılanıyor. Bu işlem aynı ölçülere getirip, karşılaştırıl hale gelir ve modelin

öğrenmesini doğru etkiliyor.

u Bu aşamadan sonra veriyi modele verilmeye hazır.





Verisetinin train/test Olarak Ayrılması

u Model doğruluğunun rastgele olup olmadığını doğrulamak için K-Fold cross

validation yöntemi kullanıldı.

u Veriyi n kadar foldlara bölünürken (n-1) kadar bölümleri train için ayrılır ve

kalan 1 bölüm test için kullanılmaktadır.

u Projede n parametresi için değer artınca zaman artışı ve performansı

düştüğünü fark ettik.

u N=5 olarak belirlettik. Yani her seferinde 4 fold train e 1 fold test için 5 kez

çalıştırlacak ve her seferinde accuracy metrikleri hesaplanacaktır.





u Yapay sinir ağları (YSA), insan beyninin öğrenme

yolunu taklit ederek beynin öğrenme,

hatırlama, genelleme yapma yolu ile topladığı

verilerden yeni veri üretebilme gibi temel

işlevlerin gerçekleştirildiği bilgisayar

yazılımlarıdır.

Yapay Sinir Ağları

ve Derin

Öğrenme





**BİYOLOJİK SİNİR SİSTEMİ ELEMANLARI VE**

**YAPAY SİNİR SİSTEMİNDEKİ KARŞILIKLARI**

Nöron

İşlemci Elemanı

Toplama Fonksiyonu

Transfer Fonksiyonu

Yapay Nöron Çıkışı

Ağırlıklar

Dentrit

Hücre Gövdesi

Aksonlar

Sinapslar





Yapay Sinir Ağı

uYapay sinir ağlarında genel mantık şöyledir. Şekil'de

görüldüğü gibi bir hücreye n tane veri girişi yapılmaktadır

(Xn veri girişi). Girilen veriler ağırlıklarla çarpılarak tüm

veriler toplanır ve sonra bias eklenir bunun sonucunda net

yargı elde edilir. Net girdi aktivasyon fonksiyonundan

geçirilir ve bir veri çıktısı elde edilmiş olur.

u

Yapay Sinir Ağları uygulamaları en çok tahmin,

sınıflandırma, veri ilişkilendirme, veri yorumlama ve

veri filtreleme işlemlerinde kullanılmaktadır .





**Yapay Sinir Ağ Modelleri**

u

Yapay sinir ağı modelleri tek katmanlı algılayıcılar, çok

katmanlı algılayıcılar, ileri beslemeli yapay sinir ağları ve

geri beslemeli yapay sinir ağları olarak dört gurupta

incelenebilir.

**İleri Beslemeli Yapay Sinir Ağları**

u

İleri beslemeli yapay sinir ağlarında nöronlar girişten

çıkışa doğru düzenli katmanlar şeklindedir. Bir katmandan

sadece kendinden sonraki katmanlara bağ bulunmaktadır.

Yapay sinir ağının girişine gelen bilgiler bir değişime

uğratılmadan orta noktaya diğer bir deyişle gizli

katmandaki hücrelere iletilir. Daha sonra sırasıyla çıkış

katmanından işlenerek geçer ve dış ortama aktarılır.

**Geri Beslemeli Yapay Sinir Ağları**

u Geri beslemeli yapay sinir ağlarında ileri beslemeli ağlardan

farklı olarak bir nöronun çıktısı sadece kendinden sonra gelen

nöron katmanına girdi olarak verilmez. Kendinden önceki

katmanda veya kendi katmanında bulunan herhangi bir nörona

girdi olarak bağlanabilir.Bu yapısı ile geri beslemeli yapay sinir

ağları doğrusal olmayan dinamik bir davranış göstermektedir.

Geri besleme özelliğini kazandıran bağlantıların bağlanış

şekline göre; aynı yapay sinir ağıyla farklı davranışta ve yapıda

geri beslemeli yapay sinir ağları elde edilebilir





u**Parametrelerin Hazırlanması**

u**Modelin Eğitimi**

MODELİN

u **İleri Besleme**

HAZIRLANMASI VE

EĞİTİMİ

u

u

u

**Aktivasyon Fonksiyonu**

**Geri yayılım**

**Ağırlıkların Güncellenmesi**

u**Modelin Doğruluğunun Hesaplanması**





u Yapay Sinir Ağı geliştirmede ilk basamak, parametrelerin

ayarlanıp modelin hazırlanmasıdır.

u Parametrelerin ayarlanma kısmında girdi ve çıktı

katmanlarında kaç adet nöron olması, gizli katman

sayısı, gizli katmanlardaki nöron sayısı, nöronlar arası

ağırlık değerleri gibi parametreler ayarlanır.

Parametrelerin

Hazırlanması

u Gizli katman sayısı :1

u Gizli katmandaki nöron sayısı : 5

u Epoch sayısı : 50 olarak ayarlanmıştır

u Giriş ve çıkış katmanlarındaki nöron sayıları verideki

özellik sayısına ve hedef değişkendeki sınıf sayısına

bağlıdır.





Model Eğitimi

u Derin öğrenme modellerinde iş yapılış aşamasına

bakıldığında öğrenme sürecinin ileri besleme ve geri

yayılım işlemlerinden oluştuğu görülür. Süreç başladığında

modele verilen girdiler ağ üzerinde ileri yönde ilerleyerek

nöronlarda birtakım işlemlerden geçer bu kısma ileri

besleme denir. Sürecin diğer basamağında ise ağ üzerinde

en sondan geriye doğru işlemler yapılır ve ağdaki hatalar

düzeltilir. Bu işlem zinciri geriye yayılım olarak adlandılır.





u Feed forward kısmında eğitim için hazırlamış veriler ağa

girdi olarak verilir. Girdiler nöronlarda çeşitli işlemlere

uğrayarak ağın en sonuna kadar ilerler.

u İlerleme esnasında veriler her bir nörondan bir diğerine

geçerken ağırlık değerleri ile çarpılır.

Feed Forward

u Bir nöronda çıktı alma işlemi aktivasyon fonksiyonu ile

yapılır. Nörona gelen işlenmiş veriler aktivasyon

fonksiyonuna girer ve fonksiyondan çıkan sonuç nöron

çıktısı olarak sonraki katman nöronlarına iletilir.





u Yapay sinir ağlarında nöron çıktısını hesaplamak için

aktivasyon fonksiyonu kullanılır

u Bu çalışmada sigmoid fonksiyonu kullanılmıştır.

u Sigmoid fonksiyonu 0-1 arasında çıktı üretir.

Sigmoid fonksiyonu :

Aktivasyon

Fonksiyonu

u

u Sigmoid grafiği :





u Geri Yayılım Algoritması, zincir kuralı

adı verilen yöntemle bir sinir ağını

etkili bir şekilde eğitmek için kullanıl

Basit bir ifadeyle, bir ağda ileri

beslemeden sonra, geri yayılım,

modelin parametrelerini ayarlayarak

geriye doğru geçiş gerçekleştirir.

Back

Propagation

u Bu aşamada ağırlıklardaki değişiklikle

geriye, yani [output](https://eksisozluk.com/?q=output+layer)[ ](https://eksisozluk.com/?q=output+layer)[layer](https://eksisozluk.com/?q=output+layer)'dan [hidden](https://eksisozluk.com/?q=hidden+layer)

[layer](https://eksisozluk.com/?q=hidden+layer)'lara, [hidden](https://eksisozluk.com/?q=hidden+layer)[ ](https://eksisozluk.com/?q=hidden+layer)[layer](https://eksisozluk.com/?q=hidden+layer)'lardan [input](https://eksisozluk.com/?q=input+layer)

[layer](https://eksisozluk.com/?q=input+layer)'lara doğru hesaplanır ve sonra

güncellenir.





Sigmoid Derivative

Türev yardımı ile

ağırlıların

güncellenmesine

yardımcı olur.





Ağırlıkların Güncellenmesi

Bu adımda uygulamanın

başında random değerler

atadığımız ağırlıkların

Ağdaki bağlantıların

ağırlıklarını, ağın gerçek çıktı

vektörü ile istenen çıktı

vektörü arasındaki farkın

değerini en aza indirecek

şekilde tekrar tekrar ayarlar.

güncellemesi geri yayılım

algoritması ile hesaplanan

delta değeri, learning rate ve

input değerinin yardımı ile

gerçekleştirilir.





u Modelin doğruluğunun hesaplanması için

accuracy yöntemi kullanılmaktadır. Bu yöntem

basit fakat etkili temel bir mantık üzerine

kuruludur. Accuracy yönteminde tahmin

sonuçlar ile gerçek sonuçlar karşılaştırılır.

Tahmin sonuçlarının ne kadarının doğru

olduğuna bakılır ve yüzdesi hesaplanır. Çıkan

sonuç modelin doğruluk değeri olarak sunulur.

**Modelin**

**Doğruluğunun**

**Hesaplanması**





Model Sonuçları

n\_folds = 5

l\_rate = 0.1

n\_epoch = 50

n\_hidden = 5

Parametrelerinde model sonuçları :

Modelin başarı oranı : 91.289%

Çalışma süresi : 1 dakika 48 saniye

n\_folds = 10

l\_rate = 0.1

n\_epoch = 50

n\_hidden = 5

Parametrelerinde model sonuçları : 91.334%

Çalışma süresi : 4 dakika





Model Sonuçları





Model Sonuçları





Model Sonuçları





Model Sonuçları





Model Sonuçları





Model Sonuçları

