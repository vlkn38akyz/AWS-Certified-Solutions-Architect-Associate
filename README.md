# AWS-Certified-Solutions-Architect-Associate

1. You are working as an AWS Architect for a start-up company. They have a two-tier production website. Database servers are spread across multiple Availability Zones and are stateful. You have configured Auto Scaling Group for these database servers with a minimum of 2 instances & maximum of 6 instances. During post-peak hours, you observe some data loss. Which feature needs to be configured additionally to avoid future data loss (and copy data before instance termination)?

a-Modify the cooldown period to complete custom actions before the Instance terminates.

b-Add lifecycle hooks to the Auto Scaling group.

c-Customize Termination policy to complete data copy before termination.

d-Suspend Terminate process that will avoid data loss.

Açıklama: Otomatik Ölçeklendirme grubuna lifecycle hooks eklemek, örneği sonlandırmadan önce bekleme durumuna getirir. Bu bekleme durumu sırasında, durum bilgisi olan bir örnekten kritik operasyonel verileri almak için özel etkinlikler gerçekleştirebilirsiniz. Varsayılan Bekleme süresi 1 saattir. Bekleme süresi sona ermeden önce örnekten veri kopyalamaya yardımcı olmayacağından A seçeneği yanlıştır. Ölçeklendirme sırasında hangi örneklerin önce sonlandırılacağını belirtmek için Sonlandırma ilkesi kullanıldığından C seçeneği yanlıştır, Otomatik Ölçeklendirme grubu için sonlandırma ilkesini yapılandırmak, örnek sonlandırmadan önce verileri kopyalamaz. Seçenek D yanlıştır, çünkü Sonlandırma politikasını Askıya Almak veri kaybını engellemez, ancak diğer süreçleri kesintiye uğratır ve ölçeğin artmasını engeller.

2-For which of the following scenarios should a Solutions Architect consider using ElasticBeanStalk? (Choose Two)

a- A web application using Amazon RDS

b- An Enterprise Data Warehouse

c- A long-running worker process

d -Capacity provisioning and load balancing of website

e- A management task run once on nightly basis

AWS Documentation clearly mentions that the Elastic Beanstalk component can be used to create Web Server environments and Worker environments. Option B is incorrect. ElasticBeanstalk is used to deploy and manage the applications on AWS. It's not used to store the data. Option C is incorrect. Beanstalk does not make sense to use for long-running processes. EC2 instances would be a better fit. Option D is correct. We can use Elastic Beanstalk to distribute incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions. It can handle the varying load of your application traffic in a single Availability Zone or across multiple Availability Zones.

3-An application with a 150 GB relational database runs on an EC2 Instance. While the application is used infrequently with small peaks in the morning and evening, which storage type would be the most cost-effective option for the above requirement?

a-Amazon EBS provisioned IOPS SSD

b-Amazon EBS Throughput Optimized HDD

c-Amazon EBS General Purpose SSD

d-Amazon EFS

Explanation: Since the database is used infrequently, not throughout the day, and the question requires the MOST cost-effective storage type, the preferred choice would be EBS General Purpose SSD over EBS provisioned IOPS SSD. The minimum volume of Throughput Optimized HDD is 500 GB. As per our scenario, we need 150 GB only. Hence, option C: Amazon EBS General Purpose SSD, would be the best choice for a cost-effective storage solution.

4-You are working for a start-up company that develops mobile gaming applications using AWS resources. For creating AWS resources, the project team is using CloudFormation Templates. The Project Team is concerned about the changes made in EC2 instance properties by the Operations Team, apart from parameters specified in CloudFormation Templates. To observe changes in AWS EC2 instance, you advise using CloudFormation Drift Detection. After Drift detection, when you check drift status for all AWS EC2 instance, drift for certain property values having default values for resource properties is not displayed. What would you do to include these resources properties to be captured in CloudFormation Drift Detection?

a-Run CloudFormation Drift Detection on individual stack resources instead of the entire CloudFormation stack.

b-Explicitly set the property value, which can be the same as the default value.

c-Manually check these resources as this is not supported in CloudFormation Drift Detection.

d-Assign Read permission to CloudFormation Drift Detection to determine drift.



