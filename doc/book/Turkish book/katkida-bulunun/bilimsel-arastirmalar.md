---
description: Sui ile alakalı Bilimsel Araştırmalar
---

# Bilimsel Araştırmalar

Bu belge, Sui ile ilgili olan ve ekibin en az bir üyesi tarafından ortaklaşa yazılmış araştırma makalelerinin bir listesini içerir. Bu makalelerdeki fikirlerden bazıları şu anda Sui'ye entegre ediliyor, diğerleri yol haritamızda yer alıyor. Kalan fikirler yol haritamızda yer almamasına rağmen gelecekte entegre edilebilir. Aşağıda bulunan, önceki çalışmalardan esinlenen en son tasarımımızı içeren [Sui Akıllı Kontrat Platformu](https://github.com/MystenLabs/sui/blob/main/doc/paper/sui.pdf)'nun teknik incelemesi ile başlayın.

### FastPay: Yüksek Performanslı Byzantine Fault Tolerant (Bizans Hata Toleranslı) Uzlaşma <a href="#fastpay-high-performance-byzantine-fault-tolerant-settlement" id="fastpay-high-performance-byzantine-fault-tolerant-settlement"></a>

* **Link:** [https://arxiv.org/abs/2003.11506](https://arxiv.org/abs/2003.11506)
* **Yayın:** Finansal teknolojilerdeki gelişmeler üzerine ACM konferansı (Advances in Financial Technologies), 2020
* **Önem:** FastPay, Sui'nin kalbinde yer alan temel protokolü tanımlamaktadır.
* **Özet:** FastPay, bazıları Byzantine (Bizans) olan bir dizi dağıtılmış doğrulayıcının, önceden finanse edilen ödemeler için yüksek bütünlüklü ve kullanılabilir bir mutabakat sistemini sürdürmesine olanak tanır. Ödemeleri yerel bir değer biriminde (kripto para birimi) gerçekleştirmek için veya itibari para birimlerinde perakende ödemeleri desteklemek için bir finansal yan altyapı olarak kullanılabilir. Bu, Sui'nin kullandığı protokol değildir, ancak Sui'nin genişlettiği temel güvenlik mekanizmasını önermektedir. FastPay, temel ilkel olarak Byzantine Consistent Broadcast'e (Bizans Tutarlı Yayın) dayanır ve tam atomik taahhüt kanallarının (konsensüs) masraflarından vazgeçer. Ortaya çıkan sistem hem onay hem de ödeme kesinliği için düşük gecikme süresine sahiptir. Dikkat çekici bir şekilde, her doğrulayıcı, sınırsız yatay ölçeklenebilirliğe izin vermek için birçok makinede parçalanabilir.

### Narwhal ve Tusk: DAG Tabanlı Bir Mempool (Bellek Havuzu) ve Verimli BFT Konsensüsü <a href="#narwhal-and-tusk-a-dag-based-mempool-and-efficient-bft-consensus" id="narwhal-and-tusk-a-dag-based-mempool-and-efficient-bft-consensus"></a>

* **Link:** [https://arxiv.org/abs/2105.11827](https://arxiv.org/abs/2105.11827)
* **Yayın:** EuroSys, 2022
* **Önem:** Sui'de paylaşılan nesneleri desteklemek için muhtemelen kullanacağımız konsensüs sistemi.
* **Özet:** Yüksek performanslı Byzantine fault-tolerant çekirdek tabanlı konsensüsü mümkün kılmak için güvenilir işlem yayma görevini işlem sıralamasından ayırmayı öneriyoruz. İşlemlerin nedensel geçmişlerinin yüksek verimli güvenilir yayılımı ve depolanması konusunda uzmanlaşmış bir mempool protokolü olan Narwhal'ı tasarlıyor ve değerlendiriyoruz. Narwhal asenkron bir ağı tolere eder ve arızalara rağmen yüksek performansı korur. Narwhal, her doğrulayıcıda birden fazla işçi kullanarak kolayca ölçeklendirilecek şekilde tasarlanmıştır ve elde edebileceğimiz verimde öngörülebilir bir sınır olmadığını göstermekteyiz. Narwhal'ı kısmen eşzamanlı bir mutabakat protokolü (Narwhal-HotStuff) ile oluşturmak, hataların varlığında veya eşzamansızlık nedeniyle aralıklı canlılık kaybında bile önemli ölçüde daha iyi verim sağlar. Bununla birlikte, canlılık kaybı daha yüksek gecikmeye neden olabilir. Hatalar meydana geldiğinde genel olarak iyi bir performans elde etmek için Narwhal ile çalışmak üzere sıfır mesaj ek yükü asenkron konsensüs protokolü olan Tusk'ı tasarlıyoruz. Çeşitli konfigürasyonlar ve hatalar altında yüksek performansını gösteriyoruz. Sonuçların bir özeti olarak, bir WAN üzerinde, Narwhal-Hotstuff, Hotstuff için 1 saniyelik gecikme süresinde 1.800 tx/sn ile karşılaştırıldığında 2 saniyeden daha az gecikme süresinde 130.000'den fazla tx/sn'ye ulaşmaktadır. Ek işçiler, herhangi bir gecikme süresi artışı olmaksızın verimi doğrusal olarak 600.000 tx/sn'ye çıkarır. Tusk yaklaşık 3 saniyelik gecikme ile 160.000 tx/sn'ye ulaşır. Hatalar altında, her iki protokol de yüksek verimi korur, ancak Narwhal-HotStuff artan gecikmeden muzdariptir.

### Zef: Düşük Gecikmeli, Ölçeklenebilir, Özel Ödemeler <a href="#zef-low-latency-scalable-private-payments" id="zef-low-latency-scalable-private-payments"></a>

* **Link:** [https://arxiv.org/abs/2201.05671](https://arxiv.org/abs/2201.05671)
* **Yayın:** Henüz yayınlanmadı (gönderim aşamasında)
* **Önem:** FastPay tasarımını, Sui'nin gerçekte kullandığı nesneleri (hesaplar yerine) destekleyecek şekilde genişletir. Bu makalenin ek bir katkısı da FastPay işlemlerine güçlü gizlilik eklemektir (ancak Sui bunu yapmayı planlamamaktadır).
* **Özet:** İsteğe bağlı ölçekte anonim dijital paralarla ödemeleri destekleyen ilk Byzantine-Fault Tolerant protokol olan Zef'i tanıtıyoruz. Zef, FastPay'in iletişim ve güvenlik modelini takip etmektedir: her iki protokol de asenkron, düşük gecikmeli, doğrusal olarak ölçeklenebilir ve kısmen güvenilen parçalanmış doğrulayıcılar tarafından desteklenmektedir. Zef ayrıca, kullanıcı hesaplarına bağlı zincir dışı sertifikalar olarak temsil edilen opak paralar sunar. Bir ödeme işlemi onları tükettiğinde veya oluşturduğunda madeni paraların nominal değerlerini gizlemek için Zef rastgele taahhütler ve NIZK kanıtları kullanır. Oluşturulan madeni paralar, [Coconut'un ](https://arxiv.org/pdf/1802.07344.pdf)kör ve rastgele eşik anonim kimlik bilgileri kullanılarak bağlanamaz hale getirilir. Coin tekrarının önlenmesiyle ilişkili depolama maliyetlerini kontrol etmek için Zef hesapları, bir hesap devre dışı bırakıldığında verilerin güvenli bir şekilde kaldırılabileceği şekilde tasarlanmıştır. Protokolün teknik özellikleri ve ayrıntılı analizinin yanı sıra, Zef'in Rust'ta açık kaynaklı bir uygulamasını da kullanıma sunuyoruz. AWS üzerindeki kapsamlı kıyaslamalarımız, ders kitabının doğrusal ölçeklenebilirliğini doğrulamakta ve nominal kapasitede bir saniyenin altında bir onay süresi göstermektedir. Blok zincirine dayalı mevcut anonim ödeme sistemleriyle karşılaştırıldığında bu, verim üzerinde teorik bir sınır olmaksızın üç kat büyüklükte bir gecikme hızını temsil etmektedir.

### Bullshark: DAG BFT Protokollerinin Pratik Hali <a href="#bullshark-dag-bft-protocols-made-practical" id="bullshark-dag-bft-protocols-made-practical"></a>

* **Link:** [https://arxiv.org/abs/2201.05677](https://arxiv.org/abs/2201.05677)
* **Yayın:** Henüz yayınlanmadı (gönderim aşamasında)
* **Önem:** Narwhal üzerinde çalışan kısmen eşzamanlı bir konsensüs protokolü sağlar. Sui, Tusk yerine bunu kullanmak isteyebilir.
* **Özet:** Kısmi senkronizasyon için optimize edilmiş ilk yönlendirilmiş asiklik grafik (Directed Acyclic Graph) tabanlı Bizans Hata Toleranslı (Byzantine-Fault Tolerant) protokol olan Bullshark'ı sunuyoruz. Bullshark, selefinin (DAG-Rider) optimal amortize karmaşıklık, asenkron canlılık, sıfır ek yük ve kuantum sonrası güvenlik gibi istenen tüm özelliklerini miras alır; ancak Bullshark aynı zamanda senkron dönemlerden yararlanan pratik bir düşük gecikmeli hızlı yol sağlar. Buna ek olarak, Bullshark'ın bağımsız bir kısmen eşzamanlı versiyonunu tanıtıyor ve bunu en son teknolojiye karşı değerlendiriyoruz. Ortaya çıkan protokol, DAG tabanlı bir mempool uygulamasının üstünde utanç verici derecede basit 20 LOC) ve oldukça verimli, örneğin 50 düğümle saniyede 125 bin işlem ve 2 saniye gecikme süresi elde ediyor.

### Liderlerinizin Farkında Olun <a href="#be-aware-of-your-leaders" id="be-aware-of-your-leaders"></a>

* **Link:** [https://arxiv.org/abs/2110.00960](https://arxiv.org/abs/2110.00960)
* **Yayın:** Finansal Kriptografi ve Veri Güvenliği (Financial Cryptography), 2022
* **Önem:** Kısmen eşzamanlı konsensüs protokolü (Bullshark gibi) için performanslı bir lider seçim algoritması sağlar. Sui, paylaşılan nesneleri desteklemek için Bullshark ile birlikte kullanmak isteyebilir.
* **Özet:** Blok zincirlerindeki gelişmeler Durum-Makine-Çoğaltma (State-Machine-Replication) dünyasını etkilemiştir ve birçok son teknoloji blok zinciri-SMR çözümü iki temele dayanmaktadır: Zincirleme ve Lider rotasyonu. Bununla birlikte, Lider rotasyonu için kullanılan önceden belirlenmiş bir çizelgeleme algoritması (robin-round mechanism) istenmeyen bir davranışa sahiptir: çökmüş taraflar sonsuz sıklıkta atanmış liderler haline gelir ve genel sistem performansını yavaşlatır. Bu makalede, diğer arzu edilen özelliklerin yanı sıra, sadece çökmeli yürütmelerde liderleri hatalı olan turların sayısını sınırlayan bir Lider kullanım gereksinimini resmileştiren yeni bir Lider Farkında SMR çerçevesi sunuyoruz. Lider Farkında SMR'ye ulaşmak için yeni, itibar tabanlı bir Lider rotasyon çözümü olan Carousel'i tanıtıyoruz. Uyarlanabilir Lider rotasyonundaki zorluk, konsensüsün kendisinin bir lidere ihtiyaç duyması nedeniyle bir lider belirlemek için konsensüse güvenememesidir. Carousel, yerel olarak bir lider belirlemek için mevcut zincir içi bilgileri kullanır ve bu zorluğa rağmen Canlılık elde eder. Carousel ile donatılmış bir HotStuff uygulaması ciddi performans iyileştirmeleri göstermektedir: hatasız ortamlarda verimi 2 kattan fazla artırır ve hataların varlığında 20 kat verim artışı ve 5 kat gecikme azalması sağlar.

### Twin'ler: BFT Sistemlerinin Sağlam Hali <a href="#twins-bft-systems-made-robust" id="twins-bft-systems-made-robust"></a>

* **Link:** [https://arxiv.org/abs/2004.10617](https://arxiv.org/abs/2004.10617)
* **Yayın:** Uluslararası Dağıtık Sistemlerin İlkeleri Konferansı (OPODIS), 2021
* **Önem:** Diğer makalelere göre Sui ile daha az ilgili olan bu çalışma, Tusk ve Bullshark gibi konsensüs sistemlerinin uygulamalarını test etmek için bir yol sunmaktadır. Bununla birlikte, makale teoriktir ve yol haritamızda yer almamaktadır.
* **Özet:** Bu makale, Bizans saldırıları (Byzantine attacks) için otomatik bir birim test üreteci olan Twin'leri sunmaktadır. Twin'ler, üç tür Bizans davranışı uygular: (i) lider eşitliği, (ii) çifte oylama ve (iii) oylanan değerleri koruyan 'kilitleri' unutmak gibi dahili durumu kaybetmek. Bir Bizans node'unun (Byzantine node) ilginç saldırılarını taklit etmek için, her iki ikize de aynı kimlikleri ve ağ kimlik bilgilerini vererek, node'un bir yerine ikiz kopyalarını örneklendirir. Sistemin geri kalanı için ikizler, 'şüpheli' bir şekilde davranan tek bir node'dan ayırt edilemez görünür. İkizler sistematik olarak büyük ölçekte Bizans saldırı senaryoları üretebilir, bunları kontrollü bir şekilde yürütebilir ve davranışlarını inceleyebilir. Twin'ler senaryoları protokol turları üzerinde yinelenir ve düğümler arasındaki iletişim modellerini değiştirir. Twins, DiemBFT içinde günlük 44 milyon Twin'ler tarafından oluşturulan senaryoyu yürütebileceği bir üretim ortamında çalışır. Eldeki sistem hata göstermezken, Twin'lerin kendi uygulamasını doğrulamak amacıyla kasıtlı olarak enjekte edilen ince güvenlik hataları dakikalar içinde ortaya çıktı. Twins, geliştiricilerin kod tabanını güncellerken, yeni özellikler eklerken veya rutin bakım görevlerini yerine getirirken doğruluğu geriletmesini önleyebilir. Twins, DiemBFT üzerinde yalnızca ince bir sarmalayıcı gerektirir; bu nedenle diğer sistemlerin bunu kullanmasını öngörüyoruz. Bu fikirden yola çıkarak, bir yeni saldırı ve diğer BFT protokollerine karşı bilinen birkaç saldırı Twin'ler senaryoları olarak somutlaştırıldı. Her durumda, hedef protokoller bir düzineden daha az protokol turu içinde kırılır. Dolayısıyla, Twin'ler yaklaşımının sorunları ortaya çıkarması gerçekçidir.

### SybilQuorum: Güven Ağları Aracılığıyla Dağıtık Ledger'ları Açın <a href="#sybilquorum-open-distributed-ledgers-through-trust-networks" id="sybilquorum-open-distributed-ledgers-through-trust-networks"></a>

* **Link:** [https://arxiv.org/abs/1906.12237](https://arxiv.org/abs/1906.12237)
* **Yayın:** Yayınlanmadı
* **Önem:** Diğer makalelere göre Sui ile daha az ilgilidir ve makale henüz başlangıç aşamasındadır. Bildiri, proof-of-Stake sistemlerini (Sui gibi) güçlendirmek için bir algoritma sunmaktadır. Ancak makale teoriktir ve yol haritamızda yer almamaktadır.
* **Özet:** Sybil saldırısı tüm eşler arası sistemlerin başına bela olur ve modern açık dağıtık ledgerlar bunu önlemek için iş kanıtı veya alan, hisse veya bellek gibi diğer kaynaklardan izin ortamlarındaki geleneksel kabul kontrolüne kadar çeşitli taktikler kullanır. SybilQuorum ile açık dağıtık bir ledgerı Sybil saldırılarına karşı güvence altına almak ve sosyal ağ tabanlı Sybil savunmalarından yararlanarak dürüst katılımcılar arasında mutabakat sağlamak için alternatif bir yaklaşım öneriyoruz. Ledger aracılığıyla güven ilişkilerini ifade eden node'ların bir değer sistemini ve genel işlem sistemini nasıl önyükleyip işletebileceğini ve Sybil saldırılarının nasıl engellendiğini gösteriyoruz. Sistemimizi güvenli bir Federe Bizans Anlaşma Sistemi (Byzantine Agreement System) olarak ampirik olarak değerlendiriyor ve bunu yapmak için bu sistemlerin teorisini genişletiyoruz.

Son güncelleme 7/14/2022, 8:18:09 PM

* [Source Code](https://github.com/MystenLabs/sui/blob/devnet/doc/src/contribute/research-papers.md)