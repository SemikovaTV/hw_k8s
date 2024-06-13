# Домашнее задание к занятию «Хранение в K8s. Часть 2»

### Цель задания

В тестовой среде Kubernetes нужно создать PV и продемострировать запись и хранение файлов.

-----
### Задание 1

**Что нужно сделать**

Создать Deployment приложения, использующего локальный PV, созданный вручную.

1. Создать Deployment приложения, состоящего из контейнеров busybox и multitool.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/44.jpg)

2. Создать PV и PVC для подключения папки на локальной ноде, которая будет использована в поде.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/45.jpg)

3. Продемонстрировать, что multitool может читать файл, в который busybox пишет каждые пять секунд в общей директории.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/46.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/47.jpg)

4. Удалить Deployment и PVC. Продемонстрировать, что после этого произошло с PV. Пояснить, почему.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/49.jpg)

5. Продемонстрировать, что файл сохранился на локальном диске ноды. Удалить PV.  Продемонстрировать что произошло с файлом после удаления PV. Пояснить, почему.

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/50.jpg)

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/img/51.jpg)

5. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

------

### Задание 2

**Что нужно сделать**

Создать Deployment приложения, которое может хранить файлы на NFS с динамическим созданием PV.

1. Включить и настроить NFS-сервер на MicroK8S.
```bash
stv@kube:~$ microk8s enable nfs
Infer repository community for addon nfs
Infer repository core for addon helm3
Addon core/helm3 is already enabled
Installing NFS Server Provisioner - Helm Chart 1.4.0

Node Name not defined. NFS Server Provisioner will be deployed on random Microk8s Node.

If you want to use a dedicated (large disk space) Node as NFS Server, disable the Addon and start over: microk8s enable nfs -n NODE_NAME
Lookup Microk8s Node name as: kubectl get node -o yaml | grep 'kubernetes.io/hostname'

Preparing PV for NFS Server Provisioner

persistentvolume/data-nfs-server-provisioner-0 created
"nfs-ganesha-server-and-external-provisioner" already exists with the same configuration, skipping
Release "nfs-server-provisioner" does not exist. Installing it now.
NAME: nfs-server-provisioner
LAST DEPLOYED: Thu Jun 13 13:31:17 2024
NAMESPACE: nfs-server-provisioner
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
The NFS Provisioner service has now been installed.

A storage class named 'nfs' has now been created
and is available to provision dynamic volumes.

You can use this storageclass by creating a `PersistentVolumeClaim` with the
correct storageClassName attribute. For example:

    ---
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: test-dynamic-volume-claim
    spec:
      storageClassName: "nfs"
      accessModes:
        - ReadWriteOnce
      resources:
        requests:
          storage: 100Mi

NFS Server Provisioner is installed

WARNING: Install "nfs-common" package on all MicroK8S nodes to allow Pods with NFS mounts to start: sudo apt update && sudo apt install -y nfs-common
WARNING: NFS Server Provisioner servers by default hostPath storage from a single Node.
```


2. Создать Deployment приложения состоящего из multitool, и подключить к нему PV, созданный автоматически на сервере NFS.
```bash
stv@kube:~/01/07$ kubectl apply -f multitool.yml
deployment.apps/multi unchanged
stv@kube:~/01/07$ kubectl get po -n vol2
NAME                     READY   STATUS    RESTARTS   AGE
multi-6b85c669fb-787kx   0/1     Pending   0          47h
stv@kube:~/01/07$ kubectl get pv -n vol2
NAME                            CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                                                  STORAGECLASS   VOLUMEATTRIBUTESCLASS   REASON   AGE
data-nfs-server-provisioner-0   1Gi        RWO            Retain           Bound    nfs-server-provisioner/data-nfs-server-provisioner-0                  <unset>                          4m42s
```
### Помогите решить проблему, после запуска pvc под не запускается, не могу понять в чем причина
Пишу и запускаю pvc:

```bash
stv@kube:~/01/07$ kubectl apply -f pvc_nfs.yml
persistentvolumeclaim/nfs-pvc unchanged
stv@kube:~/01/07$ kubectl get pv -n vol2
NAME                            CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                                                  STORAGECLASS   VOLUMEATTRIBUTESCLASS   REASON   AGE
data-nfs-server-provisioner-0   1Gi        RWO            Retain           Bound    nfs-server-provisioner/data-nfs-server-provisioner-0                  <unset>                          7m51s
stv@kube:~/01/07$ kubectl get pvc -n vol2
NAME      STATUS    VOLUME   CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
nfs-csi   Pending                                      nfs-csi        <unset>                 47h
nfs-pvc   Pending                                      nfs-csi        <unset>                 47h
stv@kube:~/01/07$ kubectl get po -n vol2
NAME                     READY   STATUS    RESTARTS   AGE
multi-6b85c669fb-787kx   0/1     Pending   0          47h
stv@kube:~/01/07$ kubectl get po -n vol2
NAME                     READY   STATUS    RESTARTS   AGE
multi-6b85c669fb-787kx   0/1     Pending   0          47h
```


3. Продемонстрировать возможность чтения и записи файла изнутри пода. 
4. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

------
