# Kubernetes Nedir?

Kubernetes, konteynerleri (container) otomatik olarak dağıtan, yöneten ve ölçekleyen bir orkestrasyon sistemidir. Yani birçok container tek tek manuel olarak yönetilmek yerine, Kubernetes tarafından merkezi şekilde kontrol edilir.

## Kubernetes Temel Kavramlar

- Cluster
  Kubernetes’in tamamına cluster denir. Bir cluster birden fazla makineden oluşabilir.

- Node
  Cluster içindeki her bir makineye node denir. Bunlar çiftlikteki ahırlar gibi düşünülebilir. Her node üzerinde pod’lar çalışır.

- Namespace
  Cluster içinde farklı projeleri veya ortamları birbirinden ayırmak için namespace kullanılır. Örneğin, `playground` isimli bir namespace varsa, o namespace içindeki kaynaklar (pod, service, vs.) diğerlerinden izole olur.

- Pod
  Kubernetes’te çalıştırılabilir en küçük birimdir. Bir pod, bir veya birden fazla container içerir.

- Deployment
  Pod’ların yaşam döngüsünü yöneten nesnedir. Pod sayısını artırmak, azaltmak, güncellemek veya rollback yapmak Deployment ile yapılır.

- Service
  Pod’lara erişim noktası sağlar. Çünkü pod isimleri ve IP adresleri değişebilir. Service, pod’lar için sabit bir adres gibi davranır. Ayrıca load balancing yaparak yükü pod’lar arasında dağıtır.

- Ingress
  Cluster dışından gelen HTTP(S) trafiğini doğru servislere yönlendirir. Yani dış dünyadan erişim kapısıdır.

## Kubernetes konusunu daha iyi açıklamak için kendimce bir çiftlik metaforu yazdım umarım anlamanıza yardımcı olur
Kubernetes’i bir çiftlik gibi düşünebiliriz:

- Cluster: Çiftliğin kendisi.
- Node: Çiftlikteki her bir ahır. Her ahırda farklı hayvanlar (pod’lar) bulunur.
- Namespace: Çiftlikteki farklı alanlar (örneğin sebze bahçesi, hayvan barınağı).
  Burada şöyle de düşünebiliriz: cluster çiftliklerin tamamını içinde bulunan bir kare olsaydı, bu çiftliklerin karışmaması için her birine birer ad vermemiz gerekirdi. İşte buna namespace diyebiliriz.
- Pod: Çiftlikteki her bir hayvan.
- Deployment: Hayvanların bakımı ve yönetimini yapan çiftçi. Kaç hayvan olacağını belirler, hasta olanı iyileştirir, eksilenin yerine yenisini koyar.
- Service: Hayvanlara ulaşmak için sabit bir kapı. Hangi hayvan nerede olursa olsun bu kapı üzerinden ulaşılır.
- Ingress: Çiftliğe dışarıdan gelen ziyaretçiler için giriş kapısı.

## Rolling Update ve Rollback

- Rolling Update: Yeni bir versiyon pod’ları yavaş yavaş devreye alınır. Eski pod’lar çalışmaya devam ederken yenileri sırayla ayağa kaldırılır.
- Rollback: Yanlış bir güncelleme yapılırsa önceki versiyona hızlıca geri dönülür.