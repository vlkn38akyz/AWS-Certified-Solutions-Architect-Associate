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

19-Your team is developing a high performance computing (HPC) application. The application resolves complex, compute-intensive problems and needs a high-performance and low-latency Lustre file system. You need to configure this file system in AWS at low cost. Which method is the most suitable?

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

24- An application hosted in AWS allows users to upload videos to an S3 bucket. A user is required to be given access to upload some videos for a week based on the profile. How could this be accomplished in the best way possible?

a-Create an IAM bucket policy to provide access for one week.

b-Create a pre-signed URL for each profile which will last for one week.

c-Create an S3 bucket policy to provide access for one week.

d-Create an IAM role to provide access for one week.

Kullanıcılara S3 paketleri için geçici erişim vermek istediğinizde, önceden imzalanmış URL'ler mükemmel çözümdür. Bu nedenle, yeni bir profil oluşturulduğunda, URL'nin bir hafta sürmesini sağlamak ve kullanıcıların gerekli nesneleri yüklemesine izin vermek için önceden imzalanmış bir URL oluşturabilirsiniz. D Seçeneği için, IAM Rol Oturumu için ayarlayabileceğiniz maksimum süre 12 saattir, dolayısıyla bu 1 haftalık gereksinimi karşılamaz.

25-To improve the network performance, you launch a C5 EC2 Amazon Linux instance and enable enhanced networking by modifying the instance attribute with “aws ec2 modify-instance-attribute --instance-id instance_id --ena-support”. Which mechanism does the EC2 instance use to enhance the networking capabilities?

a-Intel 82599 Virtual Function (VF) interface.

b-Elastic Fabric Adapter (EFA).

c-Elastic Network Adapter (ENA).

d-Elastic Network Interface (ENI).

Açıklama: Gelişmiş ağ iletişimi iki mekanizmaya sahiptir: Elastik Ağ Bağdaştırıcısı (ENA) ve Intel 82599 Sanal İşlev (VF) arabirimi. ENA için kullanıcılar bunu --ena-support ile etkinleştirebilir. Seçenek A ​yanlıştır: Çünkü “--ena-support” seçeneği Intel 82599 Sanal İşlev (VF) arabirimi tarafından kullanılmaz. Seçenek B ​ yanlıştır: Çünkü Elastik Yapı Adaptörü (EFA) gelişmiş ağ iletişimi için kullanılmaz. C Seçeneği DOĞRU: Amazon Linux'ta kullanıcılar, soruda belirtilen AWS CLI komutuyla gelişmiş ağ özelliğini etkinleştirebilir. D Seçeneği yanlıştır: Bu senaryoda, gelişmiş ağ iletişimi için kullanılan mekanizma Elastik Ağ Arayüzü (ENI) yerine Esnek Ağ Bağdaştırıcısı (ENA) olmalıdır.

26-You are creating several EC2 instances for a new application. For a better performance of the application, both low network latency and high network throughput are required for the EC2 instances. All instances should be launched in a single availability zone. How would you configure this?

a-Launch all EC2 instances in a placement group using a Cluster placement strategy.

b-Auto assign a public IP when launching the EC2 instances.

c-Launch EC2 instances in an EC2 placement group and select the Spread placement strategy.

d-When launching the EC2 instances, select an instance type that supports enhanced networking.

Explanation: The Cluster placement strategy helps to achieve a low-latency and high throughput network. Option​ ​A ​is​ CORRECT:​ The Cluster placement strategy can improve the network performance among EC2 instances. The strategy can be selected when creating a placement group. Option​ ​B ​is​ ​incorrect:​ Because the public IP cannot improve the network performance. Option​ ​C ​is​ ​incorrect:​ The Spread placement strategy is recommended when a number of critical instances should be kept separate between each other. This strategy should not be used in this scenario. Option​ ​D ​is​ ​incorrect:​ The description in the option is inaccurate. The correct method is creating a placement group with a suitable placement strategy.

27-A company hosts 5 web servers in AWS. They want to ensure that Route53 can be used to route user traffic to random healthy web servers when they request for the underlying web application. Which routing policy should be used to fulfill this requirement?
a-Simple

b-Weighted

c-Multivalue Answer with health check

d-Latency

Explanation: If you want to route traffic randomly to multiple resources such as web servers, you can create one multivalue answer record for each resource and, optionally, associate an Amazon Route 53 health check with each record. Simple routing policy – Use a single resource that performs a given function for your domain, for example, a web server that serves content for the example.com website. Latency routing policy – Use when you have resources in multiple locations and you want to route traffic to the resource that provides the best latency. Weighted routing policy – Use to route traffic to multiple resources in proportions that you specify. Multivalue answer routing policy – Use when you want Route53 to respond to DNS queries with up to eight healthy records selected at random.

28-There is a requirement for an iSCSI device and the legacy application needs local storage with low-latency access to all the data. What would you do to meet the demands of the application?

Configure the Simple Storage Service.

Configure Storage Gateway Cached volume.

Configure Storage Gateway Stored volume.

Configure Amazon Glacier.

Explanation: If you need low-latency access to your entire dataset, first configure your on-premises gateway to store all your data locally. Then, asynchronously back up point-in-time snapshots of this data to Amazon S3. This configuration provides durable and inexpensive offsite backups that you can recover to your local data center or Amazon EC2. S3 and Glacier are not used for this purpose. Volume gateway provides an iSCSI target, which enables you to create volumes and mount them as iSCSI devices from your on-premises or EC2 application servers. The volume gateway runs in either a cached or stored mode. In the cached mode, your primary data is written to S3, while retaining your frequently accessed data locally in a cache for low-latency access. In the stored mode, your primary data is stored locally and your entire dataset is available for low-latency access while asynchronously backed up to AWS

29-Your company has an online game application deployed in an Auto Scaling group. The traffic of the application is predictable. Every Friday, the traffic starts to increase, remains high on weekends and then drops on Monday. You need to plan the scaling actions for the Auto Scaling group. Which method is the most suitable for the scaling policy?

Configure a scheduled CloudWatch event rule to launch/ terminate instances at the specified time every week.

Create a predefined target tracking scaling policy based on the average CPU metric and the ASG will scale automatically.

Select the ASG and on the Automatic Scaling tab, add a step scaling policy to automatically scale out/ in at fixed time every week.

Configure a scheduled action in the Auto Scaling group by specifying the recurrence, start/end time, capacities, etc.

