---
description: DeGate DEX'te Merkeziyetsiz Grid Stratejisi
---

# Merkeziyetsiz Grid Stratejisi

### **Grid Stratejisi Nedir?**

\
Grid Stratejisi veya grid trading, belirlenen bir aralıkta alım ve satımı otomatikleştiren bir al-sat mekanizmasıdır. Belirlenen bir fiyat aralığında bir dizi alım ve satım emri vermenizi sağlar; bir alım emri gerçekleştiğinde, anında daha yüksek bir grid seviyesinde bir satış emri verir ve bir satış emri gerçekleştiğinde daha düşük bir grid seviyesinde alım emri oluşturur. Grid stratejisi, fiyatların belli bir aralıkta dalgalandığı yatay piyasalarda en iyi performansı gösterir ve küçük fiyat hareketlerinden kâr elde edilmesini sağlar.

[DeGate DEX'te](https://app.degate.com/?utm_source=gridguidebook), herhangi bir ücret ödemeden, merkeziyetsiz ve kendi cüzdanınızın kontrolünde [grid stratejisi](https://app.degate.com/en/grid/USDC/ETH/?utm_source=gridguidebook) uygulayabilirsiniz.

{% embed url="https://www.youtube.com/watch?v=uvkBgcWa6zc" %}
Grid Stratejisinin Çalışma Şekli: Ucuza Al, Yükseğe Sat
{% endembed %}



### **Grid Stratejisinin Avantajları**

Grid Stratejisi, sürekli olarak piyasayı izleme zamanı ya da enerjisi olmayan yatırımcılar arasında popülerdir. Grid Stratejisinin bazı dikkate değer avantajları şunlardır:

Otomasyon: Önce üst ve alt fiyat limitleri tanımlanır, ardından grid alım satım emirleri yerleştirilir ve ilgili varlığın fiyat hareketine göre otomatik olarak gerçekleştirilir. Grid stratejisi 7/24 çalışır (temelde düşükten alıp yüksekten satar), yatırımcılar için pasif getiri sağlar.

Uyarlanabilirlik: Grid yoğunluğu çeşitli durumlara göre optimize edilebilir. Kısa vadede, gün içindeki fiyat değişikliklerinden mikro kar elde etmek için yüzlerce grid kurulabilir; uzun vadede daha geniş bir aralık seçmek, yatırımcının genel yatay trendden kâr elde etmesini sağlar.

Kârlılık: Grid trading, piyasanın net bir trend göstermediği yan piyasalarda en iyi performansı gösterir. Yatırımcı, varlığın fiyatının hangi yönde hareket edeceğini tahmin etmek zorunda değildir ve grid stratejisi başlatıldıktan sonra sonuçları izlemek dışında başka bir şey yapması gerekmez.

### **Grid Stratejisinin (Merkeziyetsiz) Tasarım Zorlukları**

Grid Stratejisi özelliği genellikle merkezi borsalarda (CEX) bulunur. Emirleri gerçekleştirme, kullanıcıların kendi varlıkları üzerinde sahiplik yetkisine sahip olmaması nedeniyle CEX'te daha kolaydır. Mevcut piyasada merkeziyetsiz grid trading protokolleri yoktur, bunun nedeni birkaç zorluktur:

**Cüzdan İmzası**

Tipik bir grid strateji kurulumu, kullanıcının girdisine bağlı olarak 2 - 200 grid seviyesinden oluşabilir. Her bir grid seviyesi, kullanıcının cüzdan imzasını gerektiren bir alım veya satım limit emrini temsil eder. Üstelik, imza yetkilendirmesi genellikle birkaç saniye sürer, bu da grid emirlerinin yürütülmesini etkileyebilir çünkü piyasalar milisaniyeler içinde hareket eder.

**Canlı Talep İmzası**

Canlı piyasalarda fiyatlar kısa bir süre içinde yukarı veya aşağı hareket edebilir. Bu, bir alım emrinden satış emrine veya tam tersine geçebilecek grid emirlerini etkiler. Bu ters emirler, kullanıcının bilgisayarının başında olmaması durumunda zor elde edilebilecek canlı imza yetkilendirmesi gerektirir.

**Grid Stratejisine Giriş**

Merkeziyetsiz bir grid stratejisi özelliği oluşturma hedefine ulaşmak için önce standart bir grid stratejisi kurulumundaki sabitleri belirleyip tanımlıyoruz.

**Sabitler:**

Seviye Miktarı: Kullanıcının girdisinden belirlenen, her bir grid seviyesi için tahsis edilen varlıklar.

Grid Ofseti: Her bir grid seviyesi arasındaki fark, fiyat aralığı ve grid seviyelerinin sayısına göre belirlenir.

Emir Ofseti: Ters emirlerin hesaplanması için oluşturulmuş, her emir arasındaki fark. Grid ofsetine eşdeğer.

**Alım Satım Gridleri:**

Temel olarak, standart grid stratejisi kurulumu çift yönlü bir ticaret botudur. Kullanıcı imzasıyla ilgili karmaşıklıkları basitleştirmek için grid stratejisi kurulumu iki grid kategorisine ayrılır:

Alım Grid - alım grid emirlerinin kurulması

Satım Grid - satım grid emirlerinin kurulması

**Grid İmzaları:**

Bir sonraki adım, her bir Alım Satım gridi için işlem imzalarını ayarlamaktır. Daha önce tanımlanan sabitler her bir grid işlem imzasına dahil edilir. Kritik olarak, işlem imzası, mevcut piyasa fiyatına en yakın grid olarak tanımlanan ilk grid emrine bağlanır ve ardından sonraki grid emirleri, ilk grid emrinden alınan imza yetkilendirmesiyle ayarlanır.



{% hint style="info" %}
Örneğin, ETH'nin mevcut piyasa fiyatı 2000$'dır:

Alım Grid için: İlk grid emri ("Alım 1"), 2000$'ın altındaki en yakın grid seviyesinde tanımlanır.

Satım Grid için: İlk grid emri ("Satım 1"), 2000$'ın üzerindeki en yakın grid seviyesinde tanımlanır.
{% endhint %}

Bu yöntem, grid stratejisi aktifken kullanıcının birden fazla işlemi imzalama zorunluluğunu ortadan kaldırır.

**ETH/USDC Örneği:**

1. Kullanıcı A, ETH/USDC için 1800$ - 2300$ aralığında manuel bir grid stratejisi kurar ve o sırada ETH'nin mevcut fiyatı 2050$'dir. 10 grid hattı eklemiş ve 0.5 ETH ve 950 USDC tahsis etmiştir.
2. Sonuç olarak, girdilere göre 5 Satım Grid'i ve 5 Alım Grid'i ayarlanır.
3. Satım Grid'i için, kullanıcı ilk satım grid seviyesinde (yani "Satım 1") "Satım Grid İşlem İmzası"nı onaylayıp imzalamalıdır, bu sayede grid stratejisi mekanizması sonraki satım grid emirlerini kurabilecektir.
4. Alım Grid'i için, kullanıcı ilk alım grid seviyesinde (yani "Alım 1") "Alım Grid İşlem İmzası"nı onaylayıp imzalamalıdır, bu sayede grid stratejisi mekanizması sonraki alım grid emirlerini kurabilecektir.
5. Kullanıcı sadece arkasına yaslanır, rahatlar ve grid stratejisinin çeşitli emirleri (temelde düşükten alıp yüksekten satarak) uygulamasını izler, bu süreçte pasif kazanç sağlar!

Bu yenilikçi teknik tasarım sayesinde, kullanıcılar artık grid stratejilerinin faydalarından yararlanırken aynı zamanda varlıklarının tam kontrolüne sahip olabilecekler.

<figure><img src="../.gitbook/assets/0.gif" alt=""><figcaption></figcaption></figure>

Merkeziyetsiz Grid Stratejisinin Yenilikçi Teknik Tasarımı

### **Grid Ticareti Stratejileri**

Grid Ticaretinde yaygın olarak kullanılan 3 strateji vardır ve bunlar büyük ölçüde piyasa trendlerine ve ilgili varlığın performansına bağlıdır.

#### **Normal Grid Stratejisi**

Bu strateji, temel varlığın konsolide olduğu veya yatay seyrettiği dalgalı piyasalarda en iyi şekilde uygulanır. Normal Grid Stratejisi ile yatırımcı, önceden tanımlanmış fiyat aralığında hem alım hem de satım emirleri ayarlayarak varlığın fiyat hareketlerinden pasif kar elde edebilir.

![Normal Grid Stratejisi çalışırken](<../.gitbook/assets/1 (2).gif>)



#### **Alım Grid Stratejisi**

Bu strateji, ilgili token fiyatının daha da düşebileceği düşüş trendindeki piyasalarda en iyi şekilde uygulanır. Alım Grid Stratejisi ile yatırımcı, piyasa fiyatının **altında** bir dizi alım emri ayarlayarak varlığı düşük fiyattan alabilir. Ayrıca, fiyat yükseldiğinde bu grid emirleri satış emirlerine dönüştürülerek, grid aralığında kar elde etmesi sağlanır.

Alım Grid Stratejisinin ana ilkesi şudur: İlgili token uzun vadeli bir yatırım için iyi bir potansiyele sahiptir, böylece fiyat grid aralığının dışına çıksa bile yatırımcı, token’a dolar maliyeti ortalamasıyla yatırım yaparak fayda sağlar.

![](<../.gitbook/assets/2 (2).gif>)

#### **Satım Grid Stratejisi**

Bu strateji, Alım Grid Stratejisi ile aynı mantıkta çalışır, ancak ters yönde uygulanır. Satım Grid Stratejisi, ilgili tokenın daha da değer kazanacağı yükselen piyasalarda en iyi şekilde uygulanır. Satım Grid Stratejisi ile yatırımcı, piyasa fiyatının **üzerinde** bir dizi satış emri ayarlayarak varlığı yüksek fiyattan satabilir. Fiyat düştüğünde bu satış emirleri alım emirlerine dönüştürülerek, grid aralığında kar elde etmesi sağlanır.

Satım Grid Stratejisinin en büyük avantajı şudur: Yatırımcı, token fiyatı yükseldikçe kademeli olarak kar alırken, fiyat geriledikçe varlığı yeniden alarak karını maksimize eder.

![](<../.gitbook/assets/3 (2).gif>)

### **Sonuç**

Grid trading, insan duygularından etkilenmeyen ve tamamen kodla belirlenen otomatik bir yatırım stratejisidir. Bu strateji, özellikle yatay piyasalarda en iyi şekilde uygulanır ve kullanıcılara pasif kazanç sağlar.

Ayrıca, [DeGate’in](https://app.degate.com/?utm_source=gridguidebook) merkeziyetsiz tasarımına grid stratejisi özelliğine entegre ederek, kullanıcılar artık fonlarının tam kontrolüne sahip olurken otomatik ticaretin avantajlarından faydalanabilirler. [DeGate’in](https://degate.com/?utm_source=gridguidebook) limit emirleri ve merkeziyetsiz grid ticareti gibi özellikleriyle, kullanıcılar piyasa koşulları ne olursa olsun rahatça uyuyabilirler.



### **Grid Stratejisi Rehberi**

\
Grid Stratejisi veya grid trading, tanımlanmış bir aralıkta alım ve satımı otomatikleştiren güçlü bir yatırım aracıdır. Grid stratejisi, fiyatlar düştüğünde otomatik olarak alım emirleri, yükseldiğinde ise satış emirleri vererek piyasa dalgalanmalarından yararlanmanızı ve kâr elde etmenizi sağlar.

### **DeGate'te Grid Stratejisi Nasıl Kurulur?**

ETH/USDC çiftini kullanarak aşağıdaki rehber örneği inceleyelim.

![](<../.gitbook/assets/0 (12).png>)

### **Grid Stratejisi Modunu Seçin**

Seçebileceğiniz iki Grid Stratejisi modu vardır:

* **Otomatik**: Sistem tarafından otomatik oluşturulan parametreleri kullanarak Grid Stratejisi kurun.
* **Manuel**: Kendi tercihlerinizle Grid Stratejisi parametrelerini özelleştirin.

Grid Stratejisine yeni başlayanlar için \[Otomatik] modu önerilir.

![](<../.gitbook/assets/1 (11).png>)

![](<../.gitbook/assets/2 (11).png>)

#### **Grid Stratejisi Kurulumu \[OTOMATİK]** <a href="#wmukbdj4s97p" id="wmukbdj4s97p"></a>

1. \[Otomatik] sekmesine tıklayın.
2. Grid Stratejisi için tahsis etmek istediğiniz miktarı girin \[ETH/USDC]. Sadece ETH veya USDC miktarını girin, sistem Grid Stratejisi için karşılık gelen miktarı hesaplayacaktır.

{% hint style="info" %}
DeGate bakiyenizde yeterli ETH ve USDC olduğundan emin olun.
{% endhint %}

![](<../.gitbook/assets/3 (11).png>)

3. Önerilen parametreler görüntülenecektir.
4. "Grid Stratejisi Oluştur" butonuna tıklayın, kurulumu tamamlayın ve kazanmaya başlayın.

![](<../.gitbook/assets/4 (11).png>)

![](<../.gitbook/assets/5 (9).png>)

#### **Grid Stratejisi Kurulumu \[MANUEL]** <a href="#k1xx8qsr19m9" id="k1xx8qsr19m9"></a>

1. \[Manuel] sekmesine tıklayın. Özelleştirilmiş Grid Stratejinizin parametrelerini değiştirebilirsiniz.
2. Fiyat Aralığı: Üst ve alt limit fiyatlar, Grid Stratejisinin çalışacağı fiyat aralığını tanımlar.
3. Başlangıç Tahsisi: Grid Stratejisi için ayıracağınız fon miktarı. Sadece ETH veya USDC miktarını girin, sistem karşılık gelen miktarı hesaplayacaktır.
4. Grid Sayısı: Fiyat aralığı içinde Grid Stratejisinin vereceği alım ve satım emirlerinin sayısıdır.
5. Her Bir Grid için Miktar (≥$50): Her bir grid emri için tahsis edilen ETH miktarıdır.
6. "Grid Stratejisi Oluştur" butonuna tıklayın, kurulumu tamamlayın ve kazanmaya başlayın.

Her bir grid emri için minimum emir boyutu $50'dır.

![](<../.gitbook/assets/6 (9).png>)

Optimal kârlılık için, Grid Stratejisi kurulurken mevcut piyasa fiyatının fiyat aralığı içinde olması önerilir.

