---
title: Ролі та обовʼязки
content_type: concept
weight: 10
---

<!-- overview -->

Будь-хто може зробити внесок у Kubernetes. Зі зростанням ваших внесків до SIG Docs, ви можете подати заявку на різні рівні членства в спільноті. Ці ролі дозволяють брати на себе більше відповідальності в спільноті. Кожна роль вимагає більше часу та відданості. Ролі є такими:

- Будь-хто: регулярні учасники документації Kubernetes
- Члени: можуть призначати та розподіляти тікети, а також надавати відгук на pull requestʼи, який не є обовʼязковим до виконання
- Рецензенти: можуть керувати рецензією документаційних pull request'ів і гарантувати якість змін
- Затверджувачі: можуть керувати рецензією документації та зливати зміни

<!-- body -->

## Будь-хто {#anyone}

Будь-хто з обліковим записом GitHub може зробити свій внесок у Kubernetes. SIG Docs вітає всіх нових учасників!

Будь-хто може:

- Створити тікет в будь-якому [репозиторії Kubernetes](https://github.com/kubernetes/), включаючи [`kubernetes/website`](https://github.com/kubernetes/website)
- Надати відгук на pull request, який не є обовʼязковим для виконання
- Зробити внесок у локалізацію
- Запропонувати покращення у [Slack](https://slack.k8s.io/) або в [списку розсилки SIG docs](https://groups.google.com/forum/#!forum/kubernetes-sig-docs).

Після [підписання CLA](https://github.com/kubernetes/community/blob/master/CLA.md), будь-хто також може:

- Створити pull request для покращення наявного контенту, додавання нового контенту або написання блогу чи прикладу використання
- Створювати діаграми, графічні ресурси та вбудовані відеозаписи та відео

Для отримання додаткової інформації дивіться [додавання нового контенту](/uk/docs/contribute/new-content/).

## Члени {#members}

Член — це хтось, хто подав кілька pull request'ів до `kubernetes/website`. Члени є частиною [організації Kubernetes на GitHub](https://github.com/kubernetes).

Члени можуть:

- Робити все, що зазначено в розділі [Будь-хто](#anyone)
- Використовувати коментар `/lgtm`, щоб додати мітку LGTM (виглядає добре для мене) до pull request'у

  {{< note >}}
  Використання `/lgtm` запускає автоматизацію. Якщо ви хочете надати не обовʼязкове схвалення, коментар "LGTM" також працює!
  {{< /note >}}

- Використовувати коментар `/hold`, щоб заблокувати злиття для pull request'у
- Використовувати коментар `/assign`, щоб призначити рецензента для pull requestʼу
- Робити рецензування pull request'ів, які не є обовʼязковими
- Використовувати автоматизацію для розподілу та категоризації тікетів
- Документувати нові функції

### Набуття членства {#becoming-a-member}

Після подання щонайменше 5 значних pull request'ів та виконання інших [вимог](https://github.com/kubernetes/community/blob/master/community-membership.md#member):

1. Знайдіть двох [рецензентів](#reviewers) або [затверджувачів](#approvers), які стануть вашими [поручителями](/uk/docs/contribute/advanced#sponsor-a-new-contributor).

   Попросіть поручительства в [каналі #sig-docs на Slack](https://kubernetes.slack.com) або в [списку розсилки SIG Docs](https://groups.google.com/forum/#!forum/kubernetes-sig-docs).

   {{< note >}}
   Не надсилайте прямий електронний лист або пряме повідомлення у Slack окремому члену SIG Docs. Ви повинні запитати про поручительство перед поданням вашої заявки на членство.
   {{< /note >}}

2. Відкрийте тікет на GitHub у [репозиторії `kubernetes/org`](https://github.com/kubernetes/org/). Використовуйте шаблон тікета **Organization Membership Request**.

3. Повідомте своїх поручителів про тікет на GitHub. Ви можете:
   - Згадати їх через GitHub-імʼя у тікеті (`@<GitHub-username>`)
   - Надіслати їм посилання на тікет за допомогою Slack або електронної пошти.

     Поручителі схвалюють ваш запит позначкою `+1`. Після схвалення запиту вашими поручителями, адміністратор GitHub Kubernetes додає вас як члена. Вітаємо!

     Якщо ваш запит на членство не приймається, ви отримаєте відгук. Після врахування відгуків подайте заявку знову.

4. Прийміть запрошення до організації Kubernetes на GitHub у своєму обліковому записі електронної пошти.

   {{< note >}}
   GitHub надсилає запрошення на основну електронну адресу у вашому обліковому записі.
   {{< /note >}}

## Рецензенти {#reviewers}

Рецензенти відповідають за рецензування відкритих pull request'ів. На відміну від відгуків членів, автор PR повинен враховувати відгуки рецензентів. Рецензенти є членами команди GitHub [@kubernetes/sig-docs-{language}-reviews](https://github.com/orgs/kubernetes/teams?query=sig-docs).

Рецензенти можуть:

- Робити все, що зазначено в розділах [Будь-хто](#anyone) та [Члени](#members)
- Оглядати pull requestʼи та надавати обовʼязковий відгук

  {{< note >}}
  Щоб надати не обовʼязковий відгук, додайте до ваших коментарів фразу типу "Optionally: ".
  {{< /note >}}

- Редагувати рядки, що стосуються користувачів, у коді
- Покращувати коментарі до коду

Ви можете бути рецензентом SIG Docs або рецензентом для документів у певній предметній області.

### Призначення рецензентів до pull requestʼів {#assigning-reviewers-to-pull-requests}

Автоматизація призначає рецензентів до всіх pull requestʼів. Ви можете запросити огляд від конкретної особи, додавши коментар: `/assign [@_github_handle]`.

Якщо призначений рецензент не прокоментував PR, інший рецензент може втрутитися. Ви також можете призначати технічних рецензентів за потреби.

### Використання `/lgtm` {#using-lgtm}

LGTM означає "Виглядає добре для мене" і вказує, що pull request є технічно точним і готовим до злиття. Усі PR потребують коментаря `/lgtm` від рецензента та коментаря `/approve` від затверджувача для злиття.

Коментар `/lgtm` від рецензента є обовʼязковим і запускає автоматизацію, яка додає мітку `lgtm`.

### Як стати рецензентом {#becoming-a-reviewer}

Коли ви відповідаєте [вимогам](https://github.com/kubernetes/community/blob/master/community-membership.md#reviewer), ви можете стати рецензентом SIG Docs. Рецензенти в інших SIG повинні подавати окрему заявку на статус рецензента в SIG Docs.

Щоб подати заявку:

1. Відкрийте pull request, що додає ваше імʼя користувача GitHub до розділу файлу [OWNERS_ALIASES](https://github.com/kubernetes/website/blob/main/OWNERS_ALIASES) в репозиторії `kubernetes/website`.

   {{< note >}}
   Якщо ви не впевнені, де себе додати, додайте себе до `sig-docs-en-reviews`.
   {{< /note >}}

1. Призначте PR одному або кільком затверджувачам SIG Docs (імена користувачів вказані в `sig-docs-{language}-owners`).

Якщо заявку схвалено, лідер SIG Docs додає вас до відповідної команди GitHub. Після додавання [K8s-ci-robot](https://github.com/kubernetes/test-infra/tree/master/prow#bots-home) призначає та пропонує вас як рецензента на нові pull requestʼи.

## Затверджувачі {#approvers}

Затверджувачі оглядають і затверджують pull requestʼи для злиття. Затверджувачі є членами команд GitHub [@kubernetes/sig-docs-{language}-owners](https://github.com/orgs/kubernetes/teams/?query=sig-docs).

Затверджувачі можуть робити наступне:

- Все, що зазначено в розділах [Будь-хто](#anyone), [Члени](#members) та [Рецензенти](#reviewers)
- Публікувати контент учасників, затверджуючи та зливаючи pull requestʼи за допомогою коментаря `/approve`
- Пропонувати покращення до посібника зі стилю
- Пропонувати покращення до тестів документації
- Пропонувати покращення до вебсайту Kubernetes або інших інструментів

Якщо PR вже має `/lgtm`, або якщо затверджувач також додає коментар `/lgtm`, PR автоматично зливається. Затверджувач SIG Docs повинен залишити коментар `/lgtm` лише на змінах, які не потребують додаткового технічного огляду.

### Затвердження pull requestʼів

Затверджувачі та лідери SIG Docs є єдиними, хто може зливати pull requestʼи в репозиторій вебсайту. Це супроводжується певними обовʼязками.

- Затверджувачі можуть використовувати команду `/approve`, яка зливає PR в репозиторій.

  {{< warning >}}
  Недбале злиття може зламати сайт, тому переконайтеся, що, коли ви щось зливаєте, ви впевнені в цьому.
  {{< /warning >}}

- Переконайтеся, що запропоновані зміни відповідають [посібнику зі змісту документації](/uk/docs/contribute/style/content-guide/).

  Якщо у вас є питання, або ви не впевнені в чомусь, не соромтеся запросити додатковий огляд.

- Переконайтеся, що тести Netlify пройшли перед тим, як ви використаєте команду `/approve` для PR.

    <img src="/images/docs/contribute/netlify-pass.png" width="75%" alt="Тести Netlify повинні пройти перед затвердженням" />

- Відвідайте попередній перегляд сторінки Netlify для PR, щоб переконатися, що все виглядає добре перед затвердженням.

- Беріть участь у [графіку чергування PR Wrangler](https://github.com/kubernetes/website/wiki/PR-Wranglers) для щотижневих ротацій. SIG Docs очікує, що всі затверджувачі братимуть участь у цій ротації. Дивіться [PR чергування](/uk/docs/contribute/participate/pr-wranglers/) для отримання додаткової інформації.

### Як стати затверджувачем {#becoming-an-approver}

Коли ви відповідаєте [вимогам](https://github.com/kubernetes/community/blob/master/community-membership.md#approver), ви можете стати затверджувачем SIG Docs. Затверджувачі в інших SIG повинні подавати окрему заявку на статус затверджувача в SIG Docs.

Щоб подати заявку:

1. Відкрийте pull request, що додає вас до розділу файлу [OWNERS_ALIASES](https://github.com/kubernetes/website/blob/main/OWNERS_ALIASES) у репозиторії `kubernetes/website`.

    {{< note >}}
    Якщо ви не впевнені, де себе додати, додайте себе до `sig-docs-en-owners`.
    {{< /note >}}

2. Призначте PR одному або кільком поточним затверджувачам SIG Docs.

Якщо заявку схвалено, лідер SIG Docs додає вас до відповідної команди GitHub. Після додавання, [@k8s-ci-robot](https://github.com/kubernetes/test-infra/tree/master/prow#bots-home) призначає та пропонує вас як рецензента на нові pull request'и.

## {{% heading "whatsnext" %}}

- Прочитайте про [PR чергування](/uk/docs/contribute/participate/pr-wranglers/), роль, яку всі затверджувачі виконують по черзі.