A seçeneği yanlıştır:​ Bu seçenek işe yarayabilir. Ancak, ölçeklendirme eylemlerini gerçekleştirmek için Lambda işlevi gibi bir hedef yapılandırmanız gerekir. Seçenek B ​ yanlış:​ Hedef izleme ölçeklendirme ilkesi ASG için bir hedef tanımlar. Ölçeklendirme eylemleri bir zamanlamaya göre gerçekleşmez. Seçenek C ​yanlış: Adım ölçeklendirme ilkesi, ASG'yi belirtilen zamanda ölçeklenecek şekilde yapılandırmaz. D Seçeneği DOĞRU: Zamanlanmış ölçekleme ile, kullanıcılar ASG'nin ölçeklenmesi için bir zamanlama tanımlar. Bu seçenek gereksinimleri karşılayabilir.

Option​ ​A ​is​ ​incorrect:​ This option may work. However you have to configure a target such as a Lambda function to perform the scaling actions. Option​ ​B ​is​ ​incorrect:​ The target tracking scaling policy defines a target for the ASG. The scaling actions do not happen based on a schedule. Option​ ​C ​is​ ​incorrect:​ The step scaling policy does not configure the ASG to scale at specified time. Option​ ​D ​is​ CORRECT:​ With scheduled scaling, users define a schedule for the ASG to scale. This option can meet the requirements.

30-There is an application that consists of EC2 Instances behind classic ELBs. An EC2 proxy is used for content management of the backend instances. The application might not be able to scale properly. What should be used to scale the proxy and backend instances appropriately? (SELECT TWO)

Use Auto Scaling for the proxy servers.

Use Auto Scaling for the backend instances.

Replace the Classic ELB with Application ELB.

Use Application ELB for both the frontend and backend instances.

Explanation: When you see a requirement for scaling, consider the Auto Scaling service provided by AWS. This can be used to scale both the backend instances and the EC2 proxy server.

31-There is a website hosted in AWS that might get a lot of traffic over the next couple of weeks. If the application experiences a natural disaster at this time, what should be used to reduce potential disruption to users?

Use an ELB to divert traffic to an Infrastructure hosted in another region.

Use an ELB to divert traffic to an Infrastructure hosted in another AZ.

Use CloudFormation to create backup resources in another AZ.

Use Route53 to route requests to another instance in a different region.

Bir olağanüstü durum kurtarma senaryosunda, verilen tüm seçenekler arasından en iyi seçenek, trafiği statik bir web sitesine yönlendirmektir. Seçenek A yanlıştır çünkü ELB, trafiği birden çok bölgede değil, yalnızca bir bölgede dengeleyebilir. B ve C seçenekleri yanlıştır çünkü AZ'ler arasında yedekleme kullanmak olağanüstü durum kurtarma amaçları için yeterli değildir. "Sorun durumunda olası kesintiyi azaltmak için" ifadesi bir felaket kurtarma durumuna işaret ediyor. Bu durumu yönetmenin birden fazla yolu vardır. Ancak burada verilen listeden en iyi seçeneği seçmemiz gerekiyor. Bunlardan en uygunu D Seçeneğidir.

32. A database, hosted using the Amazon RDS service, is getting a lot of database queries and has now become a bottleneck for the associating application. Which action would ensure that the database is not a performance bottleneck?

Setup a CloudFront distribution in front of the database.

Setup an ELB in front of the database.

Setup ElastiCache in front of the database.

Setup SNS in front of the database.

ElastiCache, veritabanına karşı verilen ortak sorguları önbelleğe almak için bir veritabanının önünde kullanılabilen bir bellek içi çözümdür. Bu, veritabanındaki genel yükü azaltabilir. A seçeneği yanlıştır çünkü bu normalde içerik dağıtımı için kullanılır. Seçenek B kısmen doğrudur, ancak dahili yük dengeleme çözümü olarak bir veritabanınız daha olması gerekir. SNS basit bir bildirim hizmeti olduğu için D seçeneği yanlıştır.

33- A company has an infrastructure that consists of machines which send log information every 5 minutes. The number of these machines can run into thousands and it is required to ensure that the analysis of every log item is completed within 24 hours. What could be helpful in fulfilling this requirement?

Use Kinesis Data Streams with S3 to take the logs and store them in S3 for processing.

Launch an Elastic Beanstalk application to take the processing job of the logs.

Launch an EC2 instance with enough EBS volumes to consume the logs which can be used for further processing.

Use CloudTrail to store all the logs which can be analyzed at a later stage.

Explanation: AWS Documentation mentions the following: Amazon Kinesis Data Streams (KDS) is a massively scalable and durable real-time data streaming service. KDS can continuously capture gigabytes of data per second from thousands of sources such as website clickstreams, database event streams, financial transactions, social media feeds, IT logs, and location-tracking events. Make your streaming data available to multiple real-time analytics applications, to Amazon S3 or to AWS Lambda within 70 milliseconds of the data being collected.

34-A company is planning to build a 2-tier architecture with a web server and a database server with separate environments for development and testing. The architecture will be hosted on EC2 Instances accordingly, and database server would require less than 16,000 IOPS per volume. Which of the following EBS volumes are optimum for the underlying EC2 Instances? (Select Two)

General Purpose SSD for the web server

Provisioned IOPS for the web server

General Purpose SSD for the database server

Provisioned IOPS for the database server

Explanation : The General Purpose SSD would be suitable for development and test environments and the IOPS SSD for business critical applications

35-A company is hosting a MySQL database in AWS using the AWS RDS service. To offload the reads, a Read Replica has been created and reports are run off the Read Replica database. But at certain times, the reports show stale data. What could be the possible reason behind this?

The Read Replica has not been created properly.

The backup of the original database has not been set properly.

C-This is due to the replication lag. 

The Multi-AZ feature is not enabled.


An AWS Whitepaper on the caveat for reading Replicas is given below which must be taken into consideration by architects: Read Replicas are separate database instances that are replicated asynchronously. As a result, they are subject to replication lag and might be missing some of the latest transactions. Application architects need to consider which queries have the tolerance to slightly stale data. Those queries can be executed on a Read Replica, while the rest should run on the primary node. Read Replicas may also not accept any write queries

36-You have enabled CloudTrail logs for your company’s AWS account. In addition, the IT Security department has mentioned that the logs need to be encrypted. How could this be achieved?

Enable SSL certificates for the CloudTrail logs.

B-There is no need to do anything since the logs will already be encrypted.

Enable Server-Side Encryption for the trail.

Enable Server-Side Encryption for the destination S3 bucket.

Açıklama : Varsayılan olarak, CloudTrail olay günlüğü dosyaları Amazon S3 sunucu tarafı şifrelemesi (SSE) kullanılarak şifrelenir. Ayrıca günlük dosyalarınızı bir AWS Key Management Service (AWS KMS) anahtarıyla şifrelemeyi de seçebilirsiniz. Günlük dosyalarınızı istediğiniz kadar kovanızda saklayabilirsiniz. Günlük dosyalarını otomatik olarak arşivlemek veya silmek için Amazon S3 yaşam döngüsü kurallarını da tanımlayabilirsiniz. Günlük dosyası teslimi ve doğrulama hakkında bildirimler istiyorsanız Amazon SNS bildirimlerini ayarlayabilirsiniz.

