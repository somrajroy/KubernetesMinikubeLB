# KubernetesMinikubeLB
A load balancer application can be developed & tested in minikube and with some tricks & no extra costs. <br/><br/>
* Clone the repository and navigate to lab-04 folder in Powershell/CLI <br/>
* Command to check clusters in minikube <br/>
  $ minikube profile list <br/>
* Switch to minikube context <br/>
  $ kubectl config use-context minikube <br/>
* Enable NGINX Ingress controller <br/>
  $ minikube addons enable ingress <br/>
* Verify that the NGINX Ingress controller is running <br/>
  $ kubectl get pods -n ingress-nginx <br/>
* Create the Deployment resources in k8s-deployments folder <br/>
  $ kubectl apply -f ./k8s-deployments/ <br/>
* Please list the existing Deployments <br/>
  $ kubectl get deployments <br/>
* Check pods <br/>
  $ kubectl get pods <br/>
* The worker Pod will fail because there is still no connection between the pods <br/>
![image](https://user-images.githubusercontent.com/92582005/201910572-abce9ef8-d551-42d8-82f6-d260311c8c69.png) <br/>
* Create the services <br/>
  $ kubectl apply -f ./k8s-services/ <br/>
* Get the services and you will notice that there is no "External IP" for LoadBalancer is pending because minikube is local. For a CSP there will be an external IP assigned which can be accessed from Internet <br/>
![image](https://user-images.githubusercontent.com/92582005/201911094-7880f6b4-19c0-4fee-99ab-233504c93e7f.png) <br/>
* Check the pods now and the worker pod will be running with restarts. If it is not running the create then delete the deployment and create the worker deployment once again. The YAML file of worker deployment is in folder "k8s-deployments"  <br/>
  $ kubectl get pods <br/>
  ![image](https://user-images.githubusercontent.com/92582005/201911548-9b9ebe69-daf0-41f8-b016-1d8123d90464.png) <br/>
* Now the tricky part. Each LoadBalaner service creates a NodePort service. We can find out by the below command and then view the service in browser using the NodePort service <br/>
  $ minikube service <service-name>
* Run the vote service and it will open in new window and would display the NodePort URL. Give your vote <br/>
  $ minikube service vote <br/>
  ![image](https://user-images.githubusercontent.com/92582005/201912196-a664a3e1-52ce-4ce7-83a5-d00879324bd9.png) <br/>
* Access the "result" service and check the results (it will be automatically opened in new browser): <br/>
  $ minikube service result <br/>
  ![image](https://user-images.githubusercontent.com/92582005/201912676-5759322c-2582-45a1-a5ee-9b24c20540d7.png) <br/>
* Delete Services and deployments <br/>
  $ kubectl delete -f ./k8s-services/ <br/>
  $ kubectl delete -f ./k8s-deployments/ <br/>
* Clean everything <br/>
  $ kubectl delete all --all <br/>
