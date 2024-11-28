---
title: Проксі у Kubernetes
content_type: concept
weight: 100
---

<!-- overview -->

На цій сторінці пояснюються проксі, що використовуються з Kubernetes.

<!-- body -->

## Проксі {#proxies}

У вас можуть зустрітися декілька різних проксі, коли ви використовуєте Kubernetes:

1. [Проксі kubectl](/uk/docs/tasks/access-application-cluster/access-cluster/#directly-accessing-the-rest-api):

    - працює на робочому столі користувача або в контейнері
    - забезпечує проксі з локальної адреси до apiserver Kubernetes
    - клієнт до проксі використовує HTTP
    - проксі до apiserver використовує HTTPS
    - знаходить apiserver
    - додає заголовки автентифікації

1. [Проксі apiserver](/uk/docs/tasks/access-application-cluster/access-cluster-services/#discovering-builtin-services):

    - є бастіоном, вбудованим в apiserver
    - зʼєднує користувача поза кластером з IP-адресами кластера, які інакше можуть бути недоступними
    - працює в процесах apiserver
    - клієнт до проксі використовує HTTPS (або http, якщо apiserver налаштовано так)
    - проксі до цілі може використовувати HTTP або HTTPS, як вибрав проксі за наявною інформацією
    - може бути використаний для доступу до Node, Pod або Service
    - виконує балансування навантаження при використанні для доступу до Service

1. [kube proxy](/uk/docs/concepts/services-networking/service/#ips-and-vips):

    - працює на кожному вузлі
    - забезпечує проксі UDP, TCP та SCTP
    - не розуміє HTTP
    - надає балансування навантаження
    - використовується лише для доступу до Service

1. Проксі/балансувальник перед apiserver(s):

    - існування та реалізація різниться від кластера до кластера (наприклад, nginx)
    - розташований між всіма клієнтами та одним або кількома apiservers
    - діє як балансувальник навантаження, якщо є кілька apiservers.

1. Хмарні балансувальники навантаження на зовнішньому Service:

    - надаються деякими хмарними провайдерами (наприклад, AWS ELB, Google Cloud Load Balancer)
    - створюються автоматично, коли у Service Kubernetes тип — `LoadBalancer`
    - зазвичай підтримують лише UDP/TCP
    - підтримка SCTP залежить від реалізації балансувальника навантаження хмарного провайдера
    - реалізація відрізняється від провайдера хмарних послуг.

Зазвичай користувачі Kubernetes не повинні турбуватися про щось, крім перших двох типів. Зазвичай адміністратор кластера забезпечує правильне налаштування останніх типів.

## Запит на перенаправлення {#requesting-redirects}

Проксі замінили можливості перенаправлення. Перенаправлення були визнані застарілими.