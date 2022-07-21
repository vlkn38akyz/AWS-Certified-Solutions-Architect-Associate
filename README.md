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



2- A solutions architect is designing a high performance computing (HPC) workload on Amazon EC2. The EC2 instances need to communicate to each other frequently and require network performance with low latency and high throughput.Which EC2 configuration meets these requirements?

A. Launch the EC2 instances in a cluster placement group in one Availability Zone

B. Launch the EC2 instances in a spread placement group in one Availability Zone

C. Launch the EC2 instances in an Auto Scaling group in two Regions and peer the VPCs

D. Launch the EC2 instances in an Auto Scaling group spanning multiple Availability Zones

Keywords: - each other frequently and require network performance with low latency and high throughput.
          - cluster placement

Explanation:
Placement groups
When you launch a new EC2 instance, the EC2 service attempts to place the instance in such a way that all of your instances are spread out across underlying hardware to minimize correlated failures.You can use placement groups to influence the placement of a group of interdependent instances to meet the needs of your workload. Depending on the type of workload.
Cluster – packs instances close together inside an Availability Zone. This strategy enables workloads to achieve the low-latency network performance necessary for tightly-coupled node-to-node communication that is typical of HPC applications.

Açıklama:
Yerleşim grupları
Yeni bir EC2 bulut sunucusu başlattığınızda, EC2 hizmeti, bulut sunucusunu, ilişkili arızaları en aza indirmek için tüm bulut sunucularınız temel donanıma yayılacak şekilde yerleştirmeye çalışır. Birbirine bağlı bir grubun yerleşimini etkilemek için yerleştirme gruplarını kullanabilirsiniz. iş yükünüzün ihtiyaçlarını karşılayacak örnekler. İş yükünün türüne bağlı olarak.
Küme – örnekleri bir Erişilebilirlik Alanı içinde birbirine yakın paketler. Bu strateji, iş yüklerinin, HPC uygulamalarında tipik olan, sıkı bir şekilde bağlanmış düğümden düğüme iletişim için gerekli olan düşük gecikmeli ağ performansını elde etmesini sağlar.

3-  An administrator would like to automate the creation of new AWS accounts for the research and development department of the organisation where new workloads need to be spun-up promptly and categorized into groups. How can this be achieved efficiently?


a-Use of AWS CloudFormation would be sufficient

b-Use of AWS Organisations

c-Using the AWS API to programmatically create each account via command line interface

d-AWS Identity Access Management (IAM)

AWS Organizations, büyümeyle birlikte ortamlarınızı merkezi olarak yönetmenize ve idare etmenize ve AWS kaynaklarınızı ölçeklendirmenize yardımcı olur. AWS Organizations’ı kullanarak programlama yoluyla yeni AWS hesapları oluşturabilir ve kaynak ayırabilir, iş akışlarınızı düzenlemek için hesapları gruplandırabilir, yönetim amacıyla hesaplara veya gruplara politikalar uygulayabilir ve tüm hesaplarınız için tek bir ödeme yöntemi kullanarak faturalamayı basitleştirebilirsiniz.

Ayrıca, AWS Organizations diğer AWS hizmetleriyle entegredir, bu nedenle merkezi yapılandırmaları, güvenlik mekanizmalarını, denetim gerekliliklerini ve kuruluşunuzda yer alan hesaplar arasındaki kaynak paylaşımını tanımlayabilirsiniz. AWS Organizations, herhangi bir ek ücret olmadan tüm AWS müşterileri tarafından kullanılabilir.

4-  An organisation utilizes a software suite that consists of a multitude of underlying microservices hosted on the cloud. The application is frequently giving runtime errors. Which service will help in the troubleshooting process?
a-AWS CloudTrail

b-AWS CloudWatch

c-AWS X-Ray

d-Amazon Elasticsearch Service

AWS X-Ray, yazılım geliştiricilerin üretimi ve dağıtılmış uygulamaları (ör. mikro hizmetler mimarisi kullanılarak oluşturulanlar) analiz edip bunların hatalarını ayıklamasına yardımcı olur. X-Ray ile, performans sorunlarının ve hataların kök nedenini belirlemek ve sorunlarını gidermek için uygulamanızın ve temel hizmetlerinin nasıl performans gösterdiğini anlayabilirsiniz. X-Ray, uygulamanızdan geçen isteklerin uçtan uca görünümünü sunar ve uygulamalarınızın temel bileşenlerinin bir haritasını gösterir. X-Ray’i kullanarak üç katmanlı basit uygulamalardan binlerce hizmet içeren karmaşık mikro hizmet uygulamalarına kadar birçok uygulamayı hem geliştirme hem de üretim aşamasında analiz edebilirsiniz.

5-An administrator would like to efficiently automate the replication and deployment of a specific software configuration existent on one EC2 instance onto four hundred others. Which AWS service is BEST suited for this implementation?
a-AWS OpsWorks

b-AWS Beanstalk

c-AWS Launch Configuration

d-AWS Auto-scaling

AWS OpsWorks, Chef ve Puppet'ın yönetilen bulut sunucularını sağlayan bir yapılandırma yönetimi hizmetidir. Chef ve Puppet, sunucularınızın yapılandırmalarını otomatikleştirmek için kod kullanmanızı sağlayan otomasyon platformlarıdır. OpsWorks, Chef ve Puppet'ı kullanarak sunucularınızın Amazon EC2 bulut sunucularınızda veya şirket içi bilişim ortamlarınızda yapılandırma, dağıtım ve yönetim biçimini otomatikleştirmenizi sağlar.

