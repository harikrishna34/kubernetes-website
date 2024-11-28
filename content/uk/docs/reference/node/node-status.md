---
content_type: reference
title: Стан вузла
weight: 80
---

<!-- overview -->

Стан [вузла](/uk/docs/concepts/architecture/nodes/) у Kubernetes є критичним аспектом управління кластером Kubernetes. У цій статті ми розглянемо основи моніторингу та підтримки стану вузлів, щоб забезпечити справний та стабільний кластер.

## Поля стану вузла {#node-status-fields}

Стан вузла містить наступну інформацію:

* [Адреси](#addresses)
* [Стани](#condition)
* [Місткість та Доступність](#capacity)
* [Інформація](#info)

Ви можете використовувати команду `kubectl` для перегляду стану вузла та інших деталей:

```shell
kubectl describe node <insert-node-name-here>
```

Кожен розділ вихідних даних описано нижче.

## Адреси {#addresses}

Використання цих полів варіюється залежно від вашого постачальника хмарних послуг або конфігурації на голому залізі.

* HostName: Імʼя хосту, яке повідомляється ядром вузла. Може бути перевизначене за допомогою параметра kubelet `--hostname-override`.
* ExternalIP: Як правило, це IP-адреса вузла, яка доступна ззовні кластера.
* InternalIP: Як правило, це IP-адреса вузла, яка доступна лише всередині кластера.

## Стани {#condition}

Поле `conditions` описує стан усіх `Running` вузлів. Прикладами умов є:

{{< table caption = "Стан вузлів та опис, коли кожен стан застосовується." >}}
| Умова вузла          | Опис |
|----------------------|------|
| `Ready`              | `True`, якщо вузол справний та готовий приймати Podʼи, `False`, якщо вузол не справний і не приймає Podʼи, та `Unknown`, якщо контролер вузла не отримав інформацію від вузла протягом останнього `node-monitor-grace-period` (стандартно 40 секунд) |
| `DiskPressure`       | `True`, якщо є тиск на розмір диска, тобто якщо місткість диска низька; інакше `False` |
| `MemoryPressure`     | `True`, якщо є тиск на памʼять вузла, тобто якщо памʼять вузла низька; інакше `False` |
| `PIDPressure`        | `True`, якщо є тиск на процеси, тобто якщо на вузлі занадто багато процесів; інакше `False` |
| `NetworkUnavailable` | `True`, якщо мережа для вузла неправильно налаштована, інакше `False` |
{{< /table >}}

{{< note >}}
Якщо ви використовуєте командний рядок для перегляду деталей вузла з вимкненим плануванням (cordoned Node), стан включає `SchedulingDisabled`. `SchedulingDisabled` не є станом в API Kubernetes; замість цього вузли з вимкненим плануванням позначені як Unschedulable в їхній специфікації.
{{< /note >}}

В API Kubernetes стан вузла представлений як частина `.status` ресурсу Node. Наприклад, наступна структура JSON описує справний вузол:

```json
"conditions": [
  {
    "type": "Ready",
    "status": "True",
    "reason": "KubeletReady",
    "message": "kubelet is posting ready status",
    "lastHeartbeatTime": "2019-06-05T18:38:35Z",
    "lastTransitionTime": "2019-06-05T11:41:27Z"
  }
]
```

Коли на вузлах виникають проблеми, панель управління Kubernetes автоматично створює [taints](/uk/docs/concepts/scheduling-eviction/taint-and-toleration/), які відповідають станам, що впливають на вузол. Прикладом цього є ситуація, коли `status` стану Ready залишається `Unknown` або `False` довше, ніж налаштований інтервал NodeMonitorGracePeriod у kube-controller-manager, який стандартно становить 40 секунд. Це спричинить додавання на вузол taint `node.kubernetes.io/unreachable` для статусу `Unknown` або taint `node.kubernetes.io/not-ready` для статусу `False`.

Ці taints впливають на Podʼи, що перебувають в очікуванні, оскільки планувальник враховує taints вузла при призначенні Podʼів на вузол. Наявні Podʼи, заплановані на вузол, можуть бути виселені через застосування taints типу `NoExecute`. Podʼи також можуть мати {{< glossary_tooltip text="tolerations" term_id="toleration" >}}, що дозволяє їм бути запланованими та продовжувати працювати на вузлі, навіть якщо на ньому є певний taint.

Дивіться [Виселення на основі taint](/uk/docs/concepts/scheduling-eviction/taint-and-toleration/#taint-based-evictions) та [Taint вузлів за станами](/uk/docs/concepts/scheduling-eviction/taint-and-toleration/#taint-nodes-by-condition) для отримання додаткової інформації.

## Місткість та Доступність {#capacity}

Описує ресурси, доступні на вузлі: процесор, памʼять та максимальну кількість Podʼів, які можуть бути заплановані на вузлі.

Поля у блоці місткості вказують на загальну кількість ресурсів, які має вузол. Блок доступності вказує на кількість ресурсів на вузлі, які доступні для використання звичайними подами.

Ви можете дізнатися більше про місткість та доступність ресурсів, дізнаючись, як [зарезервувати обчислювальні ресурси](/uk/docs/tasks/administer-cluster/reserve-compute-resources/#node-allocatable) на вузлі.

## Інформація {#info}

Описує загальну інформацію про вузол, таку як версія ядра, версія Kubernetes (kubelet і kube-proxy), деталі контейнерного середовища та яка операційна система використовується на вузлі. Kubelet збирає цю інформацію з вузла та публікує її в API Kubernetes.

## Пульс {#heartbeats}

Пульс, що надсилається вузлами Kubernetes, допомагають вашому кластеру визначити
доступність кожного вузла та вжити заходів у разі виявлення збоїв.

Для вузлів існує дві форми пульсу:

* оновлення `.status` вузла
* обʼєкти [Lease](/uk/docs/concepts/architecture/leases/) у {{< glossary_tooltip term_id="namespace" text="просторі імен">}} `kube-node-lease`. Кожен вузол має повʼязаний обʼєкт Lease.

Порівняно з оновленнями `.status` вузла, Lease є легким ресурсом. Використання Lease для пульсу знижує вплив цих оновлень на продуктивність для великих кластерів.

Kubelet відповідає за створення та оновлення `.status` вузлів, а також за оновлення їх повʼязаних Lease.

* Kubelet оновлює `.status` вузла або коли стан змінюється, або якщо не було оновлень протягом налаштованого інтервалу. Стандартний інтервал для оновлень `.status` вузлів становить 5 хвилин, що значно довше, ніж типових 40 секунд для вузлів, що стали недоступними.
* Kubelet створює та оновлює свій обʼєкт Lease кожні 10 секунд (стандартний інтервал оновлення). Оновлення Lease відбуваються незалежно від оновлень `.status` вузла. Якщо оновлення Lease не вдається, Kubelet повторює спробу, використовуючи експоненціальне збільшення інтервалу з початкового 200 мілісекунд до максимально 7 секунд.