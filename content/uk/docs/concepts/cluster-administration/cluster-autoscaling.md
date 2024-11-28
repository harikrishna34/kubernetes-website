---
title: Автомасштабування кластера
linkTitle: Автомасштабування кластера
description: >-
  Автоматичне керування вузлами кластера для адаптації до попиту.
content_type: concept
weight: 120
---

<!-- overview -->

Kubernetes потрібні {{< glossary_tooltip text="вузли" term_id="node" >}} у вашому кластері для роботи {{< glossary_tooltip text="Podʼів" term_id="pod" >}}. Це означає, що потрібно забезпечити місце для робочих Podʼів та для самого Kubernetes.

Ви можете автоматично налаштувати кількість ресурсів, доступних у вашому кластері: _автомасштабування вузлів_. Ви можете змінювати кількість вузлів або змінювати потужність, яку надають вузли. Перший підхід називається _горизонтальним масштабуванням_, а другий — _вертикальним масштабуванням_.

Kubernetes може навіть забезпечити багатовимірне автоматичне масштабування для вузлів.

<!-- body -->

## Керування вузлами вручну {#manual-node-management}

Ви можете вручну керувати потужністю на рівні вузла, де ви налаштовуєте фіксовану кількість вузлів; ви можете використовувати цей підхід навіть якщо забезпечення (процес встановлення, управління та виведення з експлуатації) для цих вузлів автоматизоване.

Ця сторінка присвячена наступному кроку, а саме автоматизації управління обсягом потужності вузла (ЦП, памʼяті та інших ресурсів вузла), доступним у вашому кластері.

## Автоматичне горизонтальне масштабування {#autoscaling-horizontal}

### Автомасштабувальник {#cluster-autoscaler}

Ви можете використовувати [Автомасштабувальник](https://github.com/kubernetes/autoscaler/tree/master/cluster-autoscaler), щоб автоматично керувати масштабуванням ваших вузлів. Автомасштабувальник може інтегруватися з хмарним постачальником або з [кластерним API](https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/cloudprovider/clusterapi/README.md) Kubernetes, щоб забезпечити фактичне управління вузлами, яке потрібно.

Автомасштабувальник додає вузли, коли неможливо розмістити потоки, і видаляє вузли, коли ці вузли порожні.

#### Інтеграції з хмарними постачальниками {#cluster-autoscaler-providers}

[README](https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/README.md) для кластерного масштабувальника містить список деяких доступних інтеграцій з хмарними постачальниками.

## Багатовимірне масштабування з урахуванням вартості {#autoscaling-multi-dimension}

### Karpenter {#autoscaler-karpenter}

[Karpenter](https://karpenter.sh/) підтримує пряме керування вузлами через втулки, які інтегруються з конкретними хмарними постачальниками та можуть керувати вузлами для вас, оптимізуючи загальну вартість.

> Karpenter автоматично запускає саме ті обчислювальні ресурси, які потрібні вашим застосункам. Його спроєктовано, щоб ви могли повною мірою скористатись можливостями хмари з швидким та простим розгортанням обчислювальних ресурсів для вашого кластера Kubernetes.

Інструмент Karpenter призначений для інтеграції з хмарним постачальником, який надає управління серверами через API, і де інформація про ціни на доступні сервери також доступна через веб-API.

Наприклад, якщо ви маєте декілька Podʼів у вашому кластері, інструмент Karpenter може купити новий вузол, який більший за один з вузлів, які ви вже використовуєте, а потім вимкнути наявний вузол, як тільки новий вузол буде готовий до використання.

#### Інтеграції з постачальниками хмарних послуг {#karpenter-providers}

{{% thirdparty-content vendor="true" %}}

Існують інтеграції між ядром Karpenter та наступними постачальниками хмарних послуг:

- [Amazon Web Services](https://github.com/aws/karpenter-provider-aws)
- [Azure](https://github.com/Azure/karpenter-provider-azure)

## Повʼязані компоненти {#related-components}

### Descheduler

[Descheduler](https://github.com/kubernetes-sigs/descheduler) може допомогти консолідувати Podʼи на меншій кількості вузлів, щоб впоратись з автоматичним масштабуванням, коли у кластера зʼявляються вільні потужності.

### Визначення розміру навантаження на основі розміру кластера {#sizing-a-workload-based-on-cluster-size}

#### Пропорційне автомасштабування кластера {#cluster-proportional-autoscaler}

Для навантажень, які потрібно масштабувати залежно від розміру кластера, таких як `cluster-dns` або інші системні компоненти, ви можете використовувати [_Cluster Proportional Autoscaler_](https://github.com/kubernetes-sigs/cluster-proportional-autoscaler).

Cluster Proportional Autoscaler спостерігає за кількістю придатних до планування вузлів та ядер, і масштабує кількість реплік цільового навантаження відповідно.

#### Вертикальний пропорційний автомасштабувальник кластера {#cluster-proportional-vertical-autoscaler}

Якщо кількість реплік має залишитися незмінною, ви можете масштабувати ваші робочі навантаження вертикально відповідно до розміру кластера, використовуючи [_Cluster Proportional Vertical Autoscaler_](https://github.com/kubernetes-sigs/cluster-proportional-vertical-autoscaler). Цей проєкт перебуває в **бета**-версії та знаходиться на GitHub.

У той час, як Cluster Proportional Autoscaler масштабує кількість реплік робочого навантаження, Cluster Proportional Vertical Autoscaler налаштовує запити ресурсів для робочого навантаження (наприклад, Deployment або DaemonSet) на основі кількості вузлів та/або ядер у кластері.

## {{% heading "whatsnext" %}}

- Дізнайтеся більше про [автомасштабування на рівні робочого навантаження](/docs/concepts/workloads/autoscaling/)
- Дізнайтеся більше про [перевищення ємності вузла для кластера](/docs/tasks/administer-cluster/node-overprovisioning/)