AWS CloudFormation Drift Detection can be used to detect changes made to AWS resources outside the CloudFormation Templates. AWS CloudFormation Drift Detection only checks property values that are explicitly set by stack templates or by specifying template parameters. It does not determine drift for property values that are set by default. To determine drift for these resources, you can explicitly set property values which can be the same as that of the default value.Option A is incorrect. If property values are assigned explicitly to these properties, running AWS CloudFormation Drift Detection would be detected in both individuals as well as the entire CloudFormation Stack.Option C is incorrect as AWS EC2 instance is supported by CloudFormation Drift Detection.Option D is incorrect. Since for all other resources, CloudFormation Drift Detection has already determined drift, there is no other read permission to be granted further.

5- While reviewing the Auto Scaling events for your application, you notice that your application is scaling up and down multiple times in the same hour. What changes would you suggest in order to optimize costs while preserving elasticity? (SELECT TWO)

a-Modify the Auto Scaling group termination policy to terminate the older instance first.

b-Modify the Auto Scaling group termination policy to terminate the newest instance first.

C-Modify the Auto Scaling group cool down timers.

d-Modify the Auto Scaling group to use Scheduled Scaling actions.

E-Modify the CloudWatch alarm period that triggers your Auto Scaling scale down policy

Burada ölçeklendirme faaliyetinin devreye girmesi ve ölçeklendirme faaliyetinden sonra tüm altyapının dengelenmesi için yeterli zaman verilmemektedir. Bu, Auto Scaling grubu CoolDown zamanlayıcılarını artırarak sağlanabilir. Ayrıca, ölçeği düşürme politikasını tetiklemek için CloudWatch alarmı için doğru eşiği tanımlamanız gerekecektir.

6-. A website runs on EC2 Instances behind an Application Load Balancer. The instances run in an Auto Scaling Group across multiple Availability Zones and deliver several static files that are stored on a shared Amazon EFS file system. The company needs to avoid serving the files from EC2 Instances every time a user requests these digital assets. What should the company do to improve the user experience of the website?

a-Move the digital assets to Amazon Glacier.

B-Cache static content using CloudFront.

c-Resize the images so that they are smaller.

d-Use reserved EC2 Instances.

AWS Documentation, CloudFront kullanmanın avantajları hakkında aşağıdakilerden bahseder: Amazon CloudFront, .html, .css, .js gibi statik ve dinamik web içeriğinizin ve görüntü dosyalarınızın kullanıcılarınıza dağıtımını hızlandıran bir web hizmetidir. CloudFront, içeriğinizi uç konumlar adı verilen dünya çapındaki bir veri merkezleri ağı aracılığıyla sunar. Bir kullanıcı, CloudFront ile sunduğunuz içeriği istediğinde, içeriğin mümkün olan en iyi performansla teslim edilmesi için kullanıcı en düşük gecikme (zaman gecikmesi) sağlayan uç konuma yönlendirilir. İçerik zaten en düşük gecikmeye sahip uç konumdaysa, CloudFront bunu hemen teslim eder. Buzul, sık aramalar için kullanılmaz. Yani A Seçeneği iyi bir çözüm değil. C & D seçenekleri de bu durumda yardımcı olmayacaktır.

7- A consulting firm repeatedly builds large architectures for their customers using AWS resources from several AWS services including IAM, Amazon EC2, Amazon RDS, DynamoDB and Amazon VPC. The consultants have architecture diagrams for each of their architectures, and are frustrated that they cannot use them to automatically create their resources. Which service should provide immediate benefits to the organization?

a-AWS Beanstalk

b-AWS CloudFormation

c-AWS CodeBuild

d-AWS CodeDeploy

Bu, sorudaki gereksinimi tamamlar ve danışmanların CloudFormation şablonları oluşturmak için mimari diyagramlarını kullanmalarını sağlar. AWS Documentation, AWS CloudFormation'da aşağıdakilerden bahseder: AWS CloudFormation, Amazon Web Service kaynaklarınızı modellemenize ve ayarlamanıza yardımcı olan bir hizmettir, böylece bu kaynakları yönetmek için daha az ve AWS'de çalışan uygulamalarınıza odaklanmak için daha fazla zaman harcayabilirsiniz. İstediğiniz tüm AWS kaynaklarını (Amazon EC2 bulut sunucuları veya Amazon RDS DB bulut sunucuları gibi) açıklayan bir şablon oluşturursunuz ve AWS CloudFormation bu kaynakları sizin için tedarik edip yapılandırmakla ilgilenir.
8-The security policy of an organization requires an application to encrypt data before writing to the disk. Which solution should the organization use to meet this requirement?

