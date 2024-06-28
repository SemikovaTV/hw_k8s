# Домашнее задание к занятию «Установка Kubernetes»

### Цель задания

Установить кластер K8s.

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. [Инструкция по установке kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/).
2. [Документация kubespray](https://kubespray.io/).

-----

### Задание 1. Установить кластер k8s с 1 master node

1. Подготовка работы кластера из 5 нод: 1 мастер и 4 рабочие ноды.
2. В качестве CRI — containerd.
3. Запуск etcd производить на мастере.
4. Способ установки выбрать самостоятельно.

------
### Ответ:

Задание буду выполнять при помощи kubespray по инструкции, представленной в лекции:

* Устанавливаю необходимые пакеты, kubespray и ansible:

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/12/img/1.jpg)

```bash
stv@kube:~$ ansible --version
ansible [core 2.16.8]
  config file = None
  configured module search path = ['/home/stv/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/stv/.local/lib/python3.11/site-packages/ansible
  ansible collection location = /home/stv/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.11.9 (main, Apr  6 2024, 17:59:24) [GCC 11.4.0] (/usr/bin/python3.11)
  jinja version = 3.0.3
  libyaml = False
```
* Передаю адреса нод и формирую файл hosts.yaml
```bash
stv@kube:~/kubespray$ cp -rfp inventory/sample inventory/myclaster
stv@kube:~/kubespray$ declare -a IPS=(10.0.0.15 10.0.0.31 10.0.0.28 10.0.0.38 10.0.0.26)
stv@kube:~/kubespray$ CONFIG_FILE=inventory/myclaster/hosts.yaml python3.11 contrib/inventory_builder/inventory.py ${IPS[@]}
DEBUG: Adding group all
DEBUG: Adding group kube_control_plane
DEBUG: Adding group kube_node
DEBUG: Adding group etcd
DEBUG: Adding group k8s_cluster
DEBUG: Adding group calico_rr
DEBUG: adding host node1 to group all
DEBUG: adding host node2 to group all
DEBUG: adding host node3 to group all
DEBUG: adding host node4 to group all
DEBUG: adding host node5 to group all
DEBUG: adding host node1 to group etcd
DEBUG: adding host node2 to group etcd
DEBUG: adding host node3 to group etcd
DEBUG: adding host node1 to group kube_control_plane
DEBUG: adding host node2 to group kube_control_plane
DEBUG: adding host node1 to group kube_node
DEBUG: adding host node2 to group kube_node
DEBUG: adding host node3 to group kube_node
DEBUG: adding host node4 to group kube_node
DEBUG: adding host node5 to group kube_node
```
* Редактирую автоконфигурацию файла hosts.yaml под параметры задания:
```yaml
all:
  hosts:
    node1:
      ansible_host: 10.0.0.12
      ip: 10.0.0.12
      access_ip: 10.0.0.12
    node2:
      ansible_host: 10.0.0.31
      ip: 10.0.0.31
      access_ip: 10.0.0.31
    node3:
      ansible_host: 10.0.0.28
      ip: 10.0.0.28
      access_ip: 10.0.0.28
    node4:
      ansible_host: 10.0.0.38
      ip: 10.0.0.38
      access_ip: 10.0.0.38
    node5:
      ansible_host: 10.0.0.26
      ip: 10.0.0.26
      access_ip: 10.0.0.26
  children:
    kube_control_plane:
      hosts:
        node1:
    kube_node:
      hosts:
        node1:
        node2:
        node3:
        node4:
        node5:
    etcd:
      hosts:
        node1:
    k8s_cluster:
      children:
        kube_control_plane:
        kube_node:
    calico_rr:
      hosts: {}
```
Запускаю playbook:
```bash
stv@kube:~/kubespray$ ansible-playbook -i inventory/myclaster/hosts.yaml cluster.yml -b -v &
```
Вижу что playbook завершился успешно

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/12/img/2.jpg)

Иду на master-ноду и проверяю ноды:

![ad](https://github.com/SemikovaTV/hw_k8s/blob/main/12/img/3.jpg)

Кластер работает, все ноды в состоянии готовности.
