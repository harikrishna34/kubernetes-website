---
title: MultiCIDRServiceAllocator
content_type: feature_gate
_build:
  list: never
  render: false

stages:
  - stage: alpha 
    defaultValue: false
    fromVersion: "1.27"
    toVersion: "1.30"
  - stage: beta
    defaultValue: false
    fromVersion: "1.31"
---
Відстежуйте розподіл IP-адрес для IP кластера сервісів за допомогою обʼєктів IPAddress.