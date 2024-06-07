# Домашнее задание к занятию «Хранение в K8s. Часть 1» Семикова Т.В. FOPS-9

### Цель задания

В тестовой среде Kubernetes нужно обеспечить обмен файлами между контейнерам пода и доступ к логам ноды.

------

### Задание 1 

**Что нужно сделать**

Создать Deployment приложения, состоящего из двух контейнеров и обменивающихся данными.

1. Создать Deployment приложения, состоящего из контейнеров busybox и multitool.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/39.jpg)

2. Сделать так, чтобы busybox писал каждые пять секунд в некий файл в общей директории.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/41.jpg)

3. Обеспечить возможность чтения файла контейнером multitool.
4. Продемонстрировать, что multitool может читать файл, который периодоически обновляется.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/40.jpg)

5. Предоставить манифесты Deployment в решении, а также скриншоты или вывод команды из п. 4.

[deployment.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/06/deployment.yml)

------

### Задание 2

**Что нужно сделать**

Создать DaemonSet приложения, которое может прочитать логи ноды.

1. Создать DaemonSet приложения, состоящего из multitool.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/42.jpg)

2. Обеспечить возможность чтения файла `/var/log/syslog` кластера MicroK8S.
3. Продемонстрировать возможность чтения файла изнутри пода.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/43.jpg)

4. Предоставить манифесты Deployment, а также скриншоты или вывод команды из п. 2.

[daemonset.yml](https://github.com/SemikovaTV/hw_k8s/blob/main/06/daemonset.yml)

------
