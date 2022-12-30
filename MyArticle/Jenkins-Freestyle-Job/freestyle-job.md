Jenkins Freestyle Job ve Trigger Oluşturma

Created by Nicolas De loof & Kseniia Nenasheva
Herkese Merhaba!

Bir önceki yazımda Jenkins’i kurmuş ve Dashboard’da “Welcome to Jenkins” yazısını görmüştük. Bizler DevOps mühendisi olarak bu arayüzle artık sık sık karşılaşacağız.


Dashboard
ilk item tipimize basit bit job oluşturarak başlamak istiyorum.

Öncelikle Job nedir? kısaca hatırlayalım.

Job: Bir jenkins projesidir. Otomatize etmek istediğimiz işleri burada belirleriz. Örneğin, job config üzerinden şu repository’i çek, şu şartlarda build et, şu testleri çalıştır ve belirlenen kişilere mail at gibi işlemleri burada belirleriz. Farklı Job’lar oluşturup otomotize etmek istediğimiz işleri birbirleri ile tetikleyerek çalıştırabilirsiniz.

Şimdi Dashboard’a geri dönebiliriz.


New Itrem
ilk olarak solda bulunan “New Item” seçeneğine tıklayarak

Job’a ismini girdikten sonra sorulması gereken soruları sorup bizim belirleyeceğimiz bir script yazıp job’umuzu oluşturacağız.


Job1
Item name ismini “job1” girdim. “Freestyle project” e tıklayıp, “ok” diyerek devam ediyorum.


Job1-decsription
açılan pencerede Jenkins bizden ilk olarak description girmemizi isteyecek daha sonra mouse’u aşağıya doğru kaydırıyorum. Şimdilik Herhangi bir “Source Code Management” kullanmıyorum.


job1-a
Kendimiz Build edeğemiz için bir Trigger ve Environment de kullanmadan aşağıya doğru iniyorum.


job1-b
“Build Steps”e gelip “Execute shell” ekliyoruz.


job1-c
ve açılan Command bölümüne $ echo “Hello World” shell komutunu ekliyoruz. Apply ve Save yapıyoruz. İlk Job’ımız hazır. 👏👏👏


job1-build
Dashboard a tıklayıp Job’ınızı inceleyebilirsiniz..


job1-bulld-a
en son ne zaman başarılı şekilde koştuğunu
Ne zaman arıza verdiğini
en son koşturulduğunda ne kadar sürmüş
açıklamalarını görebilirsiniz. Başarılı bir pipeline ise hava durumu gibi bize güneş işareti, fazla hata veren bir pipeline olursa yağmurlu işareti gönderir.


job1-build-b
Build etmek için sağda bulunan “(▶)️” düğmesine ya da direkt olarak Job1 in üstüne tıklayarak;


job1-build-c
sol tarafta bulunan “ Build Now” seçeneğine tıklarız. Ve çalışmaya başlar.


job1-build-d
Eğer başarılı bir şekilde icra edildiyse, işaretlediğim yerde gördüğünüz gibi yeşil renkte tik atar. Ve her koştuğunda “#” ile bize numara verir. Bu numaraya tıklarsak ,


Job1-output
Console Output unu görebilirsiniz.


job1-workspace
Jenkins Server’da /var/lib/jenkins/workspace klasörünün altında Job1 klasörünüz oluştu.

Şimdi gelin ikinci bir Freestyle Job oluşturup Trigger ile birbirine bağlayalım.


job2
name’e , “Job2” diyerek; Freestyle project seçip, “OK” diyerek devam ediyorum.


job2-decription
Description olarak “This is my second Job.” diyerek aşağıya geçiyorum.


job2-a
Build Triggers bölümünde , “Build after other projects are build” seçeneğine tıklayıp. Bir önceki Job’umuzun ismini giriyoruz. Yani bu tetikleyiciye “bir önceki job çalıştıktan sonra çalışmaya başla” demiş oluyoruz. Apply Save dedim ve kaydettim.


job2-b
Burada gördüğünüz gibi Job2 nin Job1'e bağlı olduğunu belirtiyor. Fakat, Sol altta henüz Build olmadığı ve numara atanmadığını görüyoruz. Şimdi Job1 e gidip ikinci kez Build Now edeceğim.


job1-trigger-build
Daha sonra Job2 ye gelip baktığımda ;


job2-trigger-build
Otomatik olarak Job2'nin Build olduğunu görüyoruz.

Bu şekilde farklı Job’lar oluşturup Trigger ile birbirini tetikleyerek birbirine bağlı Job’lar oluşturabilirsiniz.

Jenkins ilk çıktığında amacı birbirine bağlı Job’lar oluşturmaktı. Fakat dezavantajı, Freestyle Job’larda, Jenkins restart edildiği zaman işlemler durur çalışması kesilir. Pipeline’da ise jenkins restart edilse bile işlemler devam eder. Çalışması kesilmez. Bir sonraki yazımda bu farklı görevleri tek bir pipeline’da nasıl oluşturacağımızı göreceğiz. Görüşmek üzere 🙋‍♀️