37- A company has set up its data layer in the Simple Storage Service. There are a number of requests which include read/write and updates to objects in an S3 bucket. Users sometimes complain that updates to an object are not being reflected. What could be the most likely reason for this?

Versioning is not enabled for the bucket, so the newer version does not reflect the right data.

B-Updates made to the objects usually take sometime to reflect.

Encryption is enabled for the bucket, hence it is taking time for the update to occur.

The metadata for the S3 bucket is incorrectly configured.

Explanation : Updates made to the objects in S3 follow an eventual consistency model. Hence, for object updates, there can be a slight delay when an updated object is provided back to the user on the next read request.
Açıklama : S3'teki nesnelere yapılan güncellemeler, nihai bir tutarlılık modelini takip eder. Bu nedenle, nesne güncellemeleri için, bir sonraki okuma isteğinde kullanıcıya güncellenmiş bir nesne sağlandığında hafif bir gecikme olabilir.

38-Your company has enabled CORS on your S3 bucket to allow cross-origin resource sharing. In the CORS configuration, you need to specify the values for the "AllowedMethod" element. What would be your suggestion to the developer?

Those two methods require special permission from AWS

The developer’s user profile was limited to and required to be updated 

C-Only these methods are supported: GET, PUT, POST, DELETE, and HEAD 

OPTIONS and CONNECT are controlled by other bucket policies

39-Your company stores a big amount of archive data in expensive on-premises storage systems.You need to move the data to low cost storage such as Amazon S3 Glacier. Which of the following tools is the most suitable to simplify and automate the data transfer from on premises to S3 Glacier?

AWS DataSync

Server Migration Service

Database Migration Service 

Direct Connect
1/1 point
Explanation : AWS DataSync should be selected as it can simplify moving data between on-premises storage and AWS services such as S3 Glacier. Option​ ​A ​is​ CORRECT:​ With AWS DataSync, users can create a task to specify the data source and destination and then configure the data transfer. Option​ ​B ​is​ ​incorrect:​ Because Server Migration Service is used to migrate on-premise servers such as VMware. Option​ ​C ​is​ ​incorrect:​ Database Migration Service is used to migrate a database instead of local storage. Option​ ​D ​is​ ​incorrect:​ Direct Connect sets up a dedicated network connection to AWS. However it does not automate the data transfer to AWS.

40-A company has been using AWS cloud services for six months and have just finished a security review. Which of the following is considered a best practice in the security pillar of the well-architected framework?

Using the root user to create all-new user accounts, at any time

Monitoring and using alerts using CloudTrail and CloudWatch

Assigning Private IP address ranges to VPCs that do not overlap

Designing the system using elasticity to meet changes in demand
1/1 point
Explanation : Option B is correct. Monitoring and alerting for key metrics and events is the best practice of the Security pillar Option A is incorrect. For the root user, you should follow the best practice of using this login only to create another, an initial set of IAM users and groups for longer-term identity management operations Option C is incorrect. Non-overlapping Private IP addresses are in the Reliability pillar. D. Design using elasticity to meet demand is in the Performance Efficiency pillar (Design for Cloud Operations).

41-A company has a Redshift Cluster defined in AWS. The IT Operations team have ensured that both automated and manual snapshots are in place. Since the cluster is going to be run for a couple of years, Reserved Instances have been purchased. There has been a recent concern on the cost, being incurred by the cluster. Which step should be carried out to minimize the costs being incurred by the cluster?

A-Delete the manual snapshots.

Set the retention period of the automated snapshots to 35 days.

Choose to use Spot Instances instead of Reserved Instances.

Choose to use Instance store volumes to store the cluster data.

Otomatik anlık görüntüleri etkinleştirip etkinleştirmediğinizden bağımsız olarak, istediğiniz zaman istediğiniz zaman manuel bir anlık görüntü alabilirsiniz. Varsayılan olarak, el ile anlık görüntüler, kümenizi sildikten sonra bile süresiz olarak korunur. El ile anlık görüntü oluşturduğunuzda saklama süresini belirtebilir veya anlık görüntüyü değiştirerek saklama süresini değiştirebilirsiniz. Amazon Redshift konsolunu kullanarak bir anlık görüntü oluşturursanız, anlık görüntü saklama süresini varsayılan olarak 365 gün olarak ayarlar. Otomatik anlık görüntüler, 1(En Az) ila 35(Maks) gün arasındaki süre içinde (saklama süresi ayarlarına göre) otomatik olarak silinir. Bu nedenle, Otomatik anlık görüntüler yerine Manuel anlık görüntülerle ilgilenmeliyiz. Amazon Redshift, Otomatik Anlık Görüntülerde olduğu gibi Manuel anlık görüntüleri hiçbir zaman otomatik olarak silmez.

42-As a solutions architect, you need to design a multi-tier architecture for a project in AWS. The application contains three tiers: the frontend layer, business logic layer and storage layer. The frontend and business logic layers are implemented by Auto Scaling groups and Amazon DynamoDB is selected as the data storage option in the storage layer. Which of the following options is NOT a feature of this architecture?

Each layer is modularized and managed independently. 

The backend and data storage are not exposed to the internet and protected in private subnets.

The architecture is completely serverless so that users do not need to configure the desired number of servers or capabilities.

Frontend and backend servers can be configured in different availability zones for high availability.
1/1 point
Explanation : The multi-tier architecture in AWS has a number of features such as high availability and scalability, fault tolerant and security. The question asks for the option that is NOT a feature. Option C should be selected as you still need to configure the min/max/desired number of servers in ASGs and the read/write capabilities in DynamoDB tables. Option​ ​A ​is​ ​incorrect:​ Because the application is divided into three components and each component works independently. Option​ ​B ​is​ ​incorrect:​ Because the backend and data storage are located in private subnets. Users can only reach the frontend layer. Option​ ​C ​is​ CORRECT:​ Refer to the above explanations. This architecture is not completely serverless. Option​ ​D ​is​ ​incorrect:​ Because the servers in ASG can be put into several availability zones so that even if one AZ has an outage, the servers in other AZs can still work as normal

43- A company requires an open-source system for automating the deployment, scaling, and management of containerized applications. Which of the following would be ideal for such a requirement?

A-Use the Amazon Elastic Container Service for Kubernetes.

Install a custom orchestration tool on EC2 Instances.

 Use SQS to orchestrate the messages between docker containers. 

Use AWS Lambda functions to embed the logic for container orchestration.

