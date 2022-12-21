**Установить релиз:**

```bash
helm install --name filebeat-prod --namespace filebeat-prod deploy/helm/stage/ -f deploy/helm/stage/conf/${CLUSTER_NAME}/values.yaml

helm install --name filebeat-stage --namespace filebeat-stage deploy/helm/prod/ -f deploy/helm/prod/conf/${CLUSTER_NAME}/values.yaml
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
kubectl -n filebeat-prod get secrets sirius-registry -o yaml
kubectl -n filebeat-stage get secrets sirius-registry -o yaml
```
---

Настройки `filebeatConfig` находятся в `deploy/helm/prod/conf/${CLUSTER_NAME}/values.yaml` (для каждого кластера)
