Odoo on kubernetes
---

See what [Odoo](https://github.com/odoo/odoo) is.  
This repository is a showcase deployment of Odoo on a Kubernetes cluster using
[minikube](https://github.com/kubernetes/minikube).  
See repo instructions for setting up minikube.  

#### Running the example
Download a [release of minikube](https://github.com/kubernetes/minikube/releases).  

```
minikube start

Starting local Kubernetes cluster...
```

```
kubectl apply -f odoo.yaml

service "odoo-db" created
deployment "odoo-db" created
service "odoo-shop" created
deployment "odoo-shop" created
```

Wait for the pods to start before accessing the application.  
```
kubectl get po

NAME                         READY     STATUS              RESTARTS   AGE
odoo-db-3075219300-nx0kw     0/1       ContainerCreating   0          3s
odoo-shop-2676823603-s46lz   0/1       ContainerCreating   0          3s

kubectl get po

NAME                         READY     STATUS    RESTARTS   AGE
odoo-db-3075219300-nx0kw     1/1       Running   0          1m
odoo-shop-2676823603-s46lz   1/1       Running   0          1m
```

When the pods are ready, you can access the frontend service in the browser.  
```
minikube service odoo-shop

Opening kubernetes service default/odoo-shop in default browser...
```
###### NOTE:

When accessing the service the first time, Odoo starts creating its static files and tries to connect to the database. This might take a while, to see the progress you can tail the logs of the pod. Replace `odoo-shop-2676823603-s46lz` with the container name returned by `kubectl get po` and see the initialization progress.

```
kubectl logs -f odoo-shop-2676823603-s46lz
```


The browser will open with the following page, fill in the details for test data and remember to check `Load demonstration data`.  

![alt text](assets/odoo_admin.png)

You can now start hacking away at your new ERP solution.

![alt text](assets/odoo_apps.png)
