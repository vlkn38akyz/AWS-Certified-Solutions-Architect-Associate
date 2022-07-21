# AWS-Certified-Solutions-Architect-Associate

1. You are working as an AWS Architect for a start-up company. They have a two-tier production website. Database servers are spread across multiple Availability Zones and are stateful. You have configured Auto Scaling Group for these database servers with a minimum of 2 instances & maximum of 6 instances. During post-peak hours, you observe some data loss. Which feature needs to be configured additionally to avoid future data loss (and copy data before instance termination)?

a-Modify the cooldown period to complete custom actions before the Instance terminates.

b-Add lifecycle hooks to the Auto Scaling group.

c-Customize Termination policy to complete data copy before termination.

d-Suspend Terminate process that will avoid data loss.

Açıklama: Otomatik Ölçeklendirme grubuna lifecycle hooks eklemek, örneği sonlandırmadan önce bekleme durumuna getirir. Bu bekleme durumu sırasında, durum bilgisi olan bir örnekten kritik operasyonel verileri almak için özel etkinlikler gerçekleştirebilirsiniz. Varsayılan Bekleme süresi 1 saattir. Bekleme süresi sona ermeden önce örnekten veri kopyalamaya yardımcı olmayacağından A seçeneği yanlıştır. Ölçeklendirme sırasında hangi örneklerin önce sonlandırılacağını belirtmek için Sonlandırma ilkesi kullanıldığından C seçeneği yanlıştır, Otomatik Ölçeklendirme grubu için sonlandırma ilkesini yapılandırmak, örnek sonlandırmadan önce verileri kopyalamaz. Seçenek D yanlıştır, çünkü Sonlandırma politikasını Askıya Almak veri kaybını engellemez, ancak diğer süreçleri kesintiye uğratır ve ölçeğin artmasını engeller.






