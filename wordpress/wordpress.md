# wordpress

download

```sh
$ wget http://twoseven.kr/weekend/examples.tar
$ tar -xf examples.tar
```

pv

```sh
$ kubectl create -f mysql-pv.yaml
$ kubectl create -f wp-pv.yaml
$ kubectl get pv
```

pvc
```sh
$ kubectl create -f mysql-pvc.yaml
$ kubectl create -f wp-pvc.yaml
$ kubectl get pvc
```

mysql

```sh
$ kubectl create -f mysql.yaml
$ kubectl get pods -o wide
```

debugging

```sh
$ kubectl logs mysql-5df965d46d-hwz7t
$ kubectl describe pod mysql-5df965d46d-hwz7t
$ kubectl delete deployments.apps mysql --force
```

wordpress

```sh
$ kubectl create -f wp.yaml
$ kubectl get pods -o wide
```

외부에서 접속하기 위해서 서비스 실행

```sh
$ kubectl create -f mysql-service.yaml
$ kubectl create -f wp-service.yaml
$ kubectl get svc
NAME        TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
mysql       ClusterIP   10.108.164.17    <none>        3306/TCP       6m27s
wordpress   NodePort    10.100.196.239   <none>        80:30025/TCP   4m19s
```

사이트 접속

- <http://192.168.100.30:30025/>

```sh
$ cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
192.168.100.10 master.example.com master
192.168.100.20 node1.example.com node1
192.168.100.30 node2.example.com node2
```

## Secrets

```sh
$ kubectl create secret generic db-pw --from-literal password=mypass --from-literal user_password=userpass
$ kubectl get secrets
$ kubectl describe secrets db-pw
Name:         db-pw
Namespace:    testns
Labels:       <none>
Annotations:  <none>

Type:  Opaque

Data
====
password:       6 bytes
user_password:  8 bytes
```

컨피그맵 조회

```sh
$ kubectl describe configmaps config-db
```

