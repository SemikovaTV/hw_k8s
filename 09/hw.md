# Домашнее задание к занятию «Управление доступом»

### Цель задания

В тестовой среде Kubernetes нужно предоставить ограниченный доступ пользователю.

------

### Инструменты / дополнительные материалы, которые пригодятся для выполнения задания

1. [Описание](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) RBAC.
2. [Пользователи и авторизация RBAC в Kubernetes](https://habr.com/ru/company/flant/blog/470503/).
3. [RBAC with Kubernetes in Minikube](https://medium.com/@HoussemDellai/rbac-with-kubernetes-in-minikube-4deed658ea7b).

------

### Задание 1. Создайте конфигурацию для подключения пользователя

1. Создайте и подпишите SSL-сертификат для подключения к кластеру.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/1.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/2.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/3.jpg)

2. Настройте конфигурационный файл kubectl для подключения.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/4.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/5.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/6.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/7.jpg)

3. Создайте роли и все необходимые настройки для пользователя.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/8.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/9.jpg)

4. Предусмотрите права пользователя. Пользователь может просматривать логи подов и их конфигурацию (`kubectl logs pod <pod_id>`, `kubectl describe pod <pod_id>`).

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/10.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/11.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/12.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/13.jpg)

5. Предоставьте манифесты и скриншоты и/или вывод необходимых команд.

[deployment.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/09/deployment.yml)

[role.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/09/role.yml)

[rolebinding.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/09/rolebinding.yml)

------
