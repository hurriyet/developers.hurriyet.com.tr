## Hürriyet Geliştirici Ortamı

Hürriyet içeriklerine hızlıca ulaşmak ve web/mobil/masaüstü uygulamalarında kullanabilmek için Hürriyet API servisini kullanmaya şimdi başlayabilirsiniz!

### Başlarken

 1. Sisteme [kayıt ol](/developers/new).
 2. Profil sayfandan ya da [API Explorer](/api-explorer/hurriyet-developers-api/versions/1.0/) sayfasından yeni bir **API key** oluştur.
 3. API [dökümantasyonunu](/docs/versions/1.0), [Sık Sorulan Sorular](/docs/versions/1.0/sik-sorulan-sorular-sss)'ı ve [Kullanım Koşulları](/docs/versions/1.0/kullanim-kosullari)'nı oku.
 4. [API Explorer](/api-explorer/hurriyet-developers-api/versions/1.0/) yardımıyla hazır API'ları **hiç kod yazmadan** test et.

### OData Nedir?
OData _(Open Data Protocol)_ HTTP protokolü kullanan REST tabanlı veri kaynağı servislerin sorgulanması amacıyla kullanılan global bir protokoldür.

OData standartları sayesinde istek _(request)_ ve yanıt _(response)_ başlıkları, durum kodları _(status code)_, HTTP metotları _(GET, POST, vs...)_, sorgu spesifikasyonları _(query options)_ gibi temel standartlar üzerinde fazlaca vakit kaybetmeden, hızlı bir şekilde, sadece iş mantığı kurgulayarak RESTful API'lar oluşturabilirsiniz.

OData servislerini de tüketmek oldukça kolaydır. OData metadata'ları **istemci** tarafından kolayca okunabilir - yorumlanabilir seviyede oluşturulmaktadır. Dolayısıyla güçlü ve geliştirilebilir istemci uygulamalarına entegrasyonu da hızlı ve kolayca gerçekleştirilebilmektedir.

