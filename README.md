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
