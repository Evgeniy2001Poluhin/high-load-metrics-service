# High-Load Metrics Service (Go + Kubernetes)

**Go сервис с аналитикой нагрузки (rolling avg 50, z-score>2σ)**

## Результаты теста
ab -n 10000 -c 50 → RPS: 27.79, Failed: 0, ANOMALY: RPS 15000


## Архитектура
Go-service → Redis (master+3rep) → HPA (CPU>70%) → Prometheus

## Запуск
```bash
minikube start --cpus=2 --memory=4g
helm install redis bitnami/redis
kubectl apply -f k8s/
```

### 2. ФИНАЛЬНЫЕ 3 СКРИНА (15 минут)

Выполни **ПО ПОРЯДКУ** и **НЕ ЗАКРЫВАЙ** терминалы:

```bash
# 1. Все ресурсы разом
kubectl get all

# 2. Deployment + Services  
kubectl get deploy,svc

# 3. Minikube dashboard (открой в браузере и скринни)
minikube dashboard
```