A-AWS KMS API

b-AWS Certificate Manager

c-API Gateway with STS

d-IAM Access Key

B seçeneği yanlıştır. AWS Certificate Manager, geçiş halindeki trafiği şifrelemek için SSL sertifikaları oluşturmak için kullanılabilir, ancak beklemede değil. C seçeneği yanlıştır. Transit trafik için API ağ geçidini kullanırken belirteçleri vermek için kullanılır. D Seçeneği, EC2 Bulut Sunucularına güvenli erişim sağlamak için kullanılır. AWS Documentation, AWS KMS'de aşağıdakilerden bahseder: AWS Key Management Service (AWS KMS), verilerinizi şifrelemek için kullanılan şifreleme anahtarlarını oluşturmanızı ve kontrol etmenizi kolaylaştıran, yönetilen bir hizmettir. AWS KMS, Amazon Elastic Block Store (Amazon EBS), Amazon Simple Storage Service (Amazon S3), Amazon Redshift, Amazon Elastic Transcoder, Amazon WorkMail, Amazon Relational Database Service (Amazon RDS) dahil olmak üzere diğer AWS hizmetleriyle entegredir. Yönettiğiniz şifreleme anahtarları ile verilerinizi şifrelemek çok kolay.

9- You are an AWS Solutions Architect. Your company has a successful web application deployed in an AWS Auto Scaling group. The application attracts more and more global customers. However, the application’s performance is impacted. Your manager asks you how to improve the performance and availability of the application. Which of the following AWS services would you recommend?

a-AWS DataSync

b-Amazon DynamoDB Accelerator

c-AWS Lake Formation

d-AWS Global Accelerator

AWS Global hızlandırıcı, AWS uç ağında herhangi bir noktaya yayın yapan statik IP adresleri sağlar. Gelen trafik, AWS bölgelerindeki uç noktalar arasında dağıtılır. Uygulamanın performansı ve kullanılabilirliği iyileştirildi. Seçenek A ​yanlış: Çünkü DataSync, veri aktarımını otomatikleştiren bir araçtır ve performansı artırmaya yardımcı olmaz. Seçenek B ​ yanlış:​ Bu soruda DynamoDB'den bahsedilmiyor. Seçenek C yanlıştır: Çünkü AWS Lake Formation, AWS'de bu durumda yardımcı olmayacak büyük miktarda veriyi yönetmek için kullanılır. D Seçeneği DOĞRU:Global Accelerator hizmeti hem uygulama performansını hem de kullanılabilirliği iyileştirebilir.

10- A retailer exports data daily from its transactional databases into an S3 bucket in the Sydney region. The retailer's Data Warehousing team wants to import this data into an existing Amazon Redshift cluster in their VPC at Sydney. Corporate security policy mandates that data can only be transported within a VPC. Which steps would satisfy the security policy? (SELECT TWO)

A-Enable Amazon Redshift Enhanced VPC Routing.

b-Create a Cluster Security Group to allow the Amazon Redshift cluster to access Amazon S3.

c-Create a NAT gateway in a public subnet to allow the Amazon Redshift cluster to access Amazon S3.

D-Create and configure an Amazon S3 VPC endpoint.
2/2 points
Explanation: Amazon Redshift Enhanced VPC Routing provides VPC resources access to Redshift. Redshift will not be able to access the S3 VPC endpoints without enabling Enhanced VPC routing, so one option is not going to support the scenario if another is not selected. NAT instance (the proposed answer) cannot be reached by Redshift without enabling Enhanced VPC Routing.Option D: VPC Endpoints - It enables you to privately connect your VPC to the supported AWS Services and VPC Endpoint services powered by PrivateLink without requiring an IGW, NAT Device, VPN Connection or AWS Direct Connect connections. Instances in VPC do not require Public IP addresses to communicate with resources in the service, and traffic between your VPC and other service does not leave the Amazon network. S3 VPC Endpoint - it is a feature that will allow you to make even better use of VPC and S3. I recommend you to look into the following URLs to know the concept further.



