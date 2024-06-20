# Домашнее задание к занятию «Helm» - Семикова Т.В.

### Цель задания

В тестовой среде Kubernetes необходимо установить и обновить приложения с помощью Helm.

------

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. [Инструкция](https://helm.sh/docs/intro/install/) по установке Helm. [Helm completion](https://helm.sh/docs/helm/helm_completion/).

------

### Задание 1. Подготовить Helm-чарт для приложения

1. Необходимо упаковать приложение в чарт для деплоя в разные окружения.
2. Каждый компонент приложения деплоится отдельным deployment’ом или statefulset’ом.
3. В переменных чарта измените образ приложения для изменения версии.

### Ответ:
Устанавливаю helm:

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/15.jpg)

Создаю свой helm chart - nginx:

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/16.jpg)

Cоздаю отдельные файлы с переменными для разных окружений и указываю разные версии приложений.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/17.jpg)

[val_app1.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/10/nginx/val_app1.yml)

[val_app2.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/10/nginx/val_app2.yml)

------
### Задание 2. Запустить две версии в разных неймспейсах

1. Подготовив чарт, необходимо его проверить. Запуститe несколько копий приложения.
2. Одну версию в namespace=app1, вторую версию в том же неймспейсе, третью версию в namespace=app2.
3. Продемонстрируйте результат.

### Ответ:
Создаю отдельные namespace для окружений - app1 и app2

Запускаю обе версии приложения в окружении app1:

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/18.jpg)
![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/19.jpg)

Проверяю:

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/20.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/22.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/23.jpg)

Запускаю еще одну версию приложения в окружении app2:

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/21.jpg)

Проверяю версию приложения:

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img2/24.jpg)
