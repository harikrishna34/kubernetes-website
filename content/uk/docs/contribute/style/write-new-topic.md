---
title: Написання нової теми
content_type: task
weight: 70
---

<!-- overview -->

Ця сторінка показує, як створити нову тему для документації Kubernetes.

## {{% heading "prerequisites" %}}

Створіть форк репозиторію документації Kubernetes, як описано в розділі [Створення PR](/uk/docs/contribute/new-content/open-a-pr/).

<!-- steps -->

## Вибір типу сторінки {#choosing-a-page-type}

Перед тим, як почати писати нову тему, подумайте про тип сторінки, який найкраще підходить для вашого контенту:

{{< table caption = "Керівництво з вибору типу сторінки" >}}
Тип | Опис
:--- | :----------
Concept | Сторінка концепту пояснює певний аспект Kubernetes. Наприклад, сторінка концепту може описувати обʼєкт Kubernetes Deployment і пояснювати його роль як застосунку під час його розгортання, масштабування та оновлення. Зазвичай сторінки концептів не містять послідовностей кроків, але натомість надають посилання на завдання або підручники. Для прикладу теми концепту, див. [Вузли](/uk/docs/concepts/architecture/nodes/).
Task | Сторінка завдання показує, як виконати одне конкретне завдання. Ідея полягає в тому, щоб надати читачам послідовність кроків, які вони можуть виконати під час читання сторінки. Сторінка завдання може бути короткою або довгою, за умови, що вона зосереджена на одній темі. На сторінці завдання можна поєднувати короткі пояснення з кроками, які потрібно виконати, але якщо вам потрібно надати докладне пояснення, ви повинні зробити це в темі концепту. Повʼязані теми завдань і концептів повинні посилатися одна на одну. Для прикладу короткої сторінки завдання див. [Налаштування контейнера Pod для використання тому для зберігання](/uk/docs/tasks/configure-pod-container/configure-volume-storage/). Для прикладу довшої сторінки завдання див. [Налаштування проб для перевірки працездатності та готовності](/uk/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/).
Tutorial | Сторінка підручника показує, як досягти мети, яка обʼєднує кілька функцій Kubernetes. Підручник може містити кілька послідовностей кроків, які читачі можуть виконувати під час читання сторінки. Або він може надавати пояснення повʼязаних фрагментів коду. Наприклад, підручник може надати покроковий огляд зразка коду. Підручник може включати короткі пояснення функцій Kubernetes, які обʼєднуються, але повинен посилатися на відповідні теми концептів для детального пояснення окремих функцій.
{{< /table >}}

### Створення нової сторінки {#creating-a-new-page}