11-A team is building an application that must persist and index JSON data in a highly available data store. The latency of data access must remain consistent despite very high application traffic. Which service would help the team to meet the above requirement?

Amazon EFS

Amazon Redshift

DynamoDB

AWS CloudFormation
1/1 point
Explanation: AWS Documentation mentions the following about DynamoDB: Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. The data in DynamoDB is stored in JSON format, and hence it is the perfect data storage to meet the requirement mentioned in the question.

12- An organization hosts a multi-language website on AWS, which is served using CloudFront. Language is specified in the HTTP request as shown below: 
quest as shown below: 
http://d11111f8.cloudfront.net/main.html?language=de
http://d11111f8.cloudfront.net/main.html?language=en
http://d11111f8.cloudfront.net/main.html?language=es 
How should AWS CloudFront be configured to deliver cached data in the correct language?

Forward cookies to the origin

Based on query string parameters

Cache objects at the origin

Serve dynamic content
1/1 point
Explanation: Since language is specified in the query string parameters, CloudFront should be configured for the same.

13-A Solutions Architect is designing a shared service for hosting containers from several customers on Amazon ECS. These containers will use several AWS services. A container from one customer should not be able to access data from another customer. Which solution would help the architect to meet these requirements?

A-IAM roles for ECS tasks

b-IAM roles for EC2 Instances

c-IAM Instance profile for EC2 Instances

d-Security Group rules

 The AWS Documentation mentions the following: With IAM roles for Amazon ECS tasks, you can specify an IAM role to be used by the containers in a task. Applications are required to sign their AWS API requests with AWS credentials, and this feature provides a strategy to manage credentials for your application's use. This is similar to how Amazon EC2 instance profiles provide credentials to EC2 instances.
 
14- A company is developing a web application to be hosted in AWS. This application needs a data store for session data. As an AWS Solution Architect, what would you recommend as an ideal option to store session data? (SELECT TWO)

a-CloudWatch

B-DynamoDB

c-Elastic Load Balancing

D-ElastiCache

Storage Gateway
1/2 points
Explanation: DynamoDB and ElastiCache are perfect options for storing session data. AWS Documentation mentions the following on Amazon DynamoDB: Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale. It is a fully managed cloud database and supports both document and key-value store models. Its flexible data model, reliable performance, and automatic scaling of throughput capacity make it a great fit for mobile, web, gaming, ad tech, IoT, and many other applications.AWS Documentation mentions the following on AWS ElastiCache: AWS ElastiCache is a web service that makes it easy to set up, manage, and scale a distributed in-memory data store or cache environment in the cloud. It provides a high-performance, scalable, and cost-effective caching solution while removing the complexity associated with deployment and management of a distributed cache environment.

15-A company needs to store images that are uploaded by users via a mobile application. There is also a need to ensure that security measures are in place to avoid data loss. What step should be taken for protection against unintended user actions?

a-Store data in an EBS volume and create snapshots once a week.

-B-Store data in an S3 bucket and enable versioning.

c-Store data on Amazon EFS storage.

d-Store data on EC2 instance storage.

Sürüm oluşturma, paket düzeyindedir ve bir nesnenin önceki sürümlerini kurtarmak için kullanılabilir. A seçeneği, dosyaların yanlışlıkla silinmesine karşı koruma sağlamadığından yanlıştır. C seçeneği yanlıştır. Bu ideal bir çözüm değildir çünkü birden çok EC2 bulut sunucusu dosya sistemine erişebilir. D seçeneği geçicidir.

16-. As an AWS solution architect, you are building a new image processing application with queuing service. There is fleet of m4.large EC2 instances which would poll SQS as images are uploaded by users. The image processing takes around 55 seconds for completion, and users are notified via emails on completion. During the trial period, you find duplicate messages being generated due to which users are getting multiple emails for the same image. What would be the best option to eliminate duplicate messages before going to production?

a-Create delay queue for 60 seconds.

B-Increase visibility timeout to 60 seconds.

c-Create delay queue to greater than 60 seconds.

d-Decrease visibility timeout below 60 seconds.

