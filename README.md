# telman-devops_platform
telman-devops Platform repository

# Знакомство с Kubernetes, основные понятия и архитектура
### Домашнее задание
1) Установил minikube
2) Запустил k8s кластер `minikube start`
3) Проверил что кластер работает корректно `kubectl cluster-info`
4) Написал Dockerfile с nginx образом
5) Написал манифест web-pod.yaml и запустил его командой `kubectl apply -f web-pod.yaml`
6) Проверил работоспособность `kubectl get pod web -o yaml` / `kubectl describe pod web`
7) Дописал манифест web-pod.yaml, добавил init sidecar контейнер который копирует файл index.html в контейнер
8) Проверил работоспособность web сервера `kubectl port-forward --address 0.0.0.0 pod/web 8000:8000`
9) Собрал frontend модуль приложения hipster-shop 
10) Запустил в режиме ad-hoc `kubectl run frontend --image 870414/frontend:latest --restart=Never`
11) Сгенерировал манифест с использованием ad-hoc `kubectl run frontend --image 870414/frontend:latest --restart=Never --dryrun -o yaml > frontend-pod.yaml`
12) Нашел и устранил ошибку `environment variable`


# Механика запуска и взаимодействия контейнеров в Kubernetes
### Домашнее задание
1) Установил kind и создал кластер
2) Создал манифест ReplicaSet
3) Создал 2 магифеста Deployment, для frontend и paymentservice
4) Добавил два манифеста, аналог blue-green и Rolling Update
5) Настроил Probes 

# Безопасность и управление доступом
### Домашнее задание
task01
1) Создал Service Account bob, дал ему роль admin в рамках всего кластера
2) Создал Service Account dave без доступа к кластеру

task02
1) Создал Namespace prometheus
2) Создал Service Account carol в этом Namespace
3) Дал всем Service Account в Namespace prometheus возможность делать get, list, watch в отношении Pods всего кластера

task03
1) Создал Namespace dev
2) Создал Service Account jane в Namespace dev
3) Дал jane роль admin в рамках Namespace dev
4) Создал Service Account ken в Namespace dev
5) Дал ken роль view в рамках Namespace dev

# Сетевая подсистема Kubernetes
### Домашнее задание
1) Добавил проверку readinessProbe и livenessProbe для Pod
2) Применил манифест Deployment с 3я репликами
3) Добавил RollingUpdate стратегию для Deployment манифеста
4) Написал Service ClusterIP, включили IPVS, обновили iptables 
```
/tmp/iptables.cleanup

 *nat
 -A POSTROUTING -s 172.17.0.0/16 ! -o docker0 -j MASQUERADE
 COMMIT
 *filter
 COMMIT
 *mangle
 COMMIT

iptables-restore /tmp/iptables.cleanup

iptables --list -nv -t nat
```
5) Установил MetalLB, настроил балансировщик с помощью манифеста ConfigMap
6) Установил "коробочный" ingress-nginx
7) Применил nginx-lb, Headless-сервис, правила Ingress

# Хранение данных в Kubernetes: Volumes, Storages, Statefull-приложения
### Домашнее задание
1) Развернул StatefulSet с MinIO
2) Применил конфигурацию Headless Service, для доступа к minio изнутри кластера
3) Написал и применил Secret манифест, для скрытия "чувствительных" данных