Використовуйте [тип контенту](/uk/docs/contribute/style/page-content-types/) для кожної нової сторінки, яку ви пишете. Сайт документації надає шаблони або [Hugo archetypes](https://gohugo.io/content-management/archetypes/) для створення нових сторінок контенту. Щоб створити нову сторінку, запустіть команду `hugo new` з шляхом до файлу, який ви хочете створити. Наприклад:

```shell
hugo new docs/concepts/my-first-concept.md
```

## Вибір заголовка та імені файлу {#choosing-a-title-and-filename}

Виберіть заголовок, який містить ключові слова, за якими ви хочете, щоб пошукові системи знаходили вашу сторінку. Створіть імʼя файлу, використовуючи слова в заголовку, розділені дефісами. Наприклад, тема з заголовком [Використання HTTP-проксі для доступу до API Kubernetes](/uk/docs/tasks/extend-kubernetes/http-proxy-access-api/) має імʼя файлу `http-proxy-access-api.md`. Вам не потрібно додавати слово "kubernetes" в імʼя файлу, оскільки "kubernetes" вже є в URL для теми, наприклад:

```none
/docs/tasks/extend-kubernetes/http-proxy-access-api/
```

## Додавання заголовка теми до метаданих front matter{#adding-the-topic-title-to-the-front-matter}

У вашій темі додайте поле `title` до [метаданих](https://gohugo.io/content-management/front-matter/). Метадані — це блок YAML, який знаходиться між потрійними рисками на початку сторінки. Ось приклад:

```yaml
---
title: Використання HTTP-проксі для доступу до API Kubernetes
---
```

## Вибір теки {#choosing-a-directory}

Залежно від типу сторінки, розмістіть ваш новий файл у підтеці однієї з тек:

* /content/en/docs/tasks/
* /content/en/docs/tutorials/
* /content/en/docs/concepts/

Ви можете розмістити свій файл у наявній підтеці або створити нову підтекуг.

## Розміщення вашої теми в таблиці змісту {#adding-your-topic-to-the-table-of-contents}

Таблиця змісту створюється динамічно, використовуючи структуру тек вихідного коду документації. Теки верхнього рівня у `/content/en/docs/` створюють навігацію верхнього рівня, а підтеки мають власні записи в таблиці змісту.

Кожна підтека має файл `_index.md`, який представляє "домашню" сторінку для контенту даної підтеки. `_index.md` не потребує шаблону. Він може містити оглядовий контент про теми в теці.

Інші файли в теці зазвичай сортуються в алфавітному порядку. Це майже ніколи не є найкращим випадком. Щоб контролювати відносне сортування тем у підтеці, встановіть в ключ метаданих `weight:` значення, ціле число. Зазвичай ми використовуємо кратні 10, щоб врахувати додавання тем пізніше. Наприклад, тема з вагою `10` буде розташована перед темою з вагою `20`.

## Вбудовування коду у вашу тему {#embedding-code-in-your-topic}

Якщо ви хочете включити якийсь код у вашу тему, ви можете вбудувати код безпосередньо у файл, використовуючи синтаксис блоку коду markdown. Це рекомендується в таких випадках (не вичерпний список):

* Код показує вивід з команди, наприклад `kubectl get deploy mydeployment -o json | jq '.status'`.
* Код недостатньо загальний для того, щоб користувачі могли його випробувати. Наприклад, ви можете вбудувати YAML файл для створення Pod, який залежить від конкретної реалізації [FlexVolume](/uk/docs/concepts/storage/volumes/#flexvolume).
* Код є неповним прикладом, оскільки його мета — підкреслити частину великого файлу. Наприклад, при описі способів налаштування [RoleBinding](/uk/docs/reference/access-authn-authz/rbac/#role-binding-examples), ви можете надати короткий фрагмент безпосередньо у вашому файлі теми.
* Код не призначений для того, щоб користувачі його випробовували з інших причин. Наприклад, коли ви описуєте, як новий атрибут має бути доданий до ресурсу за допомогою команди `kubectl edit`, ви можете надати короткий приклад, який містить лише атрибут для додавання.

## Включення коду з іншого файлу {#including-code-from-another-file}

Інший спосіб включити код у вашу тему — створити новий, повний зразок файлу (або групи зразків файлів), а потім посилатися на зразок із вашої теми. Використовуйте цей метод для включення зразків YAML файлів, коли зразок є загальним і багаторазовим, і ви хочете, щоб читач спробував його самостійно.

При додаванні нового самостійного зразка файлу, такого як YAML файл, розмістіть код в одній з підтек `<LANG>/examples/`, де `<LANG>` — це мова для теми. У файлі вашої теми використовуйте shortcode `code_sample`:

```hugo
{{%/* code_sample file="<RELPATH>/my-example-yaml>" */%}}
```

де `<RELPATH>` — це шлях до файлу, який потрібно включити, відносно теки `examples`. Наступний shortcode Hugo посилається на YAML файл, розташований за адресою `/content/en/examples/pods/storage/gce-volume.yaml`.

```hugo
{{%/* code_sample file="pods/storage/gce-volume.yaml" */%}}
```

## Показ як створити обʼєкт API з файлу конфігурації {#showing-how-to-create-an-api-object-from-a-configuration-file}

Якщо вам потрібно продемонструвати, як створити обʼєкт API на основі файлу конфігурації, розмістіть файл конфігурації в одній з підтек у `<LANG>/examples`.

У вашій темі вкажіть цю команду:

```shell
kubectl create -f https://k8s.io/examples/pods/storage/gce-volume.yaml
```

{{< note >}}
Коли додаєте нові YAML файли до теки `<LANG>/examples`, переконайтеся, що файл також включено до файлу `<LANG>/examples_test.go`. Система Travis CI для вебсайту автоматично запускає цей тест, коли подаються PR, щоб переконатися, що всі приклади проходять тести.
{{< /note >}}

Для прикладу теми, яка використовує цей прийом, див. [Запуск Stateful застосунку в одному екземплярі](/uk/docs/tasks/run-application/run-single-instance-stateful-application/).

## Додавання зображень до теми {#adding-images-to-your-topic}

Розмістіть файли зображень у теці `/images`. Переважний формат зображення — SVG.

## {{% heading "whatsnext" %}}

* Дізнайтеся про [використання типів контенту сторінок](/uk/docs/contribute/style/page-content-types/).
* Дізнайтеся про [створення pull request](/uk/docs/contribute/new-content/open-a-pr/).