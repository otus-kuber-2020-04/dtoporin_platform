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
