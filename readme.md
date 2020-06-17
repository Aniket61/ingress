kubectl create deployment test1 --image=docker.io/httpd
    2  kubectl create deployment test2 --image=docker.io/httpd
    3  kubectl expose deployment test1 --port=80
    4  kubectl expose deployment test2 --port=80
    5  kubectl get pod s
    6  kubectl get pods
    7  kubectl exec -it test1-67574b569f-5sp5g bash
    8  kubectl exec -it test2-5f87cbc9b4-pk5vg bash
    9  kubectl get pods -o wide
   10  curl 10.244.1.4
   11  curl 10.244.1.5
   12  history
   13  curl 10.244.1.5
   14  kubectl get pods -o wide
   15  curl 10.244.1.4
   16  kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-0.31.1/deploy/static/provider/baremetal/deploy.yaml
   17  kubectl get all -n ingress-nginx
   18  kubectl get pods -n kube-system
   19  kubectl delete pod katakatacoda-cloud-provider-58f89f7d9-9z99xcoda-cloud-provider-58f89f7d9-9z99x --nn kube-system
   20  kubectl get pods -n kube-system
    
    
    cat ingrule.yml
    
    
apiVersion: networking.k8s.io/v1beta1  ### if it is v1.13 you can use extensions/v1beta1
kind: Ingress
metadata:
  name: myrule1
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - http:
      paths:
      - path: /app1
        backend:
          serviceName: test2
          servicePort: 80

master $ kubectl create -f ingrule.yml
