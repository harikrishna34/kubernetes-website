---
# Removed from Kubernetes
title: CustomResourceWebhookConversion
content_type: feature_gate

_build:
  list: never
  render: false

stages:
  - stage: alpha 
    defaultValue: false
    fromVersion: "1.13"
    toVersion: "1.14"
  - stage: beta 
    defaultValue: true
    fromVersion: "1.15"
    toVersion: "1.15"    
  - stage: stable
    defaultValue: true
    fromVersion: "1.16"
    toVersion: "1.18"

removed: true  
---
Вмикає конверсію на основі webhook для ресурсів, створених з [CustomResourceDefinition](/uk/docs/concepts/extend-kubernetes/api-extension/custom-resources/).