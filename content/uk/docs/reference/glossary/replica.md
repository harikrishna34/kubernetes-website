---
title: Replica
id: replica
date: 2023-06-11
full_link: 
short_description: >
  Репліки — це копії обʼєктів Pod, які забезпечують доступність, масштабованість і стійкість до відмов за рахунок утримання ідентичних екземплярів.
aka: 
tags:
- fundamental
- workload
---
Копія або дублікат {{< glossary_tooltip text="Podʼу" term_id="pod" >}} або набору обʼєктів Pod. Репліки забезпечують високу доступність, масштабованість і стійкість до відмов
шляхом утримання кількох ідентичних екземплярів обʼєкта Pod.

<!--more-->

У Kubernetes репліки широко використовуються для досягнення бажаного стану застосунку та надійності роботи. Вони дозволяють масштабування робочого навантаження та його розподіл по різних вузлах кластера.

Визначаючи кількість реплік в обʼєкті Deployment або ReplicaSet, Kubernetes переконується, що вказана кількість екземплярів працює, автоматично коригуючи кількість за необхідності.

Управління репліками дозволяє ефективно балансувати навантаження, виконувати поетапні оновлення та забезпечує можливості самовідновлення в кластері Kubernetes.