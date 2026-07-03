# infra-gitops

GitOps-репозиторий для Kubernetes-кластера на базе k3s.

Назначение:
- Декларативное описание всей инфраструктуры кластера через ArgoCD
- Helm chart'ы приложений + environment-specific values
- Мониторинг (VictoriaMetrics, VictoriaLogs, Grafana, Alertmanager)
- Секреты зашифрованы через SOPS + age

## Структура

```
argocd/applications/     — Application-ресурсы ArgoCD
charts/*/                — Helm chart'ы приложений
monitoring/              — values-файлы мониторинга
```

## Окружения

| Namespace | Модель | Триггер деплоя |
|-----------|--------|----------------|
| animark-dev | Pull | argocd-image-updater (latest) |
| animark-prod | Push | CI → git commit |
| monitoring | Push | git commit |
