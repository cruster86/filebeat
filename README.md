**Установить релиз:**

```bash
helm install --name filebeat-prod --namespace filebeat-prod helm/filebeat-prod/
helm install --name filebeat-stage --namespace filebeat-stage helm/filebeat-stage/
```

**Обновить релиз:**

```bash
helm upgrade --install filebeat-prod --namespace filebeat-prod helm/filebeat-prod/
helm upgrade --install filebeat-stage --namespace filebeat-stage helm/filebeat-stage/
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

Настройки `filebeatConfig` находятся в `values.yaml`