Explanation: Amazon Elastic Container Service for Kubernetes (Amazon EKS) is a managed service that makes it easy for you to run Kubernetes on AWS without the requirement of installing and operating your own Kubernetes clusters. Kubernetes is an open-source system for automating the deployment, scaling, and management of containerized applications. Operating Kubernetes for production applications presents a number of challenges. You need to manage the scaling and availability of your Kubernetes masters and persistence layer by ensuring that you have chosen appropriate instance types, running them across multiple Availability Zones, monitoring their health, and replacing unhealthy nodes. You need to patch and upgrade your masters and worker nodes to ensure that you are running the latest version of Kubernetes. All this requires expertise and a lot of manual work. With Amazon EKS, upgrades and high availability are managed for you by AWS.

Kubernetes için Amazon Elastic Container Service (Amazon EKS), kendi Kubernetes kümelerinizi kurmanıza ve çalıştırmanıza gerek kalmadan Kubernetes'i AWS'de çalıştırmanızı kolaylaştıran yönetilen bir hizmettir. Kubernetes, kapsayıcılı uygulamaların dağıtımını, ölçeklenmesini ve yönetimini otomatikleştirmek için açık kaynaklı bir sistemdir. Üretim uygulamaları için Kubernetes'i çalıştırmak bir takım zorluklar sunar. Uygun bulut sunucusu türlerini seçtiğinizden emin olarak, bunları birden çok Erişilebilirlik Alanında çalıştırarak, durumlarını izleyerek ve sağlıksız düğümleri değiştirerek Kubernetes ana sunucularınızın ve kalıcılık katmanınızın ölçeklendirmesini ve kullanılabilirliğini yönetmeniz gerekir. Kubernetes'in en son sürümünü çalıştırdığınızdan emin olmak için ana ve çalışan düğümlerinizi yamalamanız ve yükseltmeniz gerekir. Bütün bunlar uzmanlık ve çok fazla manuel çalışma gerektirir. Amazon EKS ile yükseltmeler ve yüksek kullanılabilirlik AWS tarafından sizin için yönetilir.

44-You are building a microservice architecture in AWS for a web application. A Lambda function collects clients’ requests and forwards them to a standard SQS queue. Another Lambda function gets messages from the queue and processes them. Your manager is worried about the availability of the SQS queue which may become a single point of failure. How would you address this concern?

Create another SQS queue to provide a redundancy.

Select multiple availability zones when creating the SQS queue.

Configure the SQS queue to be the FIFO queue.

No actions are required as Amazon SQS uses redundant infrastructure to provide high availability.
1/1 point
Explanation : Option​ ​A ​is​ ​incorrect:​ Because there is no need of doing that as SQS service is highly available. Option​ ​B ​is​ ​incorrect:​ Because users cannot select availability zones when configuring the SQS queue. Option​ ​C ​is​ ​incorrect:​ Because both standard and FIFO queues provide high availability. Option​ ​D ​is​ CORRECT:​ SQS is a highly available system so no actions are required.

45-You maintain a DynamoDB table that stores customers’ subscription data. High availability is very important for the table and even if there is an outage in an AWS region, the application should still be able to access the data from other regions. Which method would you take to achieve this requirement?

Create a read replica in another region as a backup.

Configure a Multi-AZ backup for the DynamoDB table

Configure a global table to use DynamoDB as a multi-region database.

No actions required as DynamoDB is a global service.


Explanation : Amazon DynamoDB global tables provide a solution for deploying a multi-region, multi-master database. Option​ ​A ​is​ ​incorrect:​ Because DynamoDB does not have such a feature. Option​ ​B ​is​ ​incorrect:​ Because there is no need to configure Multi-AZ for a DynamoDB table and it is highly available by default Option​ ​C ​is​ CORRECT:​ With the DynamoDB global table, when one AWS region becomes unavailable, users can still access the same data in other regions. Option​ ​D ​is​ ​incorrect:​ Refer to option C.

46-You have a set of IIS Servers running on EC2 Instances. You want to collect and process the log files generated from these IIS Servers. Which service would be ideal to run in this scenario?

Amazon S3 for storing the log files and Amazon EMR for processing the log files

Amazon S3 for storing the log files and EC2 Instances for processing the log files

Amazon EC2 for storing and processing the log files

Amazon DynamoDB to store the logs and EC2 for running custom log analysis scripts

Amazon EMR, büyük miktarda veriyi işlemek ve analiz etmek için Apache Hadoop ve Apache Spark gibi büyük veri çerçevelerini AWS üzerinde çalıştırmayı basitleştiren, yönetilen bir küme platformudur. Bu çerçeveleri ve Apache Hive ve Apache Pig gibi ilgili açık kaynak projelerini kullanarak, verileri analitik amaçlar ve iş zekası iş yükleri için işleyebilirsiniz. Ek olarak, büyük miktarda veriyi Amazon Simple Storage Service (Amazon S3) ve Amazon DynamoDB gibi diğer AWS veri depolarına ve veritabanlarına dönüştürmek ve bu veritabanlarından taşımak için Amazon EMR'yi kullanabilirsiniz. B ve C seçenekleri kısmen doğrudur. Bu konuda yardımcı olacak hazır bir hizmetiniz olduğunda EC2 Bulut Sunucularının günlük dosyalarını işlemesi için bir ek yük olacaktır. DynamoDB günlük dosyalarını depolamak için ideal bir seçenek olmadığından D seçeneği geçersizdir.

47-You need to ensure that new objects being uploaded to an S3 bucket are available in another region, due to the criticality of the data hosted in the S3 bucket. How could you achieve this in the easiest way possible?

Enable Cross-Region Replication for the bucket.

Write a script to copy the objects to another bucket in the destination region.

Create an S3 snapshot in the destination region.

Enable versioning that will copy the objects to the destination region.
1/1 point
Explanation : Cross-Region Replication is a bucket-level configuration that enables automatic, asynchronous copying of objects across buckets in different AWS Regions.

48_You are working as an AWS Architect for a global media firm. They have web servers deployed on EC2 instances across multiple regions. For audit purposes, you have created a CloudTrail trail to store all CloudTrail event log files to the S3 bucket. This trail applies to all regions & is stored in S3 buckets at the EU-Central region. During last year’s audit, auditors have raised a query on the integrity of log files that are stored in the S3 buckets and tendered as Non-Compliance. Which feature could help you to gain compliance from Auditors for this query?

Use Amazon SSE-S3 encryption for the CloudTrail log file while storing it to S3 buckets.

Use Amazon SSE-KMS encryption for CloudTrail log file while storing it to S3 buckets.

Use an S3 bucket policy to grant access to only Security head for S3 buckets having CloudTrail log files.

D-Enable the CloudTrail log file integrity validation feature.

