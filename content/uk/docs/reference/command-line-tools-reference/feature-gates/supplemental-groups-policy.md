---
title: SupplementalGroupsPolicy
content_type: feature_gate
_build:
  list: never
  render: false

stages:
  - stage: alpha
    defaultValue: false
    fromVersion: "1.31"
---
Вмикає підтримку детального контролю SupplementalGroups. Докладні відомості див. у статті [Налаштування детального контролю SupplementalGroups для Podʼа](/uk/docs/tasks/configure-pod-container/security-context/#supplementalgroupspolicy).