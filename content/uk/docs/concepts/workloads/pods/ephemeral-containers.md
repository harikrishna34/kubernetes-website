---
title: Ефемерні контейнери
content_type: concept
weight: 60
---

<!-- overview -->

{{< feature-state state="stable" for_k8s_version="v1.25" >}}

Ця сторінка надає огляд ефемерних контейнерів: особливого типу контейнера, який працює тимчасово в наявному {{< glossary_tooltip term_id="pod" >}} для виконання дій, ініційованих користувачем, таких як усунення несправностей. Ви можете використовувати ефемерні контейнери для інспектування служб, а не для створення застосунків.

<!-- body -->

## Розуміння ефемерних контейнерів {#understanding-ephemeral-containers}

{{< glossary_tooltip text="Podʼи" term_id="pod" >}} є фундаментальним елементом застосунків Kubernetes. Оскільки Podʼи призначені бути одноразовими та замінними, ви не можете додавати контейнер до Podʼа, якщо він вже був створений. Замість цього ви зазвичай видаляєте та замінюєте Podʼи у контрольований спосіб, використовуючи {{< glossary_tooltip text="Deployment" term_id="deployment" >}}.

Іноді, однак, необхідно оглянути стан наявного Podʼа, наприклад, для усунення несправностей, коли важко відтворити помилку. У цих випадках ви можете запустити ефемерний контейнер в Podʼі, щоб оглянути його стан та виконати певні довільні команди.

### Що таке ефемерний контейнер? {#what-is-an-ephemeral-container}

Ефемерні контейнери відрізняються від інших контейнерів тим, що вони не мають гарантій щодо ресурсів або виконання, і їх ніколи автоматично не перезапускають, тому вони не підходять для створення Застосунків. Ефемерні контейнери описуються за допомогою того ж `ContainerSpec`, що й звичайні контейнери, але багато полів
несумісні та заборонені для ефемерних контейнерів.

- У ефемерних контейнерів не може бути портів, тому такі поля, як `ports`, `livenessProbe`, `readinessProbe`, заборонені.
- Виділення ресурсів для Podʼа незмінне, тому встановлення `resources` заборонене.
- Для повного списку дозволених полів дивіться [документацію по ефемерним контейнерам (EphemeralContainer)](/docs/reference/generated/kubernetes-api/{{< param "version" >}}/#ephemeralcontainer-v1-core).

Ефемерні контейнери створюються за допомогою спеціального обробника `ephemeralcontainers` в API замість того, щоб додавати їх безпосередньо до `pod.spec`, тому не можна додавати ефемерний контейнер за допомогою `kubectl edit`.

{{< note >}}
Ефемерні контейнери не підтримуються [статичними Podʼами](/uk/docs/tasks/configure-pod-container/static-pod/).
{{< /note >}}

## Використання ефемерних контейнерів {#uses-for-ephemeral-containers}

Ефемерні контейнери корисні для інтерактивного усунення несправностей, коли `kubectl exec` недостатній, оскільки контейнер впав або образ контейнера не містить засобів налагодження.

Зокрема [образи distroless](https://github.com/GoogleContainerTools/distroless) дозволяють вам розгортати мінімальні образи контейнерів, які зменшують площу атаки та вразливість. Оскільки образи distroless не включають оболонку або будь-які засоби налагодження, складно налагоджувати образи distroless, використовуючи лише `kubectl exec`.

При використанні ефемерних контейнерів корисно включити [спільний простір імен процесу (process namespace sharing)](/uk/docs/tasks/configure-pod-container/share-process-namespace/), щоб ви могли переглядати процеси в інших контейнерах.

## {{% heading "whatsnext" %}}

- Дізнайтеся, як [налагоджувати Podʼи за допомогою ефемерних контейнерів](/uk/docs/tasks/debug/debug-application/debug-running-pod/#ephemeral-container).