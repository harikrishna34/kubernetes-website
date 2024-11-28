---
title: Незмінна інфраструктура
id: immutable-infrastructure
date: 2024-03-25
full_link:
short_description: >
  Незмінна інфраструктура — це компʼютерна інфраструктура (віртуальні машини, контейнери, мережеві пристрої), яка не може бути змінена після розгортання.

aka:
- Immutable Infrastructure
tags:
- architecture
---

Незмінна інфраструктура — це компʼютерна інфраструктура (віртуальні машини, контейнери, мережеві пристрої), яка не може бути змінена після розгортання.

<!--more-->

Незмінність може бути забезпечена автоматизованим процесом, який переписує несанкціоновані зміни або через систему, яка в першу чергу не дозволяє змін. {{< glossary_tooltip text="Контейнери" term_id="container" >}} є хорошим прикладом незмінної інфраструктури, оскільки постійні зміни в контейнерах можуть бути внесені лише шляхом створення нової версії контейнера або перестворення поточного контейнера з його образу.

Запобігаючи або виявляючи несанкціоновані зміни, незмінні інфраструктури спрощують ідентифікацію та помʼякшення ризиків безпеки. Управління такою системою стає набагато очевиднішим, оскільки адміністратори можуть робити припущення що до неї. Вони знають, що ніхто не припустився помилки або змін, про які вони забули сповістити. Незмінна інфраструктура йде рука об руку з інфраструктурою як кодом, де вся автоматизація, необхідна для створення інфраструктури, зберігається у системі контролю версій (такій як Git). Ця комбінація незмінності та контролю версій означає, що є надійний лог аудиту кожної санкціонованої зміни в системі.