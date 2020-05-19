# dtoporin_platform
dtoporin Platform repository

ДЗ
#1 Разобрался почему pod в namespace kube-system восстановились после удаления.
core-dns - deployment
etcd, kube-apiserver, kube-controller-manager, kube-scheduler - kubelet запускает на master нодах /etc/kubernetes/manifests

#2 Создан  Dockerfile для образа с web-сервисом на 8000 порту
#3 Собран образ и размещен в docker hub dtoporin/my-web-app:1.0
#4 Наиписан манифест для web-pod
#5 В манифест добалено описания для init контейнера
#6 Работа контейнера проверена 
#7 Собран образ frontend из HipsterShop
#8 Запущен образ ad-hoc 
#9* Не запустился из-за отстутствия переменной окружения "environment variable "PRODUCT_CATALOG_SERVICE_ADDR" not set"


ДЗ#2
Kubernetes controllers. ReplicaSet, Deployment, DaemonSet
#1 Создан манифест  frontend-replicaset.yaml 
#2 Не запускался т.к. нехватало селектора - добвил
#3 обновление ReplicaSet не повлекло обновление запущенных pod т.к. replicaset controller не умеет рестартовать запущенные поды при обновлении шаблона, заупщенная версия контейнеров оказалась старой
#4 Аналог blue-green:
  strategy:
      type: RollingUpdate
      rollingUpdate:
        maxSurge: 100%
        maxUnavailable: 0 

#5 Reverse Rolling Update:
  strategy:
      type: RollingUpdate
      rollingUpdate:
        maxSurge: 1
        maxUnavailable: 0

#6 задание ** 
   Добавлен параметр 
     tolerations:
           - operator: "Exists"
   Который дает возможность запуска подов на мастер-нодах
