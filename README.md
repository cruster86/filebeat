### Структура репозитория

Настройки для кластеров находятся в:
```
  - chart/${CI_ENVIRONMENT_SLUG}/conf/${CLUSTER_NAME}/values.yaml
  - chart/${CI_ENVIRONMENT_SLUG}/conf/${CLUSTER_NAME}/config.yaml
```
Конфигурация деплоя находится в: `.gitlab-ci.yaml`

Особенности установки:

  - Дополнительно создаётся psp-конфигурация. Она передаётся в правила для ClusterRole через праметр clusterRoleRules.
  - psp-конфигурация активируется через параметр:`podSecurityPolicy: true`
  - Важно: для k8s >= 1.25 необходимо выставить значение `podSecurityPolicy: false`
---

Upstream проект: https://github.com/elastic/helm-charts/tree/main/filebeat