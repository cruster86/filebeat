<details><summary>Состав проекта:</summary>
    .

    ├── deploy
    │   └── helm
    │       ├── prod
    │       │   ├── Chart.yaml
    │       │   ├── conf
    │       │   │   ├── corp
    │       │   │   │   ├── config.yaml
    │       │   │   │   └── values.yaml
    │       │   │   ├── cpm
    │       │   │   │   ├── config.yaml
    │       │   │   │   └── values.yaml
    │       │   │   ├── sirius
    │       │   │   │   ├── config.yaml
    │       │   │   │   └── values.yaml
    │       │   │   └── univ
    │       │   │   │   ├── config.yaml
    │       │   │       └── values.yaml
    │       │   ├── templates
    │       │   │   ├── _helpers.tpl
    │       │   │   ├── clusterrole.yaml
    │       │   │   ├── clusterrolebinding.yaml
    │       │   │   ├── configmap.yaml
    │       │   │   ├── daemonset.yaml
    │       │   │   ├── deployment.yaml
    │       │   │   ├── role.yaml
    │       │   │   ├── rolebinding.yaml
    │       │   │   ├── secret.yaml
    │       │   │   └── serviceaccount.yaml
    │       │   └── values.yaml
    │       └── stage
    │           ├── Chart.yaml
    │           ├── conf
    │           │   ├── corp
    │           │   │   ├── config.yaml
    │           │   │   └── values.yaml
    │           │   ├── cpm-dev
    │           │   │   ├── config.yaml
    │           │   │   └── values.yaml
    │           │   ├── sirius
    │           │   │   ├── config.yaml
    │           │   │   └── values.yaml
    │           │   └── univ
    │           │       ├── config.yaml
    │           │       └── values.yaml
    │           ├── templates
    │           │   ├── _helpers.tpl
    │           │   ├── clusterrole.yaml
    │           │   ├── clusterrolebinding.yaml
    │           │   ├── configmap.yaml
    │           │   ├── daemonset.yaml
    │           │   ├── deployment.yaml
    │           │   ├── role.yaml
    │           │   ├── rolebinding.yaml
    │           │   ├── secret.yaml
    │           │   └── serviceaccount.yaml
    │           └── values.yaml
    └── scripts
        └── helm_deploy_and_wait.sh
</details>

<details><summary>Настройки:</summary>

  - Настройка конфига: `conf/${CLUSTER_NAME}/config.yaml`
  - Настройка параметров: `conf/${CLUSTER_NAME}/values.yaml`

  - Версия filbeat для stage: `7.17.3`
  - Версия filbeat для prod: `7.17.5`
</details>

---

<details><summary>Установка/обновление/удаление filbeat в "ручном режиме":</summary>

**Установить релиз:**

```bash
helm install --name filebeat-prod --namespace filebeat-prod deploy/helm/stage/ -f deploy/helm/stage/conf/${CLUSTER_NAME}/values.yaml

helm install --name filebeat-stage --namespace filebeat-stage deploy/helm/prod/ -f deploy/helm/prod/conf/${CLUSTER_NAME}/values.yaml
```

**Посмотреть релизы в неймспейсах:**

```bash
helm list --namespace filebeat-prod
helm list --namespace filebeat-stage
```

**Обновить релиз:**

```bash
helm upgrade --install filebeat-prod --namespace filebeat-prod deploy/helm/stage/ -f deploy/helm/stage/conf/${CLUSTER_NAME}/values.yaml

helm upgrade --install filebeat-stage --namespace filebeat-stage deploy/helm/prod/ -f deploy/helm/prod/conf/${CLUSTER_NAME}/values.yaml
```

**Удалить релиз:**

```bash
helm del --purge filebeat-prod

helm del --purge filebeat-stage
``` 

**Секрет для доступ к образам:** 

```bash
kubectl -n filebeat-prod get secret sirius-registry -o yaml
kubectl -n filebeat-stage get secret sirius-registry -o yaml
```
</details>
