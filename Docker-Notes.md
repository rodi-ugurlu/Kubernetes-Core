# Docker

## Docker Nedir?

Docker, uygulamaları konteyner adı verilen hafif, taşınabilir ve izole ortamlarda paketlemek ve çalıştırmak için kullanılan bir platformdur. Konteynerlar, bir uygulamanın çalışması için gerekli tüm bağımlılıkları (kütüphaneler, kod, runtime, vb.) içerir. Bu sayede uygulama her ortamda (geliştirme, test, production) tutarlı şekilde çalışır.

## Docker Image Nedir?

Docker Image'ı, container oluştururken kullanılan şablon gibi düşünebiliriz. Örneğin projemizde PostgreSQL ve Kafka olduğunu varsayalım. Projemizin çalışması için bunların image'lerini ayrı ayrı container'lar olarak çalıştırmamız gerekir. Tek bir image'a hepsini koymayız! Yani container tarifi diyebiliriz.

## Docker File Nedir?

Dockerfile, uygulamanızı Docker imajına çeviren komut listesidir. Daha basit bir ifadeyle, bizim yerimize bir sanal bilgisayar oluşturup içine gerekli ortamı hazırlar.

## Docker File Nasıl Yazılır?

Bunu örnek bir DockerFile'ı inceleyerek anlatmak daha mantıklıdır:

```dockerfile
FROM amazoncorretto:21
COPY target/*.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]
```

### Satır Satır Açıklama:

* **FROM amazoncorretto:21**
  Git bana Docker Hub'tan Amazon Corretto'nun Java 21 image'ini indir.

* **COPY target/\*.jar app.jar**
  Projemin kök dizinindeki `target` klasörünün altında bulunan jar uzantılı dosyayı kopyala ve sanal bilgisayarın kök dizinine `app.jar` olarak yerleştir.

* **ENTRYPOINT \["java","-jar","app.jar"]**
  Container her başladığında, `java -jar app.jar` komutunu çalıştır (buradaki container'ı sanal bilgisayar gibi düşünebiliriz).

## En Çok Kullanılan Docker Komutları

### Image İşlemleri

```bash
docker build -t isim:versiyon .          # Image oluştur
docker images                            # Image'ları listele
docker rmi isim:versiyon                 # Image sil
```

### Container Başlatma/Durdurma

```bash
docker run -d -p 8080:8080 --name container_ismi image_ismi  # Container çalıştır
docker ps                                 # Çalışan container'ları göster
docker ps -a                              # Tüm container'ları göster
docker stop container_ismi                # Container durdur
docker start container_ismi               # Container başlat
docker restart container_ismi             # Container yeniden başlat
docker rm container_ismi                  # Container sil
docker rm -f container_ismi               # Container zorla sil
```

### Container İçi İşlemler

```bash
docker logs container_ismi                # Logları görüntüle
docker logs -f container_ismi             # Logları takip et
docker exec -it container_ismi bash       # Container içine gir
docker exec container_ismi komut          # Container'da komut çalıştır
```

### Temizlik

```bash
docker system prune                      # Kullanılmayanları temizle
docker system prune -a                   # Her şeyi temizle
```

### Docker Hub

```bash
docker pull image_ismi                   # Image indir
docker push kullanici_adi/image_ismi     # Image yükle
```

### Network

```bash
docker network ls                        # Network'leri listele
docker network create ag_ismi            # Network oluştur
```

### Volume

```bash
docker volume ls                         # Volume'leri listele
docker volume create volume_ismi         # Volume oluştur
```
