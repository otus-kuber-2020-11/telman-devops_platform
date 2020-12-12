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

