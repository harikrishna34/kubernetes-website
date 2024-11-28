---
title: Оновлення кластера
content_type: task
weight: 350
---

<!-- overview -->

Ця сторінка надає огляд кроків, які вам слід виконати для оновлення кластера Kubernetes.

Проєкт Kubernetes рекомендує оперативно оновлюватись до останніх випусків патчів, а також переконатися, що ви використовуєте підтримуваний мінорний випуск Kubernetes. Дотримання цих рекомендацій допоможе вам залишатися в безпеці.

Спосіб оновлення кластера залежить від того, як ви спочатку розгорнули його та від будь-яких наступних змін.

На високому рівні кроки, які ви виконуєте, такі:

- Оновити {{< glossary_tooltip text="панель управління" term_id="control-plane" >}}
- Оновити вузли в вашому кластері
- Оновити клієнтів, такі як {{< glossary_tooltip text="kubectl" term_id="kubectl" >}}
- Відредагувати маніфести та інші ресурси на основі змін API, які супроводжують нову версію Kubernetes

## {{% heading "prerequisites" %}}

Вам потрібно мати кластер. Ця сторінка присвячена оновленню з Kubernetes
{{< skew currentVersionAddMinor -1 >}} до Kubernetes {{< skew currentVersion >}}. Якщо ваш кластер зараз працює на Kubernetes {{< skew currentVersionAddMinor -1 >}}, тоді, будь ласка, перевірте документацію для версії Kubernetes, на яку ви плануєте оновити.

## Підходи до оновлення {#upgrade-approaches}

### kubeadm {#upgrade-kubeadm}

Якщо ваш кластер був розгорнутий за допомогою інструменту `kubeadm`, дивіться [Оновлення кластерів kubeadm](/uk/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/) для докладної інформації щодо оновлення кластера.

Після того, як ви оновили кластер, не забудьте [встановити останню версію `kubectl`](/uk/docs/tasks/tools/).

### Ручне розгортання {#manual-deployments}

{{< caution >}}
Ці кроки не враховують розширень сторонніх сторін, таких як мережеві втулки та втулки сховищ.
{{< /caution >}}

Вам слід вручну оновити панель управління наступним чином:

- etcd (всі екземпляри)
- kube-apiserver (всі хости панелі управління)
- kube-controller-manager
- kube-scheduler
- контролер управління хмари, якщо ви використовуєте його

На цьому етапі вам слід [встановити останню версію `kubectl`](/uk/docs/tasks/tools/).

Для кожного вузла в вашому кластері, [очистіть](/uk/docs/tasks/administer-cluster/safely-drain-node/) цей вузол, а потім або замініть його новим вузлом, який використовує {{< skew currentVersion >}} kubelet, або оновіть kubelet на цьому вузлі та відновіть його Service.

{{< caution >}}
Jxbotyyz вузлів перед оновленням kubelet забезпечує повторний вхід Podʼів та перезапуск контейнерів, що може бути необхідно для розвʼязання деяких проблем безпеки або інших важливих помилок.
{{</ caution >}}

### Інші розгортання {#upgrade-other}

Дивіться документацію для вашого інструменту розгортання кластера, щоб дізнатися рекомендовані кроки для підтримки.

## Завдання після оновлення {#post-upgrade-tasks}

### Перемикання версії API зберігання кластера {#switch-your-cluster-s-storage-api-version}

Обʼєкти, які серіалізуються в etcd для внутрішнього представлення кластера ресурсів Kubernetes, записуються за допомогою певної версії API.

Коли підтримуване API змінюється, ці обʼєкти можуть потребувати перезаписування в новому API. Невиконання цього призведе до того, що ресурси не можна буде декодувати або використовувати за допомогою сервера API Kubernetes.

Для кожного ураженого обʼєкта, отримайте його, використовуючи останню підтримувану версію API, а потім записуйте його також, використовуючи останню підтримувану версію API.

### Оновлення маніфестів {#update-manifests}

Оновлення до нової версії Kubernetes може надати нові API.

Ви можете використовувати команду `kubectl convert` для конвертації маніфестів між різними версіями API. Наприклад:

```shell
kubectl convert -f pod.yaml --output-version v1
```

Інструмент `kubectl` замінює вміст `pod.yaml` на маніфест, який встановлює `kind` на Pod (незмінно), але з оновленим `apiVersion`.

### Втулки пристроїв {#device-plugins}

Якщо ваш кластер використовує втулки пристроїв і вузол потребує оновлення до випуску Kubernetes з новішою версією API втулка пристроїв, втулки пристроїв повинні бути оновлені для підтримки обох версій перед оновленням вузла, щоб гарантувати, що виділення пристроїв продовжує успішно завершуватися під час оновлення.

Дивіться [Сумісність API](/uk/docs/concepts/extend-kubernetes/compute-storage-net/device-plugins/#api-compatibility) та [Версії API керуючого пристрою Kubelet](/uk/docs/reference/node/device-plugin-api-versions/) для отримання додаткової інформації.