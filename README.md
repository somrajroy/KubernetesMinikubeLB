# KubernetesMinikubeLB
A load balancer application can be developed in minikube and with some tricks. This is for POC's &amp; DEV/Test environments as no costs are incurred (no CSP load balancer is created.) <br/><br/>

* Command to check clusters in minikube <br/>
  $ minikube profile list <br/>
* Switch to minikube context <br/>
  $ kubectl config use-context minikube <br/>
* Enable NGINX Ingress controller <br/>
  $ minikube addons enable ingress <br/>
* Verify that the NGINX Ingress controller is running <br/>
  $ kubectl get pods -n ingress-nginx <br/>

