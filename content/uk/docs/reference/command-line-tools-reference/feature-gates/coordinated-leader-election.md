---
title: CoordinatedLeaderElection
content_type: feature_gate
_build:
  list: never
  render: false

stages:
  - stage: alpha
    defaultValue: false
    fromVersion: "1.31"
---
Вмикає поведінку, що підтримує API LeaseCandidate, а також забезпечує детерміноване обрання лідера для панелі управління Kubernetes.