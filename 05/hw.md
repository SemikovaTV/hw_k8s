# Домашнее задание к занятию «Сетевое взаимодействие в K8S. Часть 2» - Семикова Т.В. FOPS-9

### Задание 1. Создать Deployment приложений backend и frontend

1. Создать Deployment приложения _frontend_ из образа nginx с количеством реплик 3 шт.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/27.jpg)
![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/28.jpg)

  [frontend.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/05/frontend.yml)

2. Создать Deployment приложения _backend_ из образа multitool.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/29.jpg)
![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/30.jpg)

  [backend.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/05/backend.yml)

3. Добавить Service, которые обеспечат доступ к обоим приложениям внутри кластера.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/31.jpg)

  [front_svc.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/05/front_svc.yml)

  [back_svc.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/05/back_svc.yml)

4. Продемонстрировать, что приложения видят друг друга с помощью Service.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/32.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/33.jpg)

5. Предоставить манифесты Deployment и Service в решении, а также скриншоты или вывод команды п.4.

------

### Задание 2. Создать Ingress и обеспечить доступ к приложениям снаружи кластера

1. Включить Ingress-controller в MicroK8S.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/34.jpg)

2. Создать Ingress, обеспечивающий доступ снаружи по IP-адресу кластера MicroK8S так, чтобы при запросе только по адресу открывался _frontend_ а при добавлении /api - _backend_.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/38.jpg)

  [ingress.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/05/ingress.yml)

3. Продемонстрировать доступ с помощью браузера или `curl` с локального компьютера.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/37.jpg)


4. Предоставить манифесты и скриншоты или вывод команды п.2.

------
