---
reviewers:
- mikedanese
- thockin
title: Середовище контейнера
content_type: concept
weight: 20
---

<!-- overview -->

Ця сторінка описує ресурси, доступні контейнерам в середовищі контейнера.


<!-- body -->

## Середовище контейнера {#container-environment}

Середовище контейнера Kubernetes надає кілька важливих ресурсів контейнерам:

* Файлову систему, яка є комбінацією [образу](/docs/concepts/containers/images/) та одного чи декількох [томів](/docs/concepts/storage/volumes/).
* Інформацію про сам контейнер.
* Інформацію про інші обʼєкти в кластері.

### Інформація про контейнер {#container-information}

*hostname* контейнера є імʼям Pod, в якому він працює. Воно доступне через команду `hostname` або виклик функції [`gethostname`](https://man7.org/linux/man-pages/man2/gethostname.2.html) у бібліотеці libc.

Імʼя та простір імен Pod доступні як змінні середовища через [downward API](/docs/tasks/inject-data-application/downward-api-volume-expose-pod-information/).

Змінні середовища, визначені користувачем у визначенні Pod, також доступні для контейнера, так само як будь-які статично визначені змінні середовища в образі контейнера.

### Інформація про кластер {#cluster-information}

Список всіх служб, які були активні при створенні контейнера, доступний цьому контейнеру як змінні середовища. Цей список обмежений службами в межах того ж простору імен, що й новий Pod контейнера, та службами керування Kubernetes.

Для служби з імʼям *foo*, яка повʼязана з контейнером із імʼям *bar*, визначаються наступні змінні:

```shell
FOO_SERVICE_HOST=<хост, на якому працює служба>
FOO_SERVICE_PORT=<порт, на якому працює служба>
```

Служби мають виділені IP-адреси які доступні для контейнера через DNS, якщо увімкнено [надбудову DNS](https://releases.k8s.io/v{{< skew currentPatchVersion >}}/cluster/addons/dns/).

## {{% heading "whatsnext" %}}

* Дізнайтеся більше про [закріплення обробників за подіями життєвого циклу контейнера](/docs/concepts/containers/container-lifecycle-hooks/).
* Отримайте практичний досвід [прикріплення обробників до подій життєвого циклу контейнера](/docs/tasks/configure-pod-container/attach-handler-lifecycle-event/).