---
api_metadata:
  apiVersion: "coordination.k8s.io/v1alpha1"
  import: "k8s.io/api/coordination/v1alpha1"
  kind: "LeaseCandidate"
content_type: "api_reference"
description: "LeaseCandidate визначає кандидата для об'єкта Lease."
title: "LeaseCandidate v1alpha1"
weight: 6
---

`apiVersion: coordination.k8s.io/v1alpha1`

`import "k8s.io/api/coordination/v1alpha1"`

## LeaseCandidate {#LeaseCandidate}

LeaseCandidate визначає кандидата для обʼєкта Lease. Кандидати створюються таким чином, щоб координований вибір лідера вибрав найкращого лідера з переліку кандидатів.

---

- **apiVersion**: coordination.k8s.io/v1alpha1

- **kind**: LeaseCandidate

- **metadata** (<a href="{{< ref "../common-definitions/object-meta#ObjectMeta" >}}">ObjectMeta</a>)

  Докладніше: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#metadata

- **spec** (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidateSpec" >}}">LeaseCandidateSpec</a>)

  spec містить специфікацію Lease. Докладніше: <https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#spec-and-status>.

## LeaseCandidateSpec {#LeaseCandidateSpec}

LeaseCandidateSpec є специфікацією Lease.

---

- **leaseName** (string), обовʼязково

  LeaseName — це імʼя Lease, за який цей кандидат змагається. Це поле є незмінним.

- **preferredStrategies** ([]string), обовʼязково

  *Atomic: буде замінено під час злиття*

  PreferredStrategies вказує на список стратегій для вибору лідера у координованому виборі лідера. Список упорядкований, і перша стратегія переважає всі інші стратегії. Цей список використовується координованим вибором лідера для прийняття рішення про остаточну стратегію виборів. Це передбачає:

  - Якщо всі клієнти мають стратегію X як перший елемент у цьому списку, буде використана стратегія X.
  - Якщо кандидат має стратегію [X], а інший кандидат має стратегію [Y, X], Y переважає X, і буде використана стратегія Y.
  - Якщо кандидат має стратегію [X, Y], а інший кандидат має стратегію [Y, X], це є помилкою користувача, і вибір лідера не буде здійснюватися до вирішення проблеми.

  (Альфа) Для використання цього поля потрібно увімкнути функціональну можливість CoordinatedLeaderElection.

- **binaryVersion** (string)

  BinaryVersion — це бінарна версія. Вона повинна бути у форматі semver без початкової `v`. Це поле є обовʼязковим, коли стратегія "OldestEmulationVersion".

- **emulationVersion** (string)

  EmulationVersion —це версія емуляції. Вона повинна бути у форматі semver без початкової `v`. EmulationVersion повинна бути менше або дорівнювати BinaryVersion. Це поле є обовʼязковим, коли стратегія є "OldestEmulationVersion".

- **pingTime** (MicroTime)

  PingTime — це останній час, коли сервер запитував LeaseCandidate на продовження. Це виконується лише під час вибору лідера, щоб перевірити, чи стали якісь LeaseCandidates недійсними. Коли PingTime оновлюється, LeaseCandidate відповідає, оновлюючи RenewTime.

  <a name="MicroTime"></a>
  *MicroTime — це версія Time з точністю до мікросекунд.*

- **renewTime** (MicroTime)

  RenewTime — це час, коли LeaseCandidate був востаннє оновлений. Щоразу, коли Lease потребує вибору лідера, поле PingTime оновлюється, щоб сигналізувати LeaseCandidate про необхідність оновлення RenewTime. Старі обʼєкти LeaseCandidate також видаляються, якщо пройшло кілька годин з моменту останнього оновлення. Поле PingTime регулярно оновлюється, щоб запобігти видаленню ще активних LeaseCandidates.

  <a name="MicroTime"></a>
  *MicroTime — це версія Time з точністю до мікросекунд.*

## LeaseCandidateList {#LeaseCandidateList}

LeaseCandidateList — перелік обʼєктів Lease.

---

- **apiVersion**: coordination.k8s.io/v1alpha1

- **kind**: LeaseCandidateList

- **metadata** (<a href="{{< ref "../common-definitions/list-meta#ListMeta" >}}">ListMeta</a>)

  Стандартні метадані списку. Докладніше: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds

- **items** ([]<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>), обовʼязково

  items — список обʼєктів схеми.

## Operations {#Operations}

---

### `get` отримати вказаного LeaseCandidate {#get-read-the-specified-leasecandidate}

#### HTTP запит {#http-request}

GET /apis/coordination.k8s.io/v1alpha1/namespaces/{namespace}/leasecandidates/{name}

#### Параметри {#parameters}

- **name** (*в шляху*): string, обовʼязково

  імʼя LeaseCandidate

- **namespace** (*в шляху*): string, обовʼязково

  <a href="{{< ref "../common-parameters/common-parameters#namespace" >}}">namespace</a>

- **pretty** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#pretty" >}}">pretty</a>

#### Відповідь {#response}

200 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>): OK

401: Unauthorized

### `list` перелік або перегляд обʼєктів типу LeaseCandidate {#list-list-or-watch-objects-of-kind-leasecandidate}

#### HTTP запит {#http-request-1}

GET /apis/coordination.k8s.io/v1alpha1/namespaces/{namespace}/leasecandidates

#### Параметри {#parameters-1}

- **namespace** (*в шляху*): string, обовʼязково

  <a href="{{< ref "../common-parameters/common-parameters#namespace" >}}">namespace</a>

- **allowWatchBookmarks** (*в запиті*): boolean

  <a href="{{< ref "../common-parameters/common-parameters#allowWatchBookmarks" >}}">allowWatchBookmarks</a>

- **continue** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#continue" >}}">continue</a>

- **fieldSelector** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldSelector" >}}">fieldSelector</a>

- **labelSelector** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#labelSelector" >}}">labelSelector</a>

- **limit** (*в запиті*): integer

  <a href="{{< ref "../common-parameters/common-parameters#limit" >}}">limit</a>

- **pretty** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#pretty" >}}">pretty</a>

- **resourceVersion** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#resourceVersion" >}}">resourceVersion</a>

- **resourceVersionMatch** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#resourceVersionMatch" >}}">resourceVersionMatch</a>

- **sendInitialEvents** (*в запиті*): boolean

  <a href="{{< ref "../common-parameters/common-parameters#sendInitialEvents" >}}">sendInitialEvents</a>

- **timeoutSeconds** (*в запиті*): integer

  <a href="{{< ref "../common-parameters/common-parameters#timeoutSeconds" >}}">timeoutSeconds</a>

- **watch** (*в запиті*): boolean

  <a href="{{< ref "../common-parameters/common-parameters#watch" >}}">watch</a>

#### Відповідь {#response-1}

200 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidateList" >}}">LeaseCandidateList</a>): OK

