# AWS-Certified-Solutions-Architect-Associate

1- A solutions architect is designing a solution where users will be directed to a backup static error page if the  primary website is unavailable. The primary website’s DNS records are hosted in Amazon Route 53 where  their domain is pointing to an Application Load Balancer (ALB).
Which configuration should the solutions architect use to meet the company’s needs while minimizing changes and infrastructure overhead?

A-Point a Route 53 alias record to an Amazon CloudFront distribution with the ALB as one of its origins.Then, create custom error pages for the distribution

B-Set up a Route 53 active-passive failover configuration. Direct traffic to a static error page hosted within an Amazon S3 bucket when Route 53 health checks determine that the ALB endpoint is unhealthy

C. Update the Route 53 record to use a latency-based routing policy. Add the backup static error page hosted within an Amazon S3 bucket to the record so the traffic is sent to the most responsive endpoints

D. Set up a Route 53 active-active configuration with the ALB and an Amazon EC2 instance hosting a static error page as endpoints. Route 53 will only send requests to the instance if the health checks fail for the ALB

Keyword: 1-primary website is unavailable
         2-active-passive
         3-health checks


Explanation/Reference:
Explanation:
Active-passive failover
Use an active-passive failover configuration when you want a primary resource or group of resources to be available the majority of the time and you want a secondary resource or group of resources to be on standby in case all the primary resources become unavailable. When responding to queries, Route 53 includes only the healthy primary resources. If all the primary resources are unhealthy, Route 53 begins to include only the healthy secondary resources in response to DNS queries.
To create an active-passive failover configuration with one primary record and one secondary record, you just create the records and specify Failover for the routing policy. When the primary resource is healthy, Route 53 responds to DNS queries using the primary record. When the primary resource is unhealthy, Route 53 responds to DNS queries using the secondary record.
How Amazon Route 53 averts cascading failures As a first defense against cascading failures, each request routing algorithm (such as weighted and failover) has a mode of last resort. In this special mode, when all records are considered unhealthy, the Route 53 algorithm reverts to considering all records healthy.
For example, if all instances of an application, on several hosts, are rejecting health check requests, Route 53 DNS servers will choose an answer anyway and return it rather than returning no DNS answer or returning an NXDOMAIN (non-existent domain) response. An application can respond to users but still fail health checks,
so this provides some protection against misconfiguration.

Similarly, if an application is overloaded, and one out of three endpoints fails its health checks, so that it's excluded from Route 53 DNS responses, Route 53 distributes responses between the two remaining endpoints. If the remaining endpoints are unable to handle the additional load and they fail, Route 53 reverts to distributing requests to all three endpoints.
Reference: https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-types.html https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-problems.htmlTest

Açıklama/Referans:
Açıklama:
Aktif-pasif yük devretme
Bir birincil kaynağın veya kaynak grubunun çoğu zaman kullanılabilir olmasını istediğinizde ve tüm birincil kaynakların kullanılamaması durumunda ikincil bir kaynağın veya kaynak grubunun beklemede olmasını istediğinizde etkin-pasif yük devretme yapılandırması kullanın. Sorgulara yanıt verirken, Route 53 yalnızca sağlıklı birincil kaynakları içerir. Tüm birincil kaynaklar sağlıklı değilse, Route 53, DNS sorgularına yanıt olarak yalnızca sağlıklı ikincil kaynakları dahil etmeye başlar.
Bir birincil kayıt ve bir ikincil kayıtla bir aktif-pasif yük devretme yapılandırması oluşturmak için, kayıtları oluşturmanız ve yönlendirme ilkesi için Yük Devretme'yi belirtmeniz yeterlidir. Birincil kaynak sağlıklı olduğunda, Route 53, birincil kaydı kullanarak DNS sorgularına yanıt verir. Birincil kaynak sağlıklı olmadığında, Route 53, ikincil kaydı kullanarak DNS sorgularına yanıt verir.
Amazon Route 53 basamaklı hataları nasıl önler Basamaklı hatalara karşı ilk savunma olarak, her istek yönlendirme algoritmasının (ağırlıklı ve yük devretme gibi) bir son çare modu vardır. Bu özel modda, tüm kayıtlar sağlıksız olarak kabul edildiğinde, Route 53 algoritması tüm kayıtları sağlıklı olarak kabul etmeye geri döner.
Örneğin, birkaç ana bilgisayardaki bir uygulamanın tüm örnekleri durum denetimi isteklerini reddediyorsa, Route 53 DNS sunucuları, DNS yanıtı döndürmemek veya bir NXDOMAIN (var olmayan etki alanı) yanıtı döndürmek yerine yine de bir yanıt seçecek ve bu yanıtı döndürecektir. Bir uygulama kullanıcılara yanıt verebilir, ancak yine de durum denetimlerinde başarısız olur, bu, yanlış yapılandırmaya karşı bir miktar koruma sağlar.

Benzer şekilde, bir uygulama aşırı yüklenirse ve üç uç noktadan biri sistem durumu denetimlerinde başarısız olursa, bu nedenle Route 53 DNS yanıtlarından hariç tutulursa, Route 53 yanıtları kalan iki uç nokta arasında dağıtır. Kalan uç noktalar ek yükü kaldıramaz ve başarısız olurlarsa, Route 53, istekleri üç uç noktaya da dağıtmaya geri döner.
Referans: https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-types.html https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-problems .htmlTest