After you enable CloudTrail log file integrity, it will create a hash file called digest file which refers to logs that are generated. This digest file is saved in a different folder in the S3 bucket where log files are saved. Each of these digest files has the private key of public & private key pair. The DIgest file can be validated using the public key. This feature ensures that all the modifications made to CloudTrail log files are recorded. Option A is incorrect as by default all CloudTrail log files are delivered to S3 buckets using SSE-S3 encryption, this will not ensure the integrity of log files. Option B is incorrect as with Amazon SSE-KMS encryption for CloudTrail log file, there would be an additional layer of security for log files, but it won’t ensure the integrity of log files. Option C is incorrect as although this will restrict access to the bucket but won’t ensure that no modification has been done to log files post delivering in S3 buckets.

49- You work in the media industry and have created a web application where users will be able to upload photos they create, to your website. This web application must be able to call the S3 API in order to function properly. Where would you store your API credentials while maintaining the maximum level of security?

Save the API credentials to your PHP files.

Don’t save your API credentials. Instead, create a role in IAM and assign this role to an EC2 instance when you first create it. 

Save your API credentials in a public Github repository.

Pass API credentials to the instance using instance user data.
1/1 point
Explanation : Applications must sign their API requests with AWS credentials. Therefore, if you are an application developer, you need a strategy for managing credentials for your applications that run on EC2 instances. For example, you can securely distribute your AWS credentials to the instances, enabling the applications on those instances to use your credentials to sign requests, while protecting your credentials from other users. However, it&#39;s challenging to securely distribute credentials to each instance, especially those that the AWS creates on your behalfs, such as Spot Instances or instances in Auto Scaling groups. You must also be able to update the credentials on each instance when you rotate your AWS credentials. IAM roles are designed so that your applications can securely make API requests from your instances, without requiring you to manage the security credentials that the applications use.

50- You are working as an AWS Architect for a global insurance firm. For the web application, you are using S3 buckets and have configured CloudFront to cache image files. For audit purposes, you have created a CloudTrail trail in each region and the events logs files are logged in S3 bucket in the us-west-1 region. There have been changes in CloudFront which have caused all traffic being routed to the origin, resulting in increased latency for users in other continents. After scrutinizing CloudTrail logs, you found that there are duplicate CloudFront events being logged. What configuration changes would you perform to eliminate duplicate CloudFront logs?

A-Using AWS CLI, update CloudTrail trail to disable global service events that are delivered in all regions except US-West-1.

Using AWS CLI, change the configuration of a trail to logging a single region instead of logging all regions.

Using AWS console, update CloudTrail trail to disable global service events to be delivered in all regions except US-West-1.

Using the AWS console, change the configuration of a trail to logging a single region instead of logging all regions
0/1 point
Explanation : Amazon CloudFront is a global service for which events are delivered to CloudTrail trails which include global services. To avoid duplicate Amazon CloudFront events, you can disable these events from delivering to CloudTrail trails in all regions & enable in only one region. Options B & D is incorrect as if CloudTrail trail is changed to logging a single region, global service event logging is off automatically, this will disable CloudFront events being logged instead of avoiding duplicate logs. Option C is incorrect as Changes to Global service event logs can be done only via AWS CLI & not via AWS console.

51- You are working for a start-up firm that developed a new multilingual website for sharing images and video files. You are using EC2 instance to host this web application. To deliver these web content with the lowest latency to end-users, you have configured Amazon CloudFront which forward query strings to origin servers based on selected parameter values and also cache web content based upon these parameter values. During the trial, it was observed that caching is not happening based upon query strings resulting in these requests hitting origin servers. Which of the following need to be checked if CloudFront is caching properly based upon query strings? (Select Three)

Make sure that the distribution is an RTMP distribution.

B-Make sure that the delimiter character between query string parameters is a '&' character.

C-Check if Parameters' names and values are in the same case.

Make sure that the delimiter character between query string parameters is a “ / ” character.

E-Make sure that the distribution is a Web distribution.

Check only that the query parameter names are in the same case


Explanation : CloudFront Query String Forwarding only supports Web distribution. For query string forwarding, the delimiter character must be always a '&' character. Parameters' names and values used in the query string are case sensitive. Option A is incorrect as CloudFront Query String Forwarding does not support RTMP distribution. Option D is incorrect as Delimiter Character should be always '&', not '\' character. Option F is incorrect as in the case of Parameters in the query string, both the parameters' names and values are case sensitive.
52- IoT sensors monitor the number of bags that are handled at an airport. The data is sent back to a Kinesis stream with default settings. Every alternate day, the data from the stream is sent to S3 for processing. But it is noticed that S3 is not receiving all of the data that is being sent to the Kinesis stream. What could be the reason for this?

The sensors probably stopped working on some days, hence data is not sent to the stream.

S3 can only store data for a day.

C-The default retention period of the data stream is set to 24 hours only, and hence the failure.

Kinesis streams are not meant to handle IoT related data.
1/1 point
Explanation : Kinesis Streams support changes to the data record retention period of your stream. A Kinesis stream is an ordered sequence of data records, meant to be written to and read from in real-time. Data records are therefore stored in shards in your stream temporarily. The time period from when a record is added to when it is no longer accessible is called the retention period. A Kinesis stream stores the records from 24 hours (by default), up to 168 hours. Option A is incorrect, even though a possibility, cannot be considered as the right option. Option B is incorrect since S3 can store data indefinitely unless you have a lifecycle policy defined. Option D is incorrect because the Kinesis service is perfect for this sort of data ingestion.
Done

53-You are working as an AWS Administrator for a software firm that has a popular Web application hosted on EC2 instance in various regions. You are using AWS CloudHSM for offloading SSL/TLS processing from Web servers. Since this is a critical application for the firm, you need to ensure that proper backups are performed for data in AWS CloudHSM on a daily basis. What does the AWS CloudHSM use to perform a secure & durable backup?

A-Ephemeral backup key (EBK) is used to encrypt data & Persistent backup key (PBK) is used to encrypt EBK before saving data to the Amazon S3 bucket in the same region as that of AWS CloudHSM cluster.

b-Data Key is used to encrypt data & Customer Managed Key (CMK) is used to encrypt Data Key before saving data to the Amazon S3 bucket in the same region as that of AWS CloudHSM cluster.

c-Ephemeral Backup Key (EBK) is used to encrypt data & Persistent backup Key (PBK) is used to encrypt EBK before saving data to the Amazon S3 bucket in a different region than the AWS CloudHSM cluster. 

d-Data Key is used to encrypt data & Customer Managed Key (CMK) is used to encrypt Data Key before saving data to Amazon S3 bucket in a different region than the AWS CloudHSM cluster.

Explanation : To backup the AWS CloudHSM data to Amazon S3 buckets in the same region, AWS CloudHSM generates a unique Ephemeral Backup Key (EBK) to encrypt all data using AES 256-bit encryption key. This Ephemeral Backup Key (EBK) is further encrypted using Persistent Backup Key (PBK) which is also AES 256-bit encryption key. Option B is incorrect as Data Key & Customer Managed Key are not used by AWS CloudHSM for the encryption of data, instead of that EBK & PBK are used. Option C is incorrect. While taking the backup of data from different AWS CloudHSM clusters to the Amazon S3 bucket, the Amazon S3 bucket should be in the same region as that of the AWS CloudHSM cluster. Option D is incorrect as Data Key & Customer Managed Key are not used by AWS CloudHSM for the encryption of data, instead of that EBK & PBK are used for encrypting and saving data to the Amazon S3 bucket in the same region.

