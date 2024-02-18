---
title: Network Policy
id: network-policy
date: 2018-04-12
short_description: >
  Специфікація того, як дозволяється взаємодія групам Podʼів між собою та із іншими мережевими точками.

aka: 
- Мережева політика
tags:
- networking
- architecture
- extension
---
Специфікація того, як дозволяється взаємодія групам Podʼів між собою та із іншими мережевими точками.

<!--more--> 

Мережеві політики дозволяють вам декларативно налаштовувати, які Podʼи мають право підключатися одне до одного, які простори імен мають право взаємодіяти та більш конкретно, до яких портів слід застосовувати кожну політику. Ресурси `NetworkPolicy` використовують мітки для вибору Podʼів та визначення правил, які вказують, який трафік дозволяється обраним Podʼам. Мережеві політики реалізовані за допомогою підтримуваного мережевого втулка, який надає постачальник мережі. Зверніть увагу, що створення мережевого ресурсу без контролера для його виконання не матиме ефекту.