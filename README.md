# infra-gitops

GitOps-репозиторий для Kubernetes-кластера на базе k3s.

Назначение:
- Декларативное описание всей инфраструктуры кластера через ArgoCD
- Helm values для приложений
- Мониторинг (VictoriaMetrics, VictoriaLogs, Grafana, Alertmanager)
- Секреты зашифрованы через SOPS + age

## Структура

```
argocd/applications/     — Application-ресурсы ArgoCD
apps/                    — values-файлы приложений
monitoring/              — values-файлы мониторинга
```

## Окружения

| Namespace | Модель | Триггер деплоя |
|-----------|--------|----------------|
| animark-dev | Pull | argocd-image-updater (latest) |
| animark-prod | Push | CI → git commit |
| monitoring | Push | git commit |
