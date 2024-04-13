---
title: Трейси для системних компонентів Kubernetes
reviewers:
- logicalhan
- lilic
content_type: concept
weight: 90
---

<!-- overview -->

{{< feature-state for_k8s_version="v1.27" state="beta" >}}

Трейси системних компонентів реєструють затримку та звʼязки між операціями у кластері.

Компоненти Kubernetes відправляють трейси за допомогою [Протоколу OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/protocol/otlp.md#opentelemetry-protocol-specification) з експортером gRPC і можуть бути зібрані та направлені до різних систем відслідковування за допомогою [OpenTelemetry Collector](https://github.com/open-telemetry/opentelemetry-collector#-opentelemetry-collector).

<!-- body -->

## Збір трейсів {#trace-collection}

Для повного посібника зі збору трейсів та використання колектора див. [Початок роботи з OpenTelemetry Collector](https://opentelemetry.io/docs/collector/getting-started/). Однак є кілька речей, на які варто звернути увагу, що є специфічними для компонентів Kubernetes.

Типово компоненти Kubernetes експортують трейси за допомогою експортера grpc для OTLP на
[порт IANA OpenTelemetry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml?search=opentelemetry), 4317. Наприклад, якщо колектор працює як sidecar контейнер для компонента Kubernetes, наступна конфігурація приймача збере спани (spans) та відправить їх у стандартний вивід:

```yaml
receivers:
  otlp:
    protocols:
      grpc:
exporters:
  # Замініть цей експортер на експортер для вашої системи
  logging:
    logLevel: debug
service:
  pipelines:
    traces:
      receivers: [otlp]
      exporters: [logging]
```

## Трейси компонентів {#component-traces}

### Трейси kube-apiserver {#kube-apiserver-traces}

Kube-apiserver генерує спани для вхідних HTTP-запитів та для вихідних запитів до веб-хуків, etcd та повторних запитів. Він передає [W3C Trace Context](https://www.w3.org/TR/trace-context/) з вихідними запитами, але не використовує контекст трейса, доданий до вхідних запитів, оскільки kube-apiserver часто є загальнодоступною точкою доступу.

#### Увімкнення трейсів в kube-apiserver {#enabling-tracing-in-the-kube-apiserver}

Щоб увімкнути трейси, надайте kube-apiserver файл конфігурації тресів з `--tracing-config-file=<шлях-до-конфігу>`. Це приклад конфігурації, яка записує спани для 1 з 10000 запитів та використовує типову точку доступу OpenTelemetry:

```yaml
apiVersion: apiserver.config.k8s.io/v1beta1
kind: TracingConfiguration
# типове значення
#endpoint: localhost:4317
samplingRatePerMillion: 100
```

Для отримання додаткової інформації про структуру `TracingConfiguration`, див. [API сервера конфігурації (v1beta1)](/docs/reference/config-api/apiserver-config.v1beta1/#apiserver-k8s-io-v1beta1-TracingConfiguration).

### Трейси kubelet {#kubelet-traces}

{{< feature-state feature_gate_name="KubeletTracing" >}}

Інтерфейс CRI kubelet та автентифіковані http-сервери інструментовані для генерації спанів трейсів. Як і apiserver, адресу та частоту зразків можна налаштувати. Контекст трейсів також налаштований. Рішення про зразок батьківського спану завжди береться до уваги. Частота зразків трейсів, надана в конфігурації, застосовуватиметься до спанів без батьків. Ввімкнено без налаштованої точки доступу, типова адреса приймача OpenTelemetry Collector — "localhost:4317".

#### Увімкнення трейсів в kubelet {#enabling-tracing-in-the-kubelet}

Щоб увімкнути трейси, застосуйте [конфігурацію](https://github.com/kubernetes/component-base/blob/release-1.27/tracing/api/v1/types.go). Це приклад шматка конфігурації kubelet, що записує спани для 1 з 10000 запитів та використовує типову точку доступу OpenTelemetry:

```yaml
apiVersion: kubelet.config.k8s.io/v1beta1
kind: KubeletConfiguration
featureGates:
  KubeletTracing: true
tracing:
  # типове значення
  #endpoint: localhost:4317
  samplingRatePerMillion: 100
```

Якщо `samplingRatePerMillion` встановлено на мільйон (`1000000`), то кожен спан буде відправлений до експортера.

Kubelet у Kubernetes v{{< skew currentVersion >}} збирає спани зі збирання сміття, процесів синхронізації Podʼів, а також кожного методу gRPC. Kubelet передає контекст трейсів із запитами gRPC, щоб контейнерні середовища з інструментованими трейсами, такі як CRI-O та containerd, могли асоціювати їх експортовані спани з контекстом трейсів від kubelet. Отримані трейси будуть мати посилання батько-дитина між спанами kubelet та контейнерним середовищем, надаючи корисний контекст при налагодженні вузла.

Зверніть увагу, що експортування спанів завжди супроводжується невеликим перевантаженням мережі та CPU, залежно від загальної конфігурації системи. Якщо в кластері, в якому увімкнено трейси, виникає будь-яка проблема, така як ця, то помʼякшіть проблему шляхом зменшення `samplingRatePerMillion` або повністю вимкніть трейси, видаливши конфігурацію.

## Стабільність {#stability}

Інструментування трейсів все ще перебуває в активній розробці та може змінюватися різними способами. Це стосується назв спанів, приєднаних атрибутів, інструментованих точок доступу та інших. До того часу, поки ця функція не стане стабільною, не надається жодних гарантій зворотної сумісності для інструментів трейсів.

## {{% heading "whatsnext" %}}

* Прочитайте про [Початок роботи з OpenTelemetry Collector](https://opentelemetry.io/docs/collector/getting-started/)