Varsayılan görünürlük zaman aşımı 30 saniyedir. Uygulamanın işlemi tamamlamak için 60 saniyeye ihtiyacı olduğundan, görünürlük zaman aşımı 60 saniyeye çıkarılmalıdır. Bu, mesajı 60 saniye boyunca diğer tüketicilerden gizler, böylece orijinal tüketici tarafından işlemde olan aynı dosyayı işlemezler. A ve C seçenekleri yanlıştır, çünkü Gecikme kuyrukları yeni mesajların bir kuyruğa teslimini ertelemenize izin verir. birkaç saniye için. 60 saniye veya daha uzun bir gecikme kuyruğu oluşturmak, yeni mesajın teslimini belirli saniyeler kadar geciktirir ve yinelenen mesajı ortadan kaldırmaz. Görünürlük zaman aşımı mesajın işlenmesi ve silinmesi için gereken maksimum süreye ayarlandığından D seçeneği yanlıştır. kuyruk. Görünürlük zaman aşımı 60 saniyenin altına ayarlanırsa, orijinal tüketici zaten üzerinde çalışırken mesaj diğer tüketicilere tekrar görünür olacak ve yeni mesajın teslimini belirli saniyeler kadar geciktirecek ve yinelenen mesajı ortadan kaldırmayacaktır.

17- A company has a media processing application deployed in a local data center. Its file storage is built on a Microsoft Windows file server. The application and file server need to be migrated to AWS. You want to quickly set up the file server in AWS and the application code should continue working to access the file systems. Which method should you choose to create the file server?

a-Create a Windows File Server from Amazon WorkSpaces.

b-Configure a high performance Windows File System in Amazon EFS.

C-Create a Windows File Server in Amazon FSx.

d-Configure a secure enterprise storage through Amazon WorkDocs.

 In this question, a Windows file server is required in AWS and the application should continue to work unchanged. Amazon FSx for Windows File Server is the correct answer as it is backed by a fully native Windows file system. Option​ ​A ​is​ ​incorrect:​ Because Amazon WorkSpace configures a desktop server which is not required in this question. Only a Windows file server is needed. Option​ ​B ​is​ ​incorrect:​ Because EFS can not be used to configure a Windows file server. Option​ ​C ​is​ CORRECT:​ Because Amazon FSx provides fully managed Microsoft Windows file servers.Option​ ​D ​is​ ​incorrect:​ Because Amazon WorkDocs is a file sharing service in AWS. It cannot provide a native Windows file system.
 
 18-There is a requirement to get the source IP addresses that access resources in a private subnet. Which of the following could be used to fulfill this purpose?

Trusted Advisor

B-VPC Flow Logs

Use CloudWatch metrics

Use CloudTrail

990 / 5.000
Çeviri sonuçları
AWS Belgeleri aşağıdakilerden bahseder: VPC Akış Günlükleri, VPC'nizdeki ağ arabirimlerine giden ve giden IP trafiği hakkında bilgi yakalamanızı sağlayan bir özelliktir. Akış günlüğü verileri, Amazon CloudWatch Günlükleri kullanılarak depolanır. Bir akış günlüğü oluşturduktan sonra, verilerini Amazon CloudWatch Logs'ta görüntüleyebilir ve alabilirsiniz. AWS Trusted Advisor, özelleştirilmiş bulut uzmanınız olduğundan A seçeneği yanlıştır! AWS ortamınızı paradan tasarruf etmek, sistem performansını ve güvenilirliğini artırmak ve güvenlik açıklarını kapatmak amacıyla inceleyerek AWS kullanımına yönelik en iyi uygulamaları gözlemlemenize yardımcı olur. AWS CloudTrail, AWS hesabınız için yönetişim, uyumluluk, operasyonel denetim ve risk denetimi sağlayan bir hizmettir. CloudTrail ile AWS altyapınızdaki eylemlerle ilgili hesap etkinliğini günlüğe kaydedebilir, sürekli olarak izleyebilir ve saklayabilirsiniz. CloudWatch Metric, esas olarak performans ölçümleri için kullanılır.
Soru başlığı

18-Your team is developing a high performance computing (HPC) application. The application resolves complex, compute-intensive problems and needs a high-performance and low-latency Lustre file system. You need to configure this file system in AWS at low cost. Which method is the most suitable?