401: Unauthorized

### `list` перелік або перегляд обʼєктів типу LeaseCandidate {#list-list-or-watch-objects-of-kind-leasecandidate-1}

#### HTTP запит {#http-request-2}

GET /apis/coordination.k8s.io/v1alpha1/leasecandidates

#### Параметри {#parameters-2}

- **allowWatchBookmarks** (*в запиті*): boolean

  <a href="{{< ref "../common-parameters/common-parameters#allowWatchBookmarks" >}}">allowWatchBookmarks</a>

- **continue** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#continue" >}}">continue</a>

- **fieldSelector** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldSelector" >}}">fieldSelector</a>

- **labelSelector** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#labelSelector" >}}">labelSelector</a>

- **limit** (*в запиті*): integer

  <a href="{{< ref "../common-parameters/common-parameters#limit" >}}">limit</a>

- **pretty** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#pretty" >}}">pretty</a>

- **resourceVersion** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#resourceVersion" >}}">resourceVersion</a>

- **resourceVersionMatch** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#resourceVersionMatch" >}}">resourceVersionMatch</a>

- **sendInitialEvents** (*в запиті*): boolean

  <a href="{{< ref "../common-parameters/common-parameters#sendInitialEvents" >}}">sendInitialEvents</a>

- **timeoutSeconds** (*в запиті*): integer

  <a href="{{< ref "../common-parameters/common-parameters#timeoutSeconds" >}}">timeoutSeconds</a>

- **watch** (*в запиті*): boolean

  <a href="{{< ref "../common-parameters/common-parameters#watch" >}}">watch</a>

#### Відповідь {#response-2}

200 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidateList" >}}">LeaseCandidateList</a>): OK

401: Unauthorized

### `create` створення LeaseCandidate {#create-create-a-leasecandidate}

#### HTTP запит {#http-request-3}

POST /apis/coordination.k8s.io/v1alpha1/namespaces/{namespace}/leasecandidates

#### Параметри {#parameters-3}

- **namespace** (*в шляху*): string, обовʼязково

  <a href="{{< ref "../common-parameters/common-parameters#namespace" >}}">namespace</a>

- **body**: <a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>, обовʼязково

- **dryRun** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#dryRun" >}}">dryRun</a>

- **fieldManager** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldManager" >}}">fieldManager</a>

- **fieldValidation** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldValidation" >}}">fieldValidation</a>

- **pretty** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#pretty" >}}">pretty</a>

#### Відповідь {#response-3}

200 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>): OK

201 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>): Created

202 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>): Accepted

401: Unauthorized

### `update` заміна вказаного LeaseCandidate {#update-replace-the-specified-leasecandidate}

#### HTTP запит {#http-request-4}

PUT /apis/coordination.k8s.io/v1alpha1/namespaces/{namespace}/leasecandidates/{name}

#### Параметри {#parameters-4}

- **name** (*в шляху*): string, обовʼязково

  name of the LeaseCandidate

- **namespace** (*в шляху*): string, обовʼязково

  <a href="{{< ref "../common-parameters/common-parameters#namespace" >}}">namespace</a>

- **body**: <a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>, обовʼязково

