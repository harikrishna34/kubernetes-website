---
title: Посібник зі стилю документації
linktitle:  Посібник зі стилю
content_type: concept
weight: 40
---

<!-- overview -->

Ця сторінка надає вказівки щодо стилю написання документації Kubernetes. Це вказівки, а не правила. Використовуйте здоровий глузд та не соромтеся пропонувати зміни до цього документа за допомогою pull request.

Для отримання додаткової інформації про створення нового вмісту для документації Kubernetes, прочитайте [Посібник з вмісту документації](/uk/docs/contribute/style/content-guide/).

Зміни до посібника зі стилю вносяться групою SIG Docs. Щоб запропонувати зміну або доповнення, [додайте її до порядку денного](https://bit.ly/sig-docs-agenda) на наступну зустріч SIG Docs та відвідайте зустріч, щоб взяти участь в обговоренні.

<!-- body -->

{{< note >}}
Документація Kubernetes використовує [Goldmark Markdown Renderer](https://github.com/yuin/goldmark) з деякими налаштуваннями разом із кількома [Hugo Shortcodes](/uk/docs/contribute/style/hugo-shortcodes/), щоб підтримувати записи глосарія, вкладки та представлення стану функцій.
{{< /note >}}

## Мова {#language}

Документація Kubernetes була перекладена кількома мовами (див. [локалізовані файли README](https://github.com/kubernetes/website/blob/main/README.md#localization-readmemds)).

Процес локалізації документації для інших мови описано в розділі[Локалізація документації Kubernetes](/uk/docs/contribute/localization/).

Документація англійською мовою використовує правопис та граматику американської англійської.

{{< comment >}}[Якщо ви локалізуєте цю сторінку, можете пропустити пункт про американську англійську.]{{< /comment >}}

## Стандарти форматування документації {#documentation-formatting-standards}

### Використовуйте UpperCamelCase для обʼєктів API {#use-upper-camel-case-for-api-objects}

Коли ви посилаєтеся на взаємодію з обʼєктом API, використовуйте [UpperCamelCase](https://uk.wikipedia.org/wiki/CamelCase), також відомий як Pascal case. Ви можете зустріти інші варіанти написання, наприклад, "configMap", в [Довіднику API](/uk/docs/reference/kubernetes-api/). У загальній документації краще використовувати UpperCamelCase, називаючи обʼєкт "ConfigMap".

Коли ви загалом обговорюєте обʼєкт API, використовуйте [велику літеру тільки на початку речення](https://docs.microsoft.com/en-us/style-guide/text-formatting/using-type/use-sentence-style-capitalization).

Наведені нижче приклади зосереджуються на капіталізації. Для отримання додаткової інформації про форматування імен обʼєктів API перегляньте відповідні рекомендації щодо [Стилю коду](#code-style-inline-code).

{{< table caption = "Як робити та не робити — Використовуйте Pascal case для обʼєктів API" >}}
Рекомендовано | Небажано
:--| :-----
Ресурс HorizontalPodAutoscaler відповідає за ... | Horizontal pod autoscaler відповідає за ...
Обʼєкт PodList є списком Podʼів. | Обʼєкт Pod List є списком Podʼів.
Обʼєкт Volume містить поле `hostPath`. | Обʼєкт volume містить поле hostPath.
Кожен обʼєкт ConfigMap є частиною простору імен. | Кожен обʼєкт configMap є частиною простору імен.
Для управління конфіденційними даними розгляньте можливість використання API Secret. | Для управління конфіденційними даними розгляньте можливість використання secret API.
{{< /table >}}

### Використовуйте кутові дужки для заповнювачів {#use-angle-brackets-for-placeholders}

Використовуйте кутові дужки для заповнювачів. Поясніть читачеві, що представляє заповнювач, наприклад:

Показ інформацію про Pod:

```shell
kubectl describe pod <pod-name> -n <namespace>
```

Якщо простір імен Podʼа є `default`, ви можете пропустити параметр `-n`.

### Використовуйте жирний шрифт для елементів інтерфейсу користувача {#use-bold-for-ui-elements}

{{< table caption = "Як робити та не робити — Жирний шрифт для елементів інтерфейсу" >}}
Рекомендовано | Небажано
:--| :-----
Натисніть **Fork**. | Натисніть "Fork".
Виберіть **Other**. | Виберіть "Other".
{{< /table >}}

### Використовуйте курсив для визначення або введення нових термінів {#use-italics-to-define-or-introduce-new-terms}

{{< table caption = "Як робити та не робити — Використання курсиву для нових термінів" >}}
Рекомендовано | Небажано
:--| :-----
_Кластер_ — це набір вузлів ... | "Кластер" — це набір вузлів ...
Ці компоненти утворюють _панель управління_. | Ці компоненти утворюють **панель управління**.
{{< /table >}}

### Використовуйте стиль коду для імен файлів, тек та шляхів {#use-code-style-for-file-names-dirs-and-paths}

{{< table caption = "Як робити та не робити — Використовуйте кодовий стиль для імен файлів, тек та шляхів" >}}
Рекомендовано | Небажано
:--| :-----
Відкрийте файл `envars.yaml`. | Відкрийте файл envars.yaml.
Перейдіть до теки `/docs/tutorials`. | Перейдіть до теки /docs/tutorials.
Відкрийте файл `/_data/concepts.yaml`. | Відкрийте файл /\_data/concepts.yaml.
{{< /table >}}

### Використовуйте міжнародний стандарт для пунктуації всередині лапок {#use-international-standard-for-punctuation-inside-quotes}

{{< table caption = "Як робити та не робити — Використовуйте міжнародний стандарт для пунктуації всередині лапок" >}}
Рекомендовано | Небажано
:--| :-----
Події записуються з відповідною "стадією". | Події записуються з відповідною "стадією."
Копія називається "fork". | Копія називається "fork."
{{< /table >}}

## Форматування вбудованого коду {#inline-code-formatting}

### Використовуйте кодовий стиль для вбудованого коду та команд {#code-style-inline-code}

Для вбудованого в документі HTML коду використовуйте теґ `<code>`. У документі Markdown використовуйте зворотну лапку (`` ` ``). Проте, API обʼєкти, такі як StatefulSet або ConfigMap, пишуться дослівно (без зворотних лапок); це дозволяє використовувати апострофи для позначення присвійного відмінка.

{{< table caption = "Як робити та не робити — Використовуйте стиль code для вбудованого коду, команд та API обʼєктів" >}}
Рекомендовано | Небажано
:--| :-----
Команда `kubectl run` створює Pod. | Команда "kubectl run" створює Pod.
Kubelet на кожному вузлі отримує Lease... | Kubelet на кожному вузлі отримує `Lease`...
PersistentVolume представляє довговічне сховище... | `PersistentVolume` представляє довговічне сховище...
Поле `.spec.group` у CustomResourceDefinition... | Поле `CustomResourceDefinition.spec.group` у CustomResourceDefinition...
Для декларативного управління використовуйте `kubectl apply`. | Для декларативного управління використовуйте "kubectl apply".
Огортайте приклади коду потрійними зворотними лапками. (\`\`\`) | Огортайте приклади коду будь-яким іншим синтаксисом.
Використовуйте одинарні зворотні лапки для вбудованого коду. Наприклад, `var example = true`. | Використовуйте дві зірочки (`**`) або підкреслення (`_`) для вбудованого коду. Наприклад, **var example = true**.
Використовуйте потрійні зворотні лапки перед і після багаторядкового блоку коду для виділених блоків коду. | Використовуйте багаторядкові блоки коду для створення діаграм, блок-схем або інших ілюстрацій.
Використовуйте значущі імена змінних, які мають контекст. | Використовуйте імена змінних, такі як 'foo', 'bar', і 'baz', які не є значущими та не мають контексту.
Видаляйте пробіли в кінці рядків коду. | Додавайте пробіли в кінці рядків коду, коли вони важливі, оскільки інструмент читання тексту з екрана також озвучує пробіли.
{{< /table >}}

{{< note >}}
Вебсайт підтримує підсвічування синтаксису для прикладів коду, але вказівка на мову програмування є необовʼязковою. Підсвічування синтаксису в блоці коду повинно відповідати [рекомендаціям щодо контрастності](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0&showtechniques=141%2C143#contrast-minimum).
{{< /note >}}

### Використовуйте стиль коду для імен полів обʼєктів та просторів імен {#use-code-style-for-object-field-names-and-namespaces}

{{< table caption = "Як робити та не робити — Використовуйте кодовий стиль для імен полів обʼєктів" >}}
Рекомендовано | Небажано
:--| :-----
Встановіть значення поля `replicas` у конфігураційному файлі. | Встановіть значення поля "replicas" у конфігураційному файлі.
Значення поля `exec` є обʼєктом ExecAction. | Значення поля "exec" є обʼєктом ExecAction.
Запустіть процес як DaemonSet у просторі імен `kube-system`. | Запустіть процес як DaemonSet у просторі імен kube-system.
{{< /table >}}

### Використовуйте стиль коду для назв команд, інструментів та компонентів Kubernetes {#use-code-style-for-kubernetes-command-tool-and-component-names}

{{< table caption = "Як робити та не робити — Використовуйте кодовий стиль для назв командних інструментів та компонентів Kubernetes" >}}
Рекомендовано | Небажано
:--| :-----
`kubelet` підтримує стабільність вузла. | Kubelet підтримує стабільність вузла.
`kubectl` відповідає за знаходження та автентифікацію на API сервері. | Kubectl відповідає за знаходження та автентифікацію на apiserver.
Запустіть процес із сертифікатом, `kube-apiserver --client-ca-file=FILENAME`. | Запустіть процес із сертифікатом, kube-apiserver --client-ca-file=FILENAME.
{{< /table >}}

### Початок речення з назви інструменту або компонента {#starting-a-sentence-with-a-component-tool-or-component-name}

{{< table caption = "Як робити та не робити — Початок речення з назви інструменту або компонента" >}}
Рекомендовано | Небажано
:--| :-----
The `kubeadm` tool bootstraps and provisions machines in a cluster. | `kubeadm` tool bootstraps and provisions machines in a cluster.
The kube-scheduler is the default scheduler for Kubernetes. | kube-scheduler is the default scheduler for Kubernetes.
{{< /table >}}

### Використовуйте загальний дескриптор замість назви компонента {#use-a-general-descriptor-over-a-component-name}

{{< table caption = "Як робити та не робити — Використовуйте загальний дескриптор замість назви компонента" >}}
Рекомендовано | Небажано
:--| :-----
API сервер Kubernetes пропонує специфікацію OpenAPI. | Apiserver пропонує специфікацію OpenAPI.
Агреговані API є підпорядкованими API серверами. | Агреговані API є підпорядкованими APIServers.
{{< /table >}}

### Використовуйте звичайний стиль для значень полів типу string та integer {#use-normal-style-for-string-and-integer-field-values}

Для значень полів типу string або integer використовуйте звичайний стиль без лапок.

{{< table caption = "Як робити та не робити — Використовуйте нормальний стиль для значень полів типу string та integer" >}}
Рекомендовано | Небажано
:--| :-----
Встановіть значення `imagePullPolicy` на Always. | Встановіть значення `imagePullPolicy` на "Always".
Встановіть значення `image` на nginx:1.16. | Встановіть значення `image` на `nginx:1.16`.
Встановіть значення поля `replicas` на 2. | Встановіть значення поля `replicas` на `2`.
{{< /table >}}

Однак, розгляньте можливість цитування значень у випадках, коли є ризик, що читачі можуть сплутати значення з типом API.

## Посилання на API ресурси Kubernetes {#referring-to-kubernetes-api-resources}

Цей розділ описує, як ми посилаємося на API ресурси в документації.

### Уточнення щодо терміна "ресурс" {#clarification-about-resource}

Kubernetes використовує слово _ресурс_ для позначення ресурсів API. Наприклад, шлях URL `/apis/apps/v1/namespaces/default/deployments/my-app` представляє Deployment з назвою "my-app" у {{< glossary_tooltip text="просторі імен" term_id="namespace" >}} "default". У термінології HTTP, {{< glossary_tooltip text="простір імен" term_id="namespace" >}} є ресурсом — так само як всі веб-URL ідентифікують ресурс.

Документація Kubernetes також використовує "ресурс" для опису запитів і обмежень на використання процесорів і памʼяті. Дуже часто доцільно посилатися на API ресурси як на "API ресурси", щоб уникнути плутанини з процесорними ресурсами та ресурсами памʼяті або з іншими видами ресурсів.

Якщо ви використовуєте назву ресурсу в нижньому регістрі у множині, наприклад, `deployments` або `configmaps`, надайте додатковий контекст, щоб допомогти читачам зрозуміти, що ви маєте на увазі. Якщо ви використовуєте цей термін у контексті, де також можна використовувати назву в UpperCamelCase, і є ризик неоднозначності, розгляньте можливість використання типу API в UpperCamelCase.

### Коли використовувати терміни Kubernetes API {#when-to-use-kubernetes-api-terminologies}

Різні терміни Kubernetes API включають:

- _API типи (kind)_: назви, які використовуються в URL API (такі як `pods`, `namespaces`). API типи іноді також називають _типами ресурсів_.
- _API ресурс_: одиничні екземпляри API типу (такі як `pod`, `secret`).
- _Обʼєкт_: ресурс, який служить як "запис наміру". Обʼєкт є бажаним станом для конкретної частини вашого кластера, який намагається підтримувати панель управління Kubernetes. Всі обʼєкти в API Kubernetes також є ресурсами.

Для ясності ви можете додати "ресурс" або "обʼєкт", коли посилаєтесь на API ресурс у документації Kubernetes. Наприклад: пишіть "обʼєкт Secret", замість "Secret". Якщо з контексту зрозуміло, що мова йде про ресурс, можна не додавати це слово.

Розгляньте можливість перефразування, коли це допомагає уникнути непорозумінь. Звичайною ситуацією є випадок, коли ви хочете почати речення з API типу, наприклад, "Secret"; оскільки в англійській та інших мовах заголовні літери використовуються на початку речень, читачі не можуть визначити, чи маєте ви на увазі API тип або загальне поняття. Перефразування може допомогти.

### Назви API ресурсів {#api-resource-names}

Завжди форматуйте назви API ресурсів, використовуючи [UpperCamelCase](https://uk.wikipedia.org/wiki/Camel_case), також відомий як PascalCase. Не пишіть API типи з використанням форматування коду.

Не розбивайте назву API обʼєкта на окремі слова. Наприклад, використовуйте PodTemplateList, а не Pod Template List.

Для отримання додаткової інформації про PascalCase і форматування коду, ознайомтесь із відповідними рекомендаціями щодо [Використання UpperCamelCase для API обʼєктів](/uk/docs/contribute/style/style-guide/#use-upper-camel-case-for-api-objects)
та [Використання кодового стилю для вбудованого коду, команд і API обʼєктів](#code-style-inline-code).

Для отримання додаткової інформації про термінологію Kubernetes API, ознайомтесь із відповідними рекомендаціями щодо [Термінології API Kubernetes](/uk/docs/reference/using-api/api-concepts/#standard-api-terminology).

## Форматування фрагментів коду {#code-snippet-formatting}

### Не включайте символ командного рядка {#don-t-include-the-command-prompt}

{{< table caption = "Як робити та не робити — Не включайте командний рядок" >}}
Рекомендовано | Небажано
:--| :-----
`kubectl get pods` | `$ kubectl get pods`
{{< /table >}}

### Відокремлюйте команди від їх виводу {#separate-commands-from-output}

Переконайтеся, що Pod працює на обраному вами вузлі:

```shell
kubectl get pods --output=wide
```

Результат буде схожим на цей:

```console
NAME     READY     STATUS    RESTARTS   AGE    IP           NODE
nginx    1/1       Running   0          13s    10.200.0.4   worker0
```

### Версіювання прикладів для Kubernetes {#versioning-kubernetes-examples}

Приклади коду та конфігурацій, які включають інформацію про версії, повинні бути узгоджені з текстом.

Якщо інформація є специфічною для версії, версія Kubernetes повинна бути визначена у розділі `prerequisites` [шаблону Task](/uk/docs/contribute/style/page-content-types/#task) або шаблону [Tutorial](/uk/docs/contribute/style/page-content-types/#tutorial). Після збереження сторінки, розділ `prerequisites` буде показаний з назвою — **Перед тим, як почати**.

Щоб вказати версію Kubernetes для сторінки з завданням або навчальним посібником, включіть `min-kubernetes-server-version` у front matter сторінки.

Якщо YAML приклад знаходиться у файлі окремо, знайдіть та перегляньте теми, які включають його як посилання. Переконайтеся, що будь-які теми, які використовують окремий YAML, мають відповідну інформацію про версії. Якщо окремий YAML файл не посилається на жодні теми, розгляньте можливість його видалення замість оновлення.

Наприклад, якщо ви пишете навчальний посібник, що стосується версії Kubernetes 1.8, front matter вашого markdown файлу мають виглядати приблизно так:

```yaml
---
title: <ваша назва навчального посібника>
min-kubernetes-server-version: v1.8
---
```

У прикладах коду та конфігурацій не включайте коментарі про альтернативні версії. Будьте обережні, щоб не включати некоректні твердження у ваші приклади у вигляді коментарів, наприклад:

```yaml
apiVersion: v1 # попередні версії використовують...
kind: Pod
...
```

## Словник Kubernetes.io

Список специфічних для Kubernetes термінів і слів, які слід використовувати послідовно у всьому сайті.

{{< table caption = "Словник Kubernetes.io" >}}
Термін | Використання
:--- | :----
Kubernetes | Kubernetes завжди має писатися з великої літери.
Docker | Docker завжди має писатися з великої літери.
SIG Docs | SIG Docs, а не SIG-DOCS чи інші варіанти.
On-premises | On-premises або On-prem, а не On-premise чи інші варіанти.
cloud native | Cloud native або cloud native, залежно від структури речення, а не cloud-native чи Cloud Native.
open source | Open source або open source, залежно від структури речення, а не open-source чи Open Source.
{{< /table >}}

## Shortcodes {#shortcodes}

Hugo [Shortcodes](https://gohugo.io/content-management/shortcodes) допомагають створювати різні рівні риторичної привабливості. Наша документація підтримує три різні Shortcodes в цій категорії: **Note** `{{</* note */>}}`, **Caution** `{{</* caution */>}}` і **Warning** `{{</* warning */>}}`.

1. Оточуйте текст відкриваючим та закриваючим Shortcodeʼом.

2. Використовуйте наступний синтаксис для застосування стилю:

   ```none
   {{</* note */>}}
   Немає необхідності включати префікс; Shortcode автоматично додає його. (Note:, Caution:, тощо)
   {{</* /note */>}}
   ```

   Вихідний результат:

   {{< note >}}
   Обраний префікс збігається з текстом теґа.
   {{< /note >}}

### Note {#note}

Використовуйте `{{</* note */>}}` для виділення поради або корисної інформації.

Наприклад:

```hugo
{{</* note */>}}
Ви _все ще_ можете використовувати Markdown всередині цих Shortcodeʼів.
{{</* /note */>}}
```

Вихідний результат:

{{< note >}}
Ви _все ще_ можете використовувати Markdown всередині цих Shortcodeʼів.
{{< /note >}}

Ви можете використовувати `{{</* note */>}}` у списку:

```md
1. Використовуйте Shortcode примітки у списку

1. Другий пункт з вбудованою приміткою

   {{</* note */>}}
   Shortcode Warning, Caution і Note, вбудовані у списки, повинні мати відповідний відступ (на рівні початку тексту списку). Див. [Поширені проблеми з Shortcode](#common-shortcode-issues).
   {{</* /note */>}}

1. Третій пункт у списку

1. Четвертий пункт у списку
```

Вихідний результат:

1. Використовуйте Shortcode примітки у списку

1. Другий пункт з вбудованою приміткою

   {{< note >}}
   Шорткоди Warning, Caution і Note, вбудовані у списки, повинні мати відповідний відступ (на рівні початку тексту списку). Див. [Поширені проблеми з Shortcode](#common-shortcode-issues).
   {{< /note >}}

1. Третій пункт у списку

1. Четвертий пункт у списку

### Caution {#caution}

Використовуйте `{{</* caution */>}}` для привернення уваги до важливої інформації, щоб уникнути помилок.

Наприклад:

```hugo
{{</* caution */>}}
Стиль виклику застосовується лише до рядка теґа вище безпосередньо.
{{</* /caution */>}}
```

Вихідний результат:

{{< caution >}}
Стиль виклику застосовується лише до рядка теґа вище безпосередньо.
{{< /caution >}}

### Warning {#warning}

Використовуйте `{{</* warning */>}}` для вказівки на небезпеку або важливу інформацію, яку потрібно обовʼязково враховувати.

Наприклад:

```hugo
{{</* warning */>}}
Будьте обережні.
{{</* /warning */>}}
```

Вихідний результат:

{{< warning >}}
Будьте обережні.
{{< /warning >}}

## Поширені проблеми з Shortcode {#common-shortcode-issues}

### Нумеровані списки

Shortcode переривають нумеровані списки, якщо не зробити відступ у на рівні початку тексту списку перед сповіщенням та теґом.

Наприклад:

    1. Розігрійте духовку до 350˚F

    1. Приготуйте тісто та вилийте його у форму.
       {{</* note */>}}Змастіть форму для кращих результатів.{{</* /note */>}}

    1. Випікайте 20-25 хвилин або до готовності.

Вихідний результат:

1. Розігрійте духовку до 350˚F

1. Приготуйте тісто та вилийте його у форму.

   {{< note >}}Змастіть форму для кращих результатів.{{< /note >}}

1. Випікайте 20-25 хвилин або до готовності.

### Вирази Include {#include-statements}

Shortcode всередині include statements зламають збірку. Необхідно вставити їх у батьківський документ до і після виклику include. Наприклад:

```hugo
{{</* note */>}}
{{</* include "task-tutorial-prereqs.md" */>}}
{{</* /note */>}}
```

## Елементи Markdown {#markdown-elements}

{{<note>}}
*Від перекладача*

Не всі описані нижче вимоги до форматування тексту в Markdown використовуються в форматуванні англійською є оптимальними, частина з них відхиляються від стандартних вимог, щодо форматування тексту в Markdown.

В українській версії документації використовується стандартне форматування тексту в Markdown, яке відповідає загальноприйнятим стандартам.
{{</note>}}

### Переноси рядків {#line-breaks}

Використовуйте один символ переносу рядка (`\n`) для розділення контенту на рівні блоків, таких як заголовки, списки, зображення, блоки коду тощо. Винятком є заголовки другого рівня, де необхідно зробити два переноси рядка. Заголовки другого рівня слідують після заголовків першого рівня (або заголовка) без передуючих абзаців або тексту. Два переноси рядка допомагають краще візуалізувати загальну структуру контенту в текстовому редакторі.

Ручне перенесення абзаців у вихідному коді Markdown є доречним, оскільки інструмент git та сайт GitHub генерують порівняння файлів на основі рядків. Ручне перенесення довгих рядків допомагає рецензентам легко знаходити зміни у PR і надавати зворотний звʼязок. Це також допомагає командам, які займаються локалізацією, відслідковувати зміни на рівні рядків[^1]. Перенесення рядка може відбуватися в кінці речення або після знака пунктуації. Винятком є випадки, коли Markdown-посилання або шорткод очікується в одному рядку.

[^1]: Це твердження є хибним оскільки такий підхід ускладнює виконання перекладів речень які в початковому тексті розділені на кілька рядків. Розбивання речення на кілька рядків унеможлювлює використання систем роботи з перекладами, що працюють на рівні рядків, а не речень. В середині речень не має бути переносів на новий рядок!!!

### Заголовки та назви {#headings}

Користувачі цієї документації можуть використовувати інструменти озвучування тексту (екранний зчитувач) або іншу допоміжну технологію (AT). [Екранні зчитувачі](https://en.wikipedia.org/wiki/Screen_reader) є лінійними вихідними пристроями, що виводять елементи на сторінку по одному. Якщо на сторінці багато контенту, ви можете використовувати заголовки для створення внутрішньої структури сторінки. Гарна структура сторінки допомагає всім користувачам легко орієнтуватися на сторінці або фільтрувати теми, які їх цікавлять.

{{< table caption = "Рекомендовані та не рекомендовані приклади використання заголовків" >}}
Рекомендовано | Небажано
:--| :-----
Оновлюйте заголовок у метаданих сторінки або блогу. | Використовуйте заголовки першого рівня, оскільки Hugo автоматично перетворює заголовок у метаданих сторінки на заголовок першого рівня.
Використовуйте впорядковані заголовки для надання змістовного високорівневого конспекту вашого контенту. | Використовуйте заголовки рівнів 4-6, якщо це абсолютно необхідно. Якщо ваш контент настільки деталізований, можливо, його слід розбити на окремі статті.
Використовуйте символи фунта або решітки (`#`) для контенту, що не відноситься до блогу. | Використовуйте підкреслення (`---` або `===`) для позначення заголовків першого рівня.
Використовуйте "sentence case" (великі літери тільки на початку речення) для заголовків у тілі сторінки. Наприклад, **Розширення kubectl за допомогою втулків** | Використовуйте "title case" (великі літери на початку кожного слова) для заголовків у тілі сторінки. Наприклад, **Розширення Kubectl За Допомогою Втулків**
Використовуйте "title case" для заголовків сторінок у метаданих. Наприклад, `title: Kubernetes API Server Bypass Risks` | Використовуйте "sentence case" для заголовків сторінок у метаданих. Наприклад, не використовуйте `title: Kubernetes API server bypass risks`
Розмістіть відповідні посилання в основному тексті. | Використовуйте гіперпосилання (`<a href=""></a>`) у заголовках.
Для позначення заголовків використовуйте знаки фунтів або хешу (`#`). | Використовуйте **жирний** текст або інші індикатори для розділення абзаців.
{{< /table >}}

### Абзаци {#paragraphs}

{{< table caption = "Рекомендовані та не рекомендовані приклади використання абзаців" >}}
Рекомендовано | Небажано
:--| :-----
Намагайтеся, щоб абзаци не перевищували 6 речень. | Не відступайте перший абзац пробілами. Наприклад, ⋅⋅⋅Три пробіли перед абзацом зроблять його абзацем з відступом.
Використовуйте три дефіси (`---`), щоб створити горизонтальну лінію. Використовуйте горизонтальні лінії для розділення контенту в абзацах. Наприклад, зміна сцени в історії або зміна теми в розділі. | Не використовуйте горизонтальні лінії для декорацій.
{{< /table >}}

### Посилання {#links}

{{< table caption = "Рекомендовані та не рекомендовані приклади використання посилань" >}}
Рекомендовано | Небажано
:--| :-----
Створюйте гіперпосилання, що надають контекст для dvscne, на який вони посилаються. Наприклад: Деякі порти на ваших машинах відкриті. Дивіться <a href="#check-required-ports">Перевірка необхідних портів</a> для деталей. | Використовуйте неоднозначні терміни, такі як "натисніть тут". Наприклад: Деякі порти на ваших машинах відкриті. Дивіться <a href="#check-required-ports">тут</a> для деталей.
Створюйте посилання в стилі Markdown: `[текст посилання](URL)`. Наприклад: `[Hugo shortcodes](/uk/docs/contribute/style/hugo-shortcodes/#table-captions)` і вихід буде [Hugo shortcodes](/uk/docs/contribute/style/hugo-shortcodes/#table-captions). | Використовуйте посилання в стилі HTML: `<a href="/media/examples/link-element-example.css" target="_blank">Відвідайте наш підручник!</a>`, або створюйте посилання, що відкриваються в нових вкладках або вікнах. Наприклад: `[приклад сайту](https://example.com){target="_blank"}`
{{< /table >}}

### Списки {#lists}

Групуйте елементи в списках, які повʼязані між собою і повинні зʼявлятися у певному порядку або для позначення кореляції між кількома елементами. Коли екранний зчитувач натрапляє на список, незалежно від того, чи це упорядкований або неупорядкований список, він оголошує користувачеві, що є група елементів списку. Потім користувач може використовувати клавіші зі стрілками для переміщення між різними елементами списку.

- Закінчуйте кожен елемент у списку крапкою, якщо один або більше елементів у списку є завершеними реченнями. Для збереження послідовності зазвичай всі елементи або жоден з них мають бути завершеними реченнями.

  {{< note >}}
  Упорядковані списки, що є частиною незавершеного вступного речення, можуть бути написані з маленької літери і пунктуацією так, ніби кожен елемент є частиною вступного речення.
  {{< /note >}}

- Використовуйте цифру один з крапкою (`1.`)  для упорядкованих списків.

- Використовуйте (`+`), (`*`), або (`-`) для неупорядкованих списків, але якийсь один з цих символів у одному тексті (уникайте їх змішування)

- Залишайте порожній рядок після кожного списку.

- Відступайте вкладені списки на відповідну кількість пробілів, так щоб сімвол початку елемента спіску був на рівні з початком тексту елемента вищого рівня (наприклад, ⋅⋅⋅).

- Елементи списку можуть складатися з кількох абзаців. Кожен наступний абзац у пункті списку повинен бути відступлений нарівень початку тексту елементу списку або один табулятор.

### Таблиці {#tables}

Семантична мета таблиці — це представлення табличних даних. Користувачі з гарним зором можуть швидко сканувати таблицю, але екранний зчитувач проходить її рядок за рядком. Підпис таблиці використовується для створення описового заголовка для таблиці даних. Допоміжні технології (AT) використовують елемент підпису HTML для таблиці, щоб ідентифікувати вміст таблиці користувачеві в межах структури сторінки.

- Додавайте підписи до таблиць за допомогою [shortcodes Hugo](/uk/docs/contribute/style/hugo-shortcodes/#table-captions) для таблиць.

## Рекомендації щодо створення контенту {#content-best-practices}

Цей розділ містить рекомендації для створення чіткого, лаконічного і послідовного контенту.

### Використовуйте теперішній час {#use-present-tense}

{{< table caption = "Рекомендовані та не рекомендовані приклади використання теперішнього часу" >}}
Рекомендовано | Не рекомендовано
:--| :-----
Ця команда запускає проксі. | Ця команда запустить проксі.
{{< /table >}}

Виняток: Використовуйте майбутній або минулий час, якщо це необхідно для передачі правильного значення.

### Використовуйте активний стан {#use-active-voice}

{{< table caption = "Рекомендовані та не рекомендовані приклади використання активного стану" >}}
Рекомендовано | Не рекомендовано
:--| :-----
Ви можете дослідити API за допомогою оглядача. | API можна дослідити за допомогою оглядача.
Файл YAML визначає кількість реплік. | Кількість реплік визначена у файлі YAML.
{{< /table >}}

Виняток: Використовуйте пасивний стан, якщо активний стан призводить до незручної конструкції.

### Використовуйте просту і пряму мову {#use-simple-and-direct-language}

Використовуйте просту і пряму мову. Уникайте використання зайвих фраз, наприклад, слова "будь ласка".

{{< table caption = "Рекомендовані та не рекомендовані приклади використання простої і прямої мови" >}}
Рекомендовано | Не рекомендовано
:--| :-----
Щоб створити ReplicaSet, ... | Для того щоб створити ReplicaSet, ...
Дивіться конфігураційний файл. | Будь ласка, дивіться конфігураційний файл.
Перегляньте Podʼи. | За допомогою наступної команди ми переглянемо Podʼи.
{{< /table >}}

### Звертайтесь до читача на "ви"

{{< table caption = "Рекомендовані та не рекомендовані приклади звернення до читача" >}}
Рекомендовано | Не рекомендовано
:--| :-----
Ви можете створити Deployment за допомогою ... | Ми створимо Deployment за допомогою ...
У попередньому виводі ви можете побачити... | У попередньому виведенні ми можемо бачити ...
{{< /table >}}

### Уникайте латинських фраз {#avoid-latin-phrases}

Віддавайте перевагу англійським (місцевим) термінам замість латинських абревіатур.

{{< table caption = "Рекомендовані та не рекомендовані приклади уникнення латинських фраз" >}}
Рекомендовано | Не рекомендовано
:--| :-----
For example (Наприклад), ... | e.g., ...
That is (Тобто), ...| i.e., ...
{{< /table >}}

Виняток: Використовуйте "etc." (et cetera) для позначення "та інше".

## Шаблони, яких слід уникати {#patterns-to-avoid}

### Уникайте використання "ми" {#avoid-using-we}

Використання "ми" у реченні може бути заплутаним, оскільки читач може не знати, чи є він частиною "ми", про яке ви говорите.

{{< table caption = "Рекомендовані та не рекомендовані приклади використання \"ми\"" >}}
Рекомендовано | Не рекомендовано
:--| :-----
Версія 1.4 включає ... | У версії 1.4 ми додали ...
Kubernetes надає нову функцію для ... | Ми надаємо нову функцію ...
Ця сторінка навчить вас, як використовувати Podʼи. | На цій сторінці ми навчимося про Podʼи.
{{< /table >}}

### Уникайте жаргону та ідіом {#avoid-jargon-and-idioms}

Для багатьох читачів англійська є другою мовою. Уникайте жаргону та ідіом, щоб допомогти їм краще зрозуміти тему.

{{< table caption = "Правильні і неправильні приклади уникання жаргону та ідіом" >}}
Рекомендовано | Не рекомендовано
:--| :-----
Internally, ... | Under the hood, ...
Create a new cluster. | Turn up a new cluster.
{{< /table >}}

### Уникайте тверджень про майбутнє {#avoid-statements-about-the-future}

Уникайте обіцянок або натяків на майбутнє. Якщо вам потрібно говорити про функцію в альфа-версії, розмістіть текст під заголовком, який позначає його як альфа-інформацію.

Винятком з цього правила є документація про оголошені застарівання функцій, які плануються до видалення в майбутніх версіях. Один з прикладів такої документації — [Посібник з міграції із застарілих API](/uk/docs/reference/using-api/deprecation-guide/).

### Уникайте тверджень, які незабаром стануть неактуальними {#avoid-statements-that-will-soon-be-out-of-date}

Уникайте слів таких як "зараз" і "новий". Функція, яка є новою сьогодні, може не вважатися новою через кілька місяців.

{{< table caption = "Правильні і неправильні приклади уникання тверджень, які незабаром стануть застарілими" >}}
Рекомендовано | Не рекомендовано
:--| :-----
У версії 1.4, ... | У поточній версії, ...
Функція Federation надає ... | Нова функція Federation надає ...
{{< /table >}}

### Уникайте слів, що припускають певний рівень розуміння {#avoid-words-that-assume-a-specific-level-of-understanding}

Уникайте слів таких як "просто", "легко", "зрозуміло". Ці слова не додають цінності.

{{< table caption = "Правильні і неправильні приклади уникання слів, що припускають певний рівень розуміння" >}}
Рекомендовано | Не рекомендовано
:--| :-----
Включіть одну команду в ... | Включіть просто одну команду в ...
Запустіть контейнер ... | Продовжте запускати контейнер ...
Ви можете видалити ... | Ви можете легко видалити ...
Ці кроки ... | Ці прості кроки ...
{{< /table >}}

### Файл EditorConfig {#editorconfig-file}

Проєкт Kubernetes підтримує файл EditorConfig, який встановлює загальні стилістичні уподобання в текстових редакторах, таких як VS Code. Ви можете використовувати цей файл, якщо хочете переконатися, що ваші внески відповідають решті проєкту. Щоб переглянути файл, зверніться до [`.editorconfig`](https://github.com/kubernetes/website/blob/main/.editorconfig) в кореневій теці репозиторію.

## {{% heading "whatsnext" %}}

- Дізнайтеся про [написання нової теми](/uk/docs/contribute/style/write-new-topic/).
- Дізнайтеся про [використання шаблонів сторінок](/uk/docs/contribute/style/page-content-types/).
- Дізнайтеся про [власні hugo shortcodes](/uk/docs/contribute/style/hugo-shortcodes/).
- Дізнайтеся про [створення pull request](/uk/docs/contribute/new-content/open-a-pr/).