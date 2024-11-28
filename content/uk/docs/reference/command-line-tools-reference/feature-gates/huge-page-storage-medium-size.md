---
# Removed from Kubernetes
title: HugePageStorageMediumSize
content_type: feature_gate

_build:
  list: never
  render: false

stages:
  - stage: alpha 
    defaultValue: false
    fromVersion: "1.18"
    toVersion: "1.18"
  - stage: beta 
    defaultValue: true
    fromVersion: "1.19"
    toVersion: "1.21"    
  - stage: stable
    defaultValue: true
    fromVersion: "1.22"
    toVersion: "1.24"    

removed: true  
---
Увімкніть підтримку декількох розмірів попередньо виділених [величезних сторінок](/uk/docs/tasks/manage-hugepages/scheduling-hugepages/).