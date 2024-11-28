---
title: ServerSideApply
content_type: feature_gate
_build:
  list: never
  render: false

stages:
  - stage: alpha 
    defaultValue: false
    fromVersion: "1.14"
    toVersion: "1.15"
  - stage: beta
    defaultValue: true
    fromVersion: "1.16"  
    toVersion: "1.21" 
  - stage: stable
    defaultValue: true
    fromVersion: "1.22"  
---
Вмикає функцію [Server Side Apply (SSA)](/uk/docs/reference/using-api/server-side-apply/) на сервері API.