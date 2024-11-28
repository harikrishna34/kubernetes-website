---
title: KubeletCredentialProviders
content_type: feature_gate
_build:
  list: never
  render: false

stages:
  - stage: alpha 
    defaultValue: false
    fromVersion: "1.20"
    toVersion: "1.23"
  - stage: beta 
    defaultValue: true
    fromVersion: "1.24"
    toVersion: "1.25"
  - stage: stable
    defaultValue: true
    fromVersion: "1.26"
    toVersion: "1.28"

removed: true
---
Вмикає постачальників облікових даних для kubelet exec для отримання облікових даних для отримання образів.