---
title: Налаштування ротації сертифікатів для Kubelet
content_type: task
---

<!-- overview -->
Ця сторінка показує, як увімкнути та налаштувати ротацію сертифікатів для kubelet.

{{< feature-state for_k8s_version="v1.19" state="stable" >}}

## {{% heading "prerequisites" %}}

* Потрібна версія Kubernetes 1.8.0 або пізніша

<!-- steps -->

## Огляд {#overview}

Kubelet використовує сертифікати для автентифікації в Kubernetes API. Типово ці сертифікати створюються з терміном дії один рік, щоб їх не потрібно було оновлювати занадто часто.

Kubernetes містить [ротацію сертифікатів kubelet](/uk/docs/reference/access-authn-authz/kubelet-tls-bootstrapping/), яка автоматично генерує новий ключ і запитує новий сертифікат від Kubernetes API, коли поточний сертифікат наближається до закінчення терміну дії. Коли новий сертифікат стає доступним, він буде використовуватись для автентифікації зʼєднань з Kubernetes API.

## Увімкнення ротації клієнтських сертифікатів {#enabling-client-certificate-rotation}

Процес `kubelet` приймає аргумент `--rotate-certificates`, який контролює, чи буде kubelet автоматично запитувати новий сертифікат, коли наближається термін дії поточного сертифіката.

Процес `kube-controller-manager` приймає аргумент `--cluster-signing-duration` (`--experimental-cluster-signing-duration` до версії 1.19), який контролює, на який термін будуть випускатись сертифікати.

## Розуміння налаштувань ротації сертифікатів

Коли kubelet запускається, якщо він налаштований для початкового завантаження (використовуючи прапорець `--bootstrap-kubeconfig`), він використовуватиме свій початковий сертифікат для підключення до Kubernetes API та надсилатиме запит на підписання сертифіката. Ви можете переглянути статус запитів на підписання сертифікатів за допомогою:

```sh
kubectl get csr
```

Спочатку запит на підписання сертифіката від kubelet на вузлі матиме статус `Pending`. Якщо запит на підписання сертифіката відповідає певним критеріям, він буде автоматично схвалений менеджером контролерів, після чого він матиме статус `Approved`. Далі, менеджер контролерів підпише сертифікат, виданий на термін, вказаний параметром `--cluster-signing-duration`, і підписаний сертифікат буде прикріплений до запиту на підписання сертифіката.

Kubelet отримає підписаний сертифікат від Kubernetes API та запише його на диск у місці, вказаному параметром `--cert-dir`. Потім kubelet використовуватиме новий сертифікат для приєднання до Kubernetes API.

Коли наближається закінчення терміну дії підписаного сертифіката, kubelet автоматично надішле новий запит на підписання сертифіката, використовуючи Kubernetes API. Це може статись у будь-який момент між 30% та 10% залишкового часу дії сертифіката. Знову ж таки, менеджер контролерів автоматично схвалить запит на сертифікат і прикріпить підписаний сертифікат до запиту на підписання сертифіката. Kubelet отримає новий підписаний сертифікат від Kubernetes API та запише його на диск. Потім він оновить зʼєднання з Kubernetes API, щоб приєднатись за допомогою нового сертифіката.
