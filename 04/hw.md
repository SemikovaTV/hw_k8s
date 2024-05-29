# Домашнее задание к занятию «Сетевое взаимодействие в K8S. Часть 1»

### Задание 1. Создать Deployment и обеспечить доступ к контейнерам приложения по разным портам из другого Pod внутри кластера

1. Создать Deployment приложения, состоящего из двух контейнеров (nginx и multitool), с количеством реплик 3 шт.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/19.jpg)

   [deployment.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/04/deployment.yml)

2. Создать Service, который обеспечит доступ внутри кластера до контейнеров приложения из п.1 по порту 9001 — nginx 80, по 9002 — multitool 8080.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/20.jpg)

   [service.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/04/sevice.yml)

3. Создать отдельный Pod с приложением multitool и убедиться с помощью `curl`, что из пода есть доступ до приложения из п.1 по разным портам в разные контейнеры.
4. Продемонстрировать доступ с помощью `curl` по доменному имени сервиса.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/21.jpg)
![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/22.jpg)
![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/23.jpg)

5. Предоставить манифесты Deployment и Service в решении, а также скриншоты или вывод команды п.4.
------

### Задание 2. Создать Service и обеспечить доступ к приложениям снаружи кластера

1. Создать отдельный Service приложения из Задания 1 с возможностью доступа снаружи кластера к nginx, используя тип NodePort.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/24.jpg)

[nodeport.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/04/nodeport.yml)

2. Продемонстрировать доступ с помощью браузера или `curl` с локального компьютера.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/25.jpg)
![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/26.jpg)

3. Предоставить манифест и Service в решении, а также скриншоты или вывод команды п.2.

------