a-Create a Lustre file system through Amazon FSx.

Launch a high performance Lustre file system in Amazon EBS.

Create a high-speed volume cluster in EC2 placement group.

Launch the Lustre file system from AWS Marketplace.

Lustre dosya sistemi, HPC uygulamaları için kullanılabilen açık kaynaklı, paralel bir dosya sistemidir. Tanıtımı için http://lustre.org/ adresine bakın. Amazon FSx'te kullanıcılar, düşük maliyetle bir Lustre dosya sistemini hızla başlatabilir. A Seçeneği DOĞRU: Amazon FSx, Lustre dosya sistemlerini destekler ve kullanıcılar yalnızca kullandıkları kaynaklar için ödeme yapar. B Seçeneği yanlıştır: Kullanıcılar Lustre dosya sistemini EBS aracılığıyla yapılandırabilse de, birçok ekstra yapılandırmaya ihtiyaç duyar, Seçenek A daha basittir. Seçenek C yanlıştır: Çünkü EC2 yerleştirme grubu bir Lustre dosya sistemini desteklemez. D Seçeneği yanlıştır: Çünkü AWS Marketplace'teki ürünler uygun maliyetli değildir. Amazon FSx için minimum ücret veya kurulum ücreti yoktur.

19-A company is using a Redshift cluster to store their data warehouse. There is a requirement from the Internal IT Security team to encrypt data in the Redshift database. How could this be achieved? (SELECT TWO)

Encrypt the EBS volumes of the underlying EC2 Instances.

B-Use AWS KMS Customer Default master key.

Use SSL/TLS for encrypting the data.

D-Use hardware security module (HSM) to manage the top-level encryption keys.

AWS belgeleri aşağıdakilerden bahseder: Amazon Redshift, veritabanını şifrelemek için bir şifreleme anahtarları hiyerarşisi kullanır. Bu hiyerarşideki en üst düzey şifreleme anahtarlarını yönetmek için AWS Key Management Service (AWS KMS) veya bir donanım güvenlik modülü (HSM) kullanabilirsiniz. Amazon Redshift'in şifreleme için kullandığı süreç, anahtarları nasıl yönettiğinize bağlı olarak farklılık gösterir. D Seçeneği doğrudur. AWS artık AWS KMS ile birlikte Amazon S3'ün sunucu tarafı şifreleme özelliklerini kullanarak Redshift verilerinin uçtan uca şifrelemesini destekliyor.

20-You are developing an application using AWS SDK to get objects from AWS S3. The objects have big sizes and sometimes there are failures when getting objects especially when the network connectivity is poor. You want to get a specific range of bytes in a single GET request and retrieve the whole object in parts. Which method can achieve this?

Enable multipart upload in the AWS SDK.

B-Use the “Range” HTTP header in a GET request to download the specified range bytes of an object.

Reduce the retry requests and enlarge the retry timeouts through AWS SDK when fetching S3 objects.

Retrieve the whole S3 object through a single GET operation.

HTTP GET isteğindeki “Range” başlığı aracılığıyla, tüm nesneler yerine nesnelerin belirli bir kısmı indirilebilir. Seçenek A ​yanlış: Çünkü soru çok parçalı yükleme yerine çok parçalı indirme istiyor. Seçenek B ​DOĞRU: Çünkü bayt aralığı getirmeleriyle, kullanıcılar aynı nesneden farklı parçalar getirmek için Amazon S3 ile eşzamanlı bağlantılar kurabilir. Seçenek C yanlıştır: Çünkü yeniden deneme isteklerini ve zaman aşımlarını ayarlamak bir nesnenin belirli bölümlerini indiremez. D Seçeneği yanlıştır: Çünkü tüm nesneyi alma yöntemi gereksinimi karşılamıyor.

21-An application hosted on EC2 Instances has its promotional campaign due, to start in 2 weeks. There is a mandate from the management to ensure that no performance problems are encountered due to traffic growth during this time. What should be done to the Auto Scaling Group to fulfill this requirement?

Configure Step scaling for the Auto Scaling Group.

B-Configure Dynamic Scaling and use Target tracking scaling Policy.

