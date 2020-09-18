# dockerlibraryk8s
同步k8s镜像

# how to use
## 方法一
开启本地仓库
```
microk8s.enable registry
```
pull镜像
```
docker pull 516249940/busybox:latest
```
tag镜像
```
docker tag 516249940/busybox:latest localhost:32000/busybox:latest
```
push镜像
```
docker push localhost:32000/lbusybox:latest
```
最后修改yml 镜像
kubectl edit pod xxx

## 方法二
```
docker pull 516249940/busybox
docker tag 516249940/busybox:latest k8s.gcr.io/busybox:latest
docker save k8s.gcr.io/busybox:latest >  k8s.gcr.io/busybox.tar 
microk8s.ctr --namespace  k8s.io image import   busybox.tar 
```
最后修改yml 镜像
kubectl edit pod xxx
