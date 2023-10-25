# Kubernates Alıştırma

## Senaryo-2: İki Ayrı Ortamda Uygulama Dağıtımı
Farklı birinci ve ikinci ortamlarda aynı uygulamayı dağıtarak ve dört ayrı Deployment kullanarak Kubernetes'te çalıştıracaksınız. İşte adımlar:
- Bir Python veya Node.js web uygulaması oluşturun.
- İki farklı Docker imajı oluşturun: "web-app:v1" ve "web-app:v2".
- İlk ortamda "web-app:v1" Docker imajını kullanarak bir Deployment ve Servis oluşturun.
- İkinci ortamda "web-app:v2" Docker imajını kullanarak aynı uygulamayı dağıtın.
- İlk ve ikinci ortamları izole eden iki farklı - ClusterIP tipi servis oluşturun.
- İki ortamda çalışan uygulamalara servisler üzerinden erişmeye çalışın ve sonuçları karşılaştırın.

Namespace oluşturmak için;

```bash
  kubectl create namespace uygulamav1
```
```bash
  kubectl create namespace uygulamav2
```

Oluşturulan namespace görüntülemek için;

```bash
  kubectl get ns
```

Deployment oluşturmak için;

```bash
  kubectl create deployment -f deployment-pythonv1.yaml
```
```bash
  kubectl create deployment -f deployment-pythonv2.yaml
```
Oluşan deploymentların namespacede çalıştığını kontrol etmek için; 

```bash
  kubectl get deployment -n uygulamav1
```
```bash
  kubectl get deployment -n uygulamav2
```
Servis manifest dosyası oluşturmak için; 

```bash
  kubectl create -f service-pythonv1.yaml
```
```bash
  kubectl create -f service-pythonv2.yaml
```
