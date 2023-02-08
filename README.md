### Структура репозитория

Настройки для кластеров находятся в:

  - deploy/helm/${CI_ENVIRONMENT_SLUG}/conf/${CLUSTER_NAME}/values.yaml
  - deploy/helm/${CI_ENVIRONMENT_SLUG}/conf/${CLUSTER_NAME}/config.yaml

Конфигурация деплоя находится в: `.gitlab-ci.yaml`

Особенности установки:

- кластер Sirius:
  
  включить ```managedServiceAccount: true``` для создания service account, role, role binding
  
---

Upstream проект: https://github.com/elastic/helm-charts/tree/main/filebeat


