# Spring Cloud Gateway
[GitHub]()
---

## Api Gateway
- Tüm mikroservislere gelen istekleri yöneten bir geçit.
- Api Gateway: Tüm istemci istekleri yönetecek ve ilgili mikroservislere yönlendirecek
---

### 1. **spring-cloud-starter-gateway**
- **Açıklama:**
    - `spring-cloud-starter-gateway`, Spring Cloud Gateway'in temel bağımlılığıdır ve bu bağımlılık, tamamen **Reactor Netty** üzerine inşa edilmiştir. Yani, reaktif programlama modelini kullanır.
    - **Teknoloji Stack:**
        - **Reactive Programming:** Bu starter, Spring WebFlux üzerine inşa edilmiştir, bu da uygulamanın reaktif, asenkron ve yüksek performanslı olmasını sağlar.
        - **Netty:** Netty, düşük seviyeli bir ağ uygulaması çatısıdır ve Spring Cloud Gateway, Netty kullanarak performanslı ve ölçeklenebilir gateway çözümleri sunar.
    - **Kullanım Senaryosu:**
        - Yüksek performanslı, ölçeklenebilir ve asenkron işlemlerin ön planda olduğu gateway çözümleri için tercih edilir.
        - Genellikle mikroservis mimarilerinde tercih edilir, çünkü reaktif programlama modeli, büyük ölçekli ve yüksek trafikli sistemlerde daha etkili olur.

### 2. **spring-cloud-starter-gateway-mvc**
- **Açıklama:**
    - `spring-cloud-starter-gateway-mvc`, Spring Cloud Gateway'in Spring MVC tabanlı bir sürümüdür. Bu bağımlılık, Spring MVC ve Tomcat gibi servlet tabanlı bir altyapı üzerinde çalışır.
    - **Teknoloji Stack:**
        - **Spring MVC:** Bu starter, klasik Spring MVC modeli üzerine inşa edilmiştir, yani senkron ve bloklama (blocking) modelini kullanır.
        - **Servlet-based (Tomcat):** Bu starter, varsayılan olarak Tomcat gibi servlet konteynerlerinde çalışır, bu da onun klasik bir web uygulaması gibi çalışmasına olanak tanır.
    - **Kullanım Senaryosu:**
        - Senkron işlem gerektiren, özellikle var olan Spring MVC uygulamalarıyla entegrasyonun önemli olduğu durumlarda tercih edilir.
        - Geleneksel web uygulamalarıyla daha uyumlu çalışır.

### 3. **Performans ve Ölçeklenebilirlik**
- **`spring-cloud-starter-gateway`:**
    - Reaktif model üzerine kurulu olduğundan, yüksek performans ve düşük gecikme süreleri sunar.
    - Özellikle I/O (girdi/çıktı) işlemleri yoğun olan, yüksek eş zamanlı kullanıcı sayısı olan uygulamalar için daha uygundur.
    - Non-blocking yapısı sayesinde daha iyi kaynak kullanımı sağlar.

- **`spring-cloud-starter-gateway-mvc`:**
    - Geleneksel Spring MVC modeli kullanır, bu nedenle her istek bir iş parçacığı (thread) tarafından işlenir, bu da daha yüksek iş parçacığı tüketimine neden olabilir.
    - Genellikle daha küçük ölçekli uygulamalar için yeterli olabilir, ancak yüksek trafikli uygulamalarda tıkanma (bottleneck) yaşanabilir.
    - Bloklama (blocking) modeline dayalı olduğu için reaktif modelin sunduğu performans avantajlarını sağlamaz.

### 4. **Geliştirme ve Entegrasyon Kolaylığı**
- **`spring-cloud-starter-gateway`:**
    - Reaktif programlamaya alışkın olmayan geliştiriciler için öğrenme eğrisi daha dik olabilir.
    - Ancak, mikroservis tabanlı modern uygulamalarda bu bağımlılık daha yaygın olarak kullanılır.

- **`spring-cloud-starter-gateway-mvc`:**
    - Geleneksel Spring MVC ve servlet tabanlı uygulamalara aşina olan geliştiriciler için daha tanıdık bir yapı sunar.
    - Var olan Spring MVC uygulamalarıyla entegrasyonu daha kolaydır.

### Özet
- **`spring-cloud-starter-gateway`**: Reaktif modelde çalışan, yüksek performanslı ve ölçeklenebilir gateway çözümleri için kullanılır. Genellikle büyük ölçekli, yüksek trafikli mikroservis mimarilerinde tercih edilir.
- **`spring-cloud-starter-gateway-mvc`**: Geleneksel Spring MVC yapısı üzerine inşa edilmiş, daha küçük ölçekli, senkron işlemler gerektiren veya mevcut Spring MVC uygulamalarıyla uyumlu çalışması gereken durumlarda kullanılır.

Seçiminiz, projenizin gereksinimlerine ve mevcut altyapınıza bağlı olacaktır. Eğer performans ve ölçeklenebilirlik önceliğinizse, `spring-cloud-starter-gateway` daha uygun bir seçenek olacaktır. Ancak, mevcut Spring MVC uygulamalarınız varsa ve reaktif modele geçmek istemiyorsanız, `spring-cloud-starter-gateway-mvc` iyi bir tercih olabilir.