- **dryRun** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#dryRun" >}}">dryRun</a>

- **fieldManager** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldManager" >}}">fieldManager</a>

- **fieldValidation** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldValidation" >}}">fieldValidation</a>

- **pretty** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#pretty" >}}">pretty</a>

#### Відповідь {#response-4}

200 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>): OK

201 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>): Created

401: Unauthorized

### `patch` часткове оновлення вказаного LeaseCandidate {#patch-partially-update-the-specified-leasecandidate}

#### HTTP запит {#http-request-5}

PATCH /apis/coordination.k8s.io/v1alpha1/namespaces/{namespace}/leasecandidates/{name}

#### Параметри {#parameters-5}

- **name** (*в шляху*): string, обовʼязково

  name of the LeaseCandidate

- **namespace** (*в шляху*): string, обовʼязково

  <a href="{{< ref "../common-parameters/common-parameters#namespace" >}}">namespace</a>

- **body**: <a href="{{< ref "../common-definitions/patch#Patch" >}}">Patch</a>, обовʼязково

- **dryRun** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#dryRun" >}}">dryRun</a>

- **fieldManager** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldManager" >}}">fieldManager</a>

- **fieldValidation** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldValidation" >}}">fieldValidation</a>

- **force** (*в запиті*): boolean

  <a href="{{< ref "../common-parameters/common-parameters#force" >}}">force</a>

- **pretty** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#pretty" >}}">pretty</a>

#### Відповідь {#response-5}

200 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>): OK

201 (<a href="{{< ref "../cluster-resources/lease-candidate-v1alpha1#LeaseCandidate" >}}">LeaseCandidate</a>): Created

401: Unauthorized

### `delete` видалення LeaseCandidate {#delete-delete-a-leasecandidate}

#### HTTP запит {#http-request-6}

DELETE /apis/coordination.k8s.io/v1alpha1/namespaces/{namespace}/leasecandidates/{name}

#### Параметри {#parameters-6}

- **name** (*в шляху*): string, обовʼязково

  name of the LeaseCandidate

- **namespace** (*в шляху*): string, обовʼязково

  <a href="{{< ref "../common-parameters/common-parameters#namespace" >}}">namespace</a>

- **body**: <a href="{{< ref "../common-definitions/delete-options#DeleteOptions" >}}">DeleteOptions</a>

- **dryRun** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#dryRun" >}}">dryRun</a>

- **gracePeriodSeconds** (*в запиті*): integer

  <a href="{{< ref "../common-parameters/common-parameters#gracePeriodSeconds" >}}">gracePeriodSeconds</a>

- **pretty** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#pretty" >}}">pretty</a>

- **propagationPolicy** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#propagationPolicy" >}}">propagationPolicy</a>

#### Відповідь {#response-6}

200 (<a href="{{< ref "../common-definitions/status#Status" >}}">Status</a>): OK

202 (<a href="{{< ref "../common-definitions/status#Status" >}}">Status</a>): Accepted

401: Unauthorized

### `deletecollection` видалення колекції LeaseCandidate

#### HTTP запит {#http-request-7}

DELETE /apis/coordination.k8s.io/v1alpha1/namespaces/{namespace}/leasecandidates

#### Параметри {#parameters-7}

- **namespace** (*в шляху*): string, обовʼязково

  <a href="{{< ref "../common-parameters/common-parameters#namespace" >}}">namespace</a>

- **body**: <a href="{{< ref "../common-definitions/delete-options#DeleteOptions" >}}">DeleteOptions</a>

- **continue** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#continue" >}}">continue</a>

- **dryRun** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#dryRun" >}}">dryRun</a>

- **fieldSelector** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#fieldSelector" >}}">fieldSelector</a>

- **gracePeriodSeconds** (*в запиті*): integer

  <a href="{{< ref "../common-parameters/common-parameters#gracePeriodSeconds" >}}">gracePeriodSeconds</a>

- **labelSelector** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#labelSelector" >}}">labelSelector</a>

- **limit** (*в запиті*): integer

  <a href="{{< ref "../common-parameters/common-parameters#limit" >}}">limit</a>

- **pretty** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#pretty" >}}">pretty</a>

- **propagationPolicy** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#propagationPolicy" >}}">propagationPolicy</a>

- **resourceVersion** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#resourceVersion" >}}">resourceVersion</a>

- **resourceVersionMatch** (*в запиті*): string

  <a href="{{< ref "../common-parameters/common-parameters#resourceVersionMatch" >}}">resourceVersionMatch</a>

- **sendInitialEvents** (*в запиті*): boolean

  <a href="{{< ref "../common-parameters/common-parameters#sendInitialEvents" >}}">sendInitialEvents</a>

- **timeoutSeconds** (*в запиті*): integer

  <a href="{{< ref "../common-parameters/common-parameters#timeoutSeconds" >}}">timeoutSeconds</a>

#### Відповідь {#response-7}

200 (<a href="{{< ref "../common-definitions/status#Status" >}}">Status</a>): OK

401: Unauthorized