Açıklama : AWS CloudHSM verilerini aynı bölgedeki Amazon S3 klasörlerine yedeklemek için AWS CloudHSM, tüm verileri AES 256 bit şifreleme anahtarı kullanarak şifrelemek için benzersiz bir Geçici Yedekleme Anahtarı (EBK) oluşturur. Bu Geçici Yedekleme Anahtarı (EBK), ayrıca AES 256 bit şifreleme anahtarı olan Kalıcı Yedekleme Anahtarı (PBK) kullanılarak daha da şifrelenir. Veri Anahtarı ve Müşteri Tarafından Yönetilen Anahtar, verilerin şifrelenmesi için AWS CloudHSM tarafından kullanılmadığından, bunun yerine EBK ve PBK kullanıldığından B Seçeneği yanlıştır. C seçeneği yanlıştır. Farklı AWS CloudHSM kümelerinden verilerin yedeğini Amazon S3 klasörüne alırken Amazon S3 klasörü, AWS CloudHSM kümesiyle aynı bölgede olmalıdır. Veri Anahtarı ve Müşteri Tarafından Yönetilen Anahtar, AWS CloudHSM tarafından verilerin şifrelenmesi için kullanılmadığından, aynı bölgedeki Amazon S3 klasörüne veri şifrelemek ve kaydetmek için EBK ve PBK kullanıldığından D seçeneği yanlıştır.

54-You are working as an AWS Architect for a start-up company. You have developed an application that will read out AWS Blogs to AWS professionals using "Amazon Polly". You need to perform a trial with the "Amazon S3" blog, in which the first "S3" should be read as "Amazon Simple Storage Service" while all subsequent "S3" should be read as "S3". This test needs to be done in 2 different regions, us-west-1 & us-east-1. What could be done to perform the test successfully?

a-Using multiple Lexicons, create different alias for the word “ S3” & apply in different orders. Upload Lexicons in us-west-1 region & use for both regions. 

B-Using multiple Lexicons, create different alias for the word “ S3” & apply in different orders. Upload Lexicons in us-west-1 region & us-east-1 region.

c-Using a single Lexicon, create different alias for the word “ S3” & apply in different orders. Upload Lexicons in us-west-1 region & us-east-1 region.

d-Using a single Lexicon, create different alias for the word “ S3” & apply in different orders. Upload Lexicons in us-east-1 region & use for both regions.

Explanation : Lexicons are specific to a region. You will need to upload Lexicon in each region where you need to use it. For a single text which appears multiple times in the content, you can create an alias using multiple Lexicons to have different speech. Option A is incorrect as Lexicons needs to upload in all regions where content will be using Amazon Polly. Option C is incorrect as if a single word is repeating multiple times in content & needs to have different speech, we need to have multiple Lexicons created. Option D is incorrect as Lexicons needs to upload in all regions where content will be using Amazon Polly & to have a different speech for the single word being repeated multiple times, multiple Lexicons needs to be created.
Açıklama : Sözlükler bir bölgeye özgüdür. Lexicon'u kullanmanız gereken her bölgeye yüklemeniz gerekecektir. İçerikte birden çok kez görünen tek bir metin için, farklı konuşmaya sahip olmak için birden çok Sözlük kullanarak bir takma ad oluşturabilirsiniz. İçeriğin Amazon Polly'yi kullanacağı tüm bölgelerde Lexicons'ın yüklenmesi gerektiğinden A seçeneği yanlıştır. C seçeneği, içerikte tek bir kelime birden çok kez tekrarlanıyormuş gibi yanlıştır ve farklı konuşmalara sahip olması gerekir, birden fazla Lexicons oluşturmamız gerekir. İçeriğin Amazon Polly'yi kullanacağı tüm bölgelerde Lexicons'ın yüklenmesi ve tek bir kelimenin birden çok kez tekrarlanması için farklı bir konuşmaya sahip olması gerektiğinden D seçeneği yanlıştır, birden fazla Lexicons oluşturulması gerekir.

55- You create several SQS queues to store different types of customer requests. Each SQS queue has a backend node that pulls messages for processing. Now you need a service to collect messages from the frontend and push them to the related queues using the publish/subscribe model. Which service would you choose?

Amazon MQ

B-Amazon Simple Notification Service (SNS)

Amazon Simple Queue Service (SQS)

AWS Step Functions 

Explanation : AWS SNS is able to push notifications to the related SQS endpoints. SNS uses a publish/subscribe model that provides instant event notifications for applications. Option​ ​A ​is​ ​incorrect:​ Amazon MQ is a managed message broker service which is not suitable for this scenario. Option​ ​B ​is​ CORRECT:​ Because SNS uses Pub/Sub messaging to provide asynchronous event notifications. Please check https://aws.amazon.com/pub-sub-messaging/. Option​ ​C ​is​ ​incorrect:​ Because SQS does not use the publish/subscribe model. Option​ ​D ​is​ ​incorrect:​ AWS Step Functions coordinates application components using visual workflows. The service should not be used in this scenario.

AWS SNS, ilgili SQS uç noktalarına bildirim gönderebilir. SNS, uygulamalar için anında olay bildirimleri sağlayan bir yayınlama/abone olma modeli kullanır. A seçeneği ​yanlış:​ Amazon MQ, bu senaryo için uygun olmayan, yönetilen bir mesaj aracısı hizmetidir. B Seçeneği DOĞRU: Çünkü SNS, eşzamansız olay bildirimleri sağlamak için Pub/Sub mesajlaşmasını kullanır. Lütfen https://aws.amazon.com/pub-sub-messaging/ adresini kontrol edin. Seçenek C yanlıştır: Çünkü SQS yayınlama/abone olma modelini kullanmaz. D Seçeneği yanlıştır: AWS Step Functions, görsel iş akışlarını kullanarak uygulama bileşenlerini koordine eder. Hizmet bu senaryoda kullanılmamalıdır.

56-As a part of your application architecture requirements, the company has requested the ability to run analytics against all the combined log files from the Elastic Load Balancer. Which services would you use together to collect logs and process log file analysis in an AWS environment?

Amazon DynamoDB to store the logs and EC2 to run custom log analysis scripts

Amazon EC2 for storing and processing the log files

Amazon S3 for storing the ELB log files and EC2 for processing the log files analysis

