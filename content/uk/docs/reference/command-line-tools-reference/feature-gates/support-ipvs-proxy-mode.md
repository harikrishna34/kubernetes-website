---
# Removed from Kubernetes
title: SupportIPVSProxyMode
content_type: feature_gate

_build:
  list: never
  render: false

stages:
  - stage: alpha 
    defaultValue: false
    fromVersion: "1.8"
    toVersion: "1.8"
  - stage: beta 
    defaultValue: false
    fromVersion: "1.9"
    toVersion: "1.9"    
  - stage: beta 
    defaultValue: true
    fromVersion: "1.10"
    toVersion: "1.10"
  - stage: stable
    defaultValue: true
    fromVersion: "1.11"
    toVersion: "1.20"    

removed: true
---
Вмикає балансування навантаження сервісів у кластері за допомогою IPVS. Докладні відомості див. у статті [проксі-сервери](/uk/docs/reference/networking/virtual-ips/).