---
content_type: "reference"
title: Версії API Kubelet Device Manager
weight: 50
---

Ця сторінка надає інформацію про сумісність між
[API втулків пристроїв](https://github.com/kubernetes/kubelet/tree/master/pkg/apis/deviceplugin) Kubernetes та різними версіями самого Kubernetes.

## Матриця сумісності {#compatibility-matrix}

|                 |  `v1alpha1` | `v1beta1`   |
|-----------------|-------------|-------------|
| Kubernetes 1.21 |  -          | ✓           |
| Kubernetes 1.22 |  -          | ✓           |
| Kubernetes 1.23 |  -          | ✓           |
| Kubernetes 1.24 |  -          | ✓           |
| Kubernetes 1.25 |  -          | ✓           |
| Kubernetes 1.26 |  -          | ✓           |

Позначення:

* `✓` Точно такі ж функції / обʼєкти API в обох, API втулка пристроїв та версії Kubernetes.
* `+` API втулка пристроїв має функції або обʼєкти API, яких може не бути в кластері Kubernetes, або через те, що API втулка пристроїв додало додаткові нові виклики API, або через те, що сервер видалив старий виклик API. Однак, все, що у них є спільного (більшість інших API), працюватиме. Зверніть увагу, що альфа-версії API можуть зникнути або значно змінитися між незначними релізами.
* `-` Кластер Kubernetes має функції, які не може використовувати API втулка пристроїв, або через те, що сервер додав додаткові виклики API, або через те, що API втулка пристроїв видалило старий виклик API. Однак, все, що у них є спільного (більшість API), працюватиме.