Amazon S3 for storing ELB log files and Amazon EMR for processing the log files analysis
1/1 point
Explanation : Amazon EMR provides a managed Hadoop framework that makes it easy, fast, and cost-effective to process a vast amount of data across dynamically scalable Amazon EC2 instances. You can also run other popular distributed frameworks such as Apache Spark, HBase, Presto, and Flink in Amazon EMR, and interact with data in other AWS data stores such as Amazon S3 and Amazon DynamoDB. Amazon EMR securely and reliably handles a broad set of big data use cases, including log analysis, web indexing, data transformations (ETL), machine learning, financial analysis, scientific simulation, and bioinformatics.

Amazon EMR, dinamik olarak ölçeklenebilir Amazon EC2 bulut sunucularında büyük miktarda verinin işlenmesini kolay, hızlı ve uygun maliyetli hale getiren yönetilen bir Hadoop çerçevesi sağlar. Ayrıca Amazon EMR'de Apache Spark, HBase, Presto ve Flink gibi diğer popüler dağıtılmış çerçeveleri çalıştırabilir ve Amazon S3 ve Amazon DynamoDB gibi diğer AWS veri depolarındaki verilerle etkileşim kurabilirsiniz. Amazon EMR, günlük analizi, web dizine ekleme, veri dönüştürmeleri (ETL), makine öğrenimi, finansal analiz, bilimsel simülasyon ve biyoinformatik dahil olmak üzere çok çeşitli büyük veri kullanım senaryolarını güvenli ve güvenilir bir şekilde işler.

57-You have a set of Docker images that you use for building containers. You want to start using the Elastic Container Service and utilize the Docker images. You need a place to store these Docker images. What would you use for this purpose?

Use AWS DynamoDB to store the Docker images.

Use AWS RDS to store the Docker images.

Use EC2 Instances with EBS Volumes to store the Docker images.

Use the ECR Service to store the Docker images.

Explanation : Amazon Elastic Container Registry (ECR) is a fully-managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images. Amazon ECR is integrated with Amazon Elastic Container Service (ECS), simplifying your development to production workflow.

58-You have a set of Docker images that you use for building containers. You want to start using the Elastic Container Service and utilize the Docker images. You need a place to store these Docker images. What would you use for this purpose?

Use AWS DynamoDB to store the Docker images.

Use AWS RDS to store the Docker images.

Use EC2 Instances with EBS Volumes to store the Docker images.

Use the ECR Service to store the Docker images.
1/1 point
Explanation : Amazon Elastic Container Registry (ECR) is a fully-managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images. Amazon ECR is integrated with Amazon Elastic Container Service (ECS), simplifying your development to production workflow.

59-You are working with an educational website that provides online content for professional exams using WordPress. You have recently added Amazon Polly plugins to the website to provide students audio recordings for exam contents. You are getting customer feedback on the speech rate being too fast & continuous. What changes would you make in your content to resolve this? (Select Three)

A-Add a pause using SSML tag between appropriate words & paragraphs.

B-Convert commas in content into the period.

Convert period in content into commas.

Add a tag as “Reduced” for appropriate words & paragraphs.

E-Add a tag as “ Strong” for appropriate words & paragraphs.

Explanation : Using SSML tags, we can control the speech generated by Amazon Polly. In the above example, using SSML tags, convert commas to period & tag words and paragraphs as “Strong”, will help to control the speech speed, adds appropriate pause & emphasis on appropriate words slowing speaking rate. Option C is incorrect as commas will not insert a pause in the speech during the reading text. Option D is incorrect as adding the tag as “Reduced” will speed up speech rate, along with a decrease in volume.

60-You are building a large-scale confidential documentation web server on AWS such that all of its documentation will be stored on S3. One of the requirements is that it should not be publicly accessible from S3 directly, and CloudFront would be needed to accomplish this. Which method would satisfy the outlined requirements?

Create an Identity and Access Management (IAM) User for CloudFront and grant access to the objects in your S3 bucket to that IAM User.

Create an Origin Access Identity (OAI) for CloudFront and grant access to the objects in your S3 bucket to that OAI. 

Create individual policies for each bucket the documents are stored in, and grant access only to CloudFront in these policies.

Create an S3 bucket policy that lists the CloudFront distribution ID as the Principal and the target bucket as the Amazon Resource Name (ARN).
1/1 point
Explanation : If you want to use CloudFront signed URLs or signed cookies to provide access to objects in your Amazon S3 bucket, you probably want to prevent users from accessing your Amazon S3 objects using Amazon S3 URLs. If users access your objects directly in Amazon S3, they bypass the controls provided by CloudFront signed URLs or signed cookies. For example, control over the date and time that a user can no longer access your content and control over which IP addresses can be used to access the content. In addition, if users access objects both through CloudFront and directly by using Amazon S3 URLs, CloudFront access logs are less useful because they're incomplete.

61.Your company has a legacy application that uses the monolithic architecture. You need to design a new microservices architecture for the application and host it in AWS. The application should be dockerized so that it can be easily deployed. Which of the following AWS services would you choose to host the application?

Elastic Kubernetes Engine

Amazon Lambda

Elastic Container Registry

Elastic Container Service
1/1 point
Explanation : Option​ ​A ​is​ ​incorrect:​ Because the service name should be Elastic Kubernetes Service (EKS). Option​ ​B ​is​ ​incorrect:​ Because Amazon Lambda cannot run a Docker container. Option​ ​C ​is​ ​incorrect:​ Because Elastic Container Registry is the service to store Docker images and it cannot run Docker containers. Option​ ​D ​is​ CORRECT:​ Because Elastic Container service (ECS) allows users to easily run applications in Docker containers. ECS is a suitable AWS compute service for microservices.

62-You have a web application that processes customer orders. The frontend application forwards the order messages to an SQS queue. The backend contains an Elastic Load Balancer and an Auto Scaling group. You want the ASG to auto scale depending on the queue size. Which of the following CloudWatch metrics would you choose to discover the SQS queue length?

ApproximateNumberOfMessagesVisible

NumberOfMessagesReceived

NumberOfMessagesDeleted

ApproximateNumberOfMessagesNotVisible
1/1 point
Explanation : The backend nodes can scale based on the queue length. Option​ ​A ​is​ CORRECT:​ ApproximateNumberOfMessagesVisible describes the number of messages available for retrieval. It can be used to decide the queue length. Option​ ​B ​is​ ​incorrect:​ Because NumberOfMessagesReceived is the number of messages returned by calls to the ReceiveMessage action. It does not measure the queue length. Option​ ​C ​is​ ​incorrect:​ Because NumberOfMessagesDeleted is the number of messages deleted from the queue. It is not suitable to be used in this scenario. Option​ ​D ​is​ ​incorrect:​ Because ApproximateNumberOfMessagesNotVisible measures the number of messages in flight. It should not be used here.

63-You are performing a Load Testing exercise on your application that is hosted on AWS. While testing your Amazon RDS MySQL DB Instance, you notice that your application becomes nonresponsive when you reach 100% CPU utilization. Your application is read-heavy. Which methods would help scale your data-tier to meet the application’s needs? (Select Three)

Add Amazon RDS DB Read Replicas, and have your application direct read queries to them.

Add your Amazon RDS DB instance to Storage Auto Scaling, and set your desired maximum storage limit.

Use an Amazon SQS queue to throttle data going to the Amazon RDS DB Instance.

Use ElastiCache to cache common queries of your Amazon RDS DB.

Shard your data set among multiple Amazon RDS DB Instances.

Enable Multi-AZ for your Amazon RDS DB Instance.
2/3 points
Expl: Amazon RDS Read Replicas provide enhanced performance and durability for Option B is incorrect because it is not an ideal way to scale a database. Amazon RDS Auto Scaling is to scale the storage capacity. If the storage capacity threshold is reached, then capacity will be scaled through Auto Scaling. RDS Auto Scaling does not look for the CPU utilization threshold so it cannot be a solution for bottlenecks to read heavy databases. Option C is not an ideal choice. Because our application is read-heavy and this is the cause of the problem that we are facing with the RDS. So for this issue, Creating Read replicas, Elastic cache implementation, and Sharding the dataset are the ways through which we can tackle this issue. But if we have too may PUT requests for the DB, that is causing the issue then we can create an SQS queue and store these PUT requests in the message queue and then process it accordingly. Option F is invalid because the Multi-AZ feature is only a failover option.

64-You have an application that has been dockerized. You plan to deploy the application in an AWS ECS cluster. As the application gets configuration files from an S3 bucket, the ECS containers should have the AmazonS3ReadOnlyAccess permission. What is the correct method to configure the IAM permission?

Add an environment to the ECS cluster configuration to allow the S3 read only access.

Add the AmazonS3ReadOnlyAccess permission to the IAM entity that creates the ECS cluster.

Modify the user data of ECS instances to assume an IAM role that has the AmazonS3ReadOnlyAccess permission.

Attach the AmazonS3ReadOnlyAccess policy to the ECS container instance IAM role. Attach this role when creating the ECS cluster.
0/1 point
Explanation: Correct Answer – D ECS containers have access to permissions that are supplied to the container instance role. Option A is incorrect: Because ECS cluster uses the container instance IAM role instead of environment variables to control its permissions. Option B is incorrect: Because the IAM entity that creates the ECS cluster does not pass its permissions to the ECS cluster. You need to conjure an IAM role and attach it to the ECS cluster. Option C is incorrect: This is not the correct method to configure IAM permissions for an ECS cluster. Option D is CORRECT: After the AmazonS3ReadOnlyAccess policy is attached to the IAM role, the ECS instances can use the role to get objects from S3.

65-Your company currently has a set of EC2 Instances hosted in AWS. The states of these instances need to be monitored and each state needs to be changed when a metric breaches a threshold value. Which step could be helpful to fulfill this requirement? (SELECT TWO)

Use CloudWatch logs to store the state change of the instances.

Create an Amazon CloudWatch alarm that monitors an Amazon EC2 instance.

Use SQS to trigger a record to be added to a DynamoDB table.

Use AWS Lambda to store a change record in a DynamoDB table.
1/2 points
Explanation: Option A is correct. Using Cloudwatch logs collect, store, view, and search logs from AWS and non-AWS resources. Option B is correct. CloudWatch alarms are used to trigger notifications for any metric. Alarms can go to auto-scaling, EC2 actions(stop, terminate, recover, or reboot) and SNS notifications. Option C is incorrect as SQS cannot be used for monitoring. Option D is incorrect as AWS Lambda cannot be used for monitoring.

66- You have an S3 bucket that receives photos uploaded by customers. When an object is uploaded, an event notification is sent to an SQS queue with the object details. You also have an ECS cluster that gets messages from the queue to do the batch processing. The queue size may change greatly depending on the number of incoming messages and backend processing speed. Which metric would you use to scale up/down the ECS cluster capacity?

The number of messages in the SQS queue.

Memory usage of the ECS cluster.

Number of objects in the S3 bucket.

Number of containers in the ECS cluster.
0/1 point
Explanation: Correct Answer – A In this scenario, SQS queue is used to store the object details which is a highly scalable and reliable service. ECS is ideal to perform batch processing and it should scale up or down based on the number of messages in the queue. Option A is CORRECT: Users can conjure a CloudWatch alarm based on the number of messages in the SQS queue and notify the ECS cluster to scale up or down using the alarm. Option B is incorrect: Because the memory usage may not be able to reflect the workload. Option C is incorrect: Because the number of objects in S3 cannot determine if the ECS cluster should change its capacity. Option D is incorrect: Because the number of containers cannot be used as a metric to trigger an auto-scaling event.

67-You have planned to host a web application on AWS. You create an EC2 Instance in a public subnet which needs to connect to an EC2 Instance that will host an Oracle database. Which steps would ensure a secure setup? (SELECT TWO)

Place the EC2 Instance with the Oracle database in the same public subnet as the Webserver for faster communication.

Place the ec2 instance in a public subnet and the oracle database in a private subnet.

Create a database Security group which allows incoming traffic only from the Web server's security group.

Ensure that the database security group allows incoming traffic from 0.0.0.0/0
1/2 points
Explanation: Correct Answer – B and C The best and most secure option is to place the database in a private subnet. The below diagram from AWS Documentation shows this setup. Also, you ensure that access is not allowed from all sources but only from the web servers. Option A is incorrect because as per the best practice guidelines, DB instances are placed in Private subnets and allowed to communicate with web servers in the public subnet. Option D is incorrect because allowing all incoming traffic from the Internet to the DB instance is a security risk.

68-You have an RDS instance in a VPC. In the same AWS account, there is an EC2-Classic instance that does not belong to any VPC. The EC2 instance needs to communicate with the RDS instance using its private IPv4 address. Which method would you use?

Modify the security group of the RDS instance to allow the incoming traffic from the EC2-Classic instance.

Attach a security group to the EC2 instance to allow all outgoing traffic.

Enable PrivateLink for the VPC and link the EC2-Classic instance.

Enable ClassicLink for the VPC and link the EC2 instance to the VPC.
0/1 point
Expalanation: Correct Answer – D For the communication between EC2-Classic instance and resources in VPC, ClassicLink should be used. Option A is incorrect: Even if the security group is modified, the EC2-Classic instance still cannot talk with the RDS instance in the VPC. Option B is incorrect: Same as option A. Option C is incorrect: Because PrivateLink is used for resources within the VPC. It is not suitable for EC2-Classic instances. Option D is CORRECT: Because ClassicLink is the correct method to link EC2-Classic instances to VPC resources. Check the above link for how to work with ClassicLink.
Done