OData ile ilgili olarak resmi web sayfasından (http://www.odata.org/) bilgi edinebilir, uygulamalarınıza OData servislerini entegre etmek için ise http://www.odata.org/libraries/ adresinden gerekli kütüphaneleri indirebilirsiniz.

### Hürriyet API - OData Kullanımı

OData yapısının kendine özgü bir sorgu yapısı bulunmaktadır. Aşağıda en temel kullanılan bazı sorgu anahtar kelimeleri ve işlevsellikleri kısaca özetlenmiştir:

> **$select** -> Sorgudan dönen cevap setindeki kolonların/özelliklerin _(column/property)_ sınırlandırılması sağlanır. Örnek kullanım;
```
https://api.hurriyet.com.tr/v1/articles?$select=Title
```
> **$filter** -> Sorguya filtre eklenerek cevap setinin sınırlandırılması sağlanır. Örnek kullanım;
```
https://api.hurriyet.com.tr/v1/articles?$filter=Title eq 'Tatilde formda kalmak'
```

> **top** -> Sorgudan dönecek olan cevap setindeki kayıt sayısının sınırlandırılması sağlanır. Örnek kullanım;
```
https://api.hurriyet.com.tr/v1/articles?$top=3
```

> Ayrıca bu anahtar kelimeleri birlikte kullanarak sonuç setindeki filtre sayılarınızı arttırabilir ve istediğiniz sonuç setine ulaşmanızı kolaylaştırabilirsiniz. Örnek kullanım;
```
https://api.hurriyet.com.tr/v1/articles?$select=Title&$filter=ModifiedDate ge Datetime'2014-10-10T10:41:31Z'&$top=3
```

**Hürriyet API** servisi üzerinde OData protokolünü kullanarak;
  * Sistemdeki haberleri _(Articles)_,
  * Sistemdeki köşe yazılarını _(Columns)_,
  * Sistemdeki haber içi foto galerileri _(NewsPhotoGalleries)_,
  * Sistemdeki sayfaları ve sayfalara atanmış haberleri _(Pages)_,
  * Sistemdeki klasörleri _(Paths)_,
  * Sistemdeki yazarları _(Writers)_

sorgulayabilir ve uygulamalarınızda kullanabilirsiniz.

API üzerinden yapacağınız istekler, kötüye kullanımı engelleme amaçla sınırlandırılmıştır. Bu sınırlar aşağıdaki gibidir:
 * Saniyede 5 adet.
 * Saatte 500 adet.

API üzerinden gelen header bilgilerinde toplam ve kalan limitinizi görebilirsiniz. Header bilgileri aşağıdaki gibidir.
 * **X-RateLimit-Limit-hour:** Saatte toplam yapabileceğiniz istek sayısını belirtir.
 * **X-RateLimit-Limit-second:** Saniyede toplam yapabileceğiniz istek sayısını belirtir.
 * **X-RateLimit-Remaining-hour:** Bir saatlik dilim içerisinde kalan istek sayısını belirtir.
 * **X-RateLimit-Remaining-second:** Bir saniyelik dilim içerisinde kalan istek sayısını belirtir.

**1. Hürriyet API nedir?**

Hürriyet API _(application programming interface)_ web/mobil/masaüstü uygulamalarınızda Hürriyet verilerinin programatik olarak kullanılabilmesini sağlayan bir arayüzdür.

**2. Hürriyet API'yi kimler kullanabilir?**

Hürriyet API geliştiriciler için sunulmuştur ancak geliştirmeye meraklı tüm kullanıcılar yeterli teknik birikime sahip olduğu sürece arayüzü kullanabilir.

**3. Hürriyet API ile ne tür verilere ulaşabilirim?**

Hürriyet API ile haberlere, köşe yazılarına, yazarlara, foto galerilere ve sayfalara ulaşabilirsiniz. Planlarımız dahilinde sonuç kümemizi daha fazla geliştirmek var. Tüm yeni geliştirmeleri de sizlere duyurmaya çalışacağız.

**4. Hürriyet API'yi nasıl kullanabilirim?**

  Hürriyet API, RESTful tabanlı, kaynak-yönelimli bir mimari ile kurulmuştur. Bu sayede standart HTTP istekleri ile (şu anda sadece _(GET)_ metodu hizmet vermektedir) Hürriyet verilerine rahatlıkla ulaşabilirsiniz. REST mimarisi ve OData protokolü ile ilgili detayları [bu adresten](/docs/versions/1.0/odata-hakkinda) edinebilirsiniz. 

**5. Hürriyet'in tüm içeriklerine neden ulaşamıyorum?**

Hürriyet API geliştirilirken kullanım koşulları, içerik hakları gibi hukuki durumlar gözönünde bulundurulmaktadır. İlerleyen zamanlarda, sunduğumuz içerikleri detaylandırmayı/sayıca arttırmayı planlamaktayız. Eğer özel olarak ulaşmayı ve kullanmayı plandığınız veriler var ise bizimle irtibata geçebilirsiniz.

**6. Hürriyet API'yi kullanmak için neden özel bir anahtara _(API Key)_ ihtiyacım var?**

Bu anahtarlar sayesinde API kullanım detaylarını gözlemleyebiliyor, kullanıcılarımızın "Kullanım Koşulları"na uyduklarından emin olabiliyoruz. Bununla birlikte kulanıcı gizliliğine de özenle dikkat ediyor ve kayıt bilgilerinizi herhangi bir servis sağlayıcısı ile paylaşmadığımızı taahhüt ediyoruz.

**7. Hürriyet API'ye yapacağım isteklerin bir sınırı var mıdır?**

Evet, her bir kullanıcının anlık ve günlük olarak yapacağı istekler sınırlandırılmıştır. Sınır ve yetkileri [bu adresten](/docs/versions/1.0/istek-sinirlari) öğrenebilirsiniz. Eğer daha yüksek sınır ve yetkilere ihtiyaç duyuyorsanız <destek@hurriyet.com.tr> adresi üzerinden bizimle irtibata geçebilirsiniz.

**8. Hürriyet API hangi sonuç formatlarını desteklemektedir?**

İstekleriniz sonucu dönen sonuç seti JSON formatındadır. İlerleyen zamanlarda farklı formatları da desteklemeyi planlamaktayız. Önerilerinizi <destek@hurriyet.com.tr> adresi üzerinden bizimle paylaşabilirsiniz.

**9. Gelecek geliştirme planlarınız için harika fikirlerim var!**

Fikirlerinizi bizimle hemen paylaşın! <destek@hurriyet.com.tr> adresinde maillerinizi görmeyi bekliyoruz.
 
 
 