Configure Scheduled scaling for the Auto Scaling Group.

Configure Static scaling for the Auto Scaling Group.

Açıklama: Otomatik Ölçeklendirme grubundaki örnek sayısıyla orantılı olarak artan veya azalan bir kullanım metriği olan bir metriğe dayalı olarak ölçeklendirme yapıyorsanız, bunun yerine bir hedef izleme ölçeklendirme ilkesi kullanmanızı öneririz. Hedef izleme ölçeklendirme ilkelerinde, önceden tanımlanmış bir metrik seçer veya özelleştirilmiş bir metrik yapılandırır ve bir hedef değer belirlersiniz. EC2 Auto Scaling, ölçeklendirme politikasını tetikleyen CloudWatch alarmlarını oluşturur ve yönetir ve metrik ve hedef değere dayalı olarak ölçeklendirme ayarını hesaplar. Ölçeklendirme ilkesi, ölçümü belirtilen hedef değerde veya buna yakın tutmak için gereken kapasiteyi ekler veya kaldırır. Zamanlanmış ölçekleme, yük değişikliklerini tahmin edebildiğinizde ve ayrıca ne kadar süre çalıştırmanız gerektiğini bildiğinizde daha iyi çalışır. Buradaki senaryomuzda, kampanya döneminde (dönem belirtilmemiş) yoğun trafik olacağını biliyoruz, ancak gerçek trafikten emin değiliz. Bunu tahmin edecek bir geçmişimiz de yok.

22-A company has an application hosted in AWS. This application consists of EC2 Instances which sit behind an ELB. The following are the requirements from an administrative perspective: a) Ensure notifications are sent when the read requests go beyond 1000 requests per minute b) Ensure notifications are sent when the latency goes beyond 10 seconds c) Monitor all API request activities on the AWS resources Which of the followings can be used to satisfy these requirements? (SELECT TWO)

A-Use CloudTrail to monitor the API Activity.

Use CloudWatch logs to monitor the API Activity.

C-Use CloudWatch metrics for the metrics that need to be monitored as per the requirement and set up an alarm activity to send out notifications when the metric reaches the set threshold limit.

Use custom log software to monitor the latency and read requests to the ELB.

Açıklama: AWS CloudTrail, API çağrılarını izlemek için kullanılabilir. Bir ELB için CloudWatch ölçümlerini kullandığınızda, okuma isteklerinin sayısını ve gecikmeyi kutudan çıkarabilirsiniz. A seçeneği doğrudur. CloudTrail, AWS hesabınızdaki tüm kaynaklar için API çağrılarını kaydeden ve günlük dosyalarını bir Amazon S3 klasörüne teslim eden bir web hizmetidir. Kaydedilen bilgiler, kullanıcının kimliğini, AWS API çağrısının başlangıç zamanını, kaynak IP adresini, istek parametrelerini ve hizmet tarafından döndürülen yanıt öğelerini içerir. C seçeneği doğrudur. İhtiyaca göre izlenmesi gereken metrikler için Cloudwatch metriklerini kullanın ve metrik belirlenen eşik sınırına ulaştığında bildirim göndermek için bir alarm etkinliği ayarlayın.

23-A company has resources hosted in their AWS Account. There is a requirement to monitor API activity for all regions and the audit needs to be applied for future regions as well. What would fulfill this requirement?

a-Ensure CloudTrail for each region, then enable trail for each future region.

B-Ensure one CloudTrail trail is enabled for all regions.

c-Create a CloudTrail for each region. Use CloudFormation to enable the trail for all future regions.

d-Create a CloudTrail for each region. Use AWS Config to enable the trail for all future regions.

AWS Documentation aşağıdakilerden bahseder: Artık AWS hesabınız için tüm bölgelerde bir iz açabilirsiniz. CloudTrail, tüm bölgelerden günlük dosyalarını Amazon S3 klasörüne ve belirttiğiniz isteğe bağlı bir CloudWatch Logs günlük grubuna gönderir. Ayrıca, AWS yeni bir bölge başlattığında CloudTrail, yeni bölgede aynı izi oluşturacaktır. Sonuç olarak, herhangi bir işlem yapmadan yeni bölge için API etkinliği içeren günlük dosyaları alacaksınız.
