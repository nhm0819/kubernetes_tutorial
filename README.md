# kubernetes_tutorial
<br>

- docker build
```
docker build -t nhm0819/kube-tutorial .
```
<br>

- docker hub에 등록(login 필요)
```
docker push nhm0819/kube-tutorial
```
<br>

- kubernetes dashboard   
참조 : https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md
```
kubectl apply -f dashboard-adminuser.yaml  
kubectl apply -f cluster-role-binding .yaml  
kubectl proxy
```
<br>  

- token 생성  
```
kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"
```
<br>  

- kubernetes 구성요소 만들기  
pod.yaml 로 pod 생성  
service.yaml 로 service 생성  
<br>

- port forwarding
```
kubectl port-forward service/hello-svc 8200:8200
```

localhost:8200 접속 --> Hello World
