# Домашнее задание к занятию «Запуск приложений в K8S»

------

### Задание 1. Создать Deployment и обеспечить доступ к репликам приложения из другого Pod

1. Создать Deployment приложения, состоящего из двух контейнеров — nginx и multitool. Решить возникшую ошибку.

Ошибку удалось избежать, поскольку в вспомогательных материалах прочла, что 80 и 443 порт занимает nginx, поэтому сразу заменила порт

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/9.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/10.jpg)


2. После запуска увеличить количество реплик работающего приложения до 2.
3. Продемонстрировать количество подов до и после масштабирования.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/11.jpg)

[deployment.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/03/deployment.yml)

4. Создать Service, который обеспечит доступ до реплик приложений из п.1.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/13.jpg)

[service.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/03/sevice.yml)

5. Создать отдельный Pod с приложением multitool и убедиться с помощью `curl`, что из пода есть доступ до приложений из п.1.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/12.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/14.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/15.jpg)

[multitool.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/03/multitool.yml)

------

### Задание 2. Создать Deployment и обеспечить старт основного контейнера при выполнении условий

1. Создать Deployment приложения nginx и обеспечить старт контейнера только после того, как будет запущен сервис этого приложения.
2. Убедиться, что nginx не стартует. В качестве Init-контейнера взять busybox.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/16.jpg)

4. Создать и запустить Service. Убедиться, что Init запустился.
5. Продемонстрировать состояние пода до и после запуска сервиса.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/18.jpg)

[deployment_init.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/03/deployment_init.yml)

[init-svc.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/03/init-svc.yml)

------
