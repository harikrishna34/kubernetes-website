---
# Removed from Kubernetes
title: CustomResourceValidation
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
    defaultValue: true
    fromVersion: "1.9"
    toVersion: "1.15"    
  - stage: stable
    defaultValue: true
    fromVersion: "1.16"
    toVersion: "1.18"

removed: true  
---
Вмикає перевірку на основі схеми для ресурсів, створених з [CustomResourceDefinition](/uk/docs/concepts/extend-kubernetes/api-extension/custom-resources/).