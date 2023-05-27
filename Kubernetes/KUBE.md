## KUBERNETES 
___


#### What is Kubernetes?
 * Official Definition  
    -> Open source **container orchestration tool**  
    -> Developed by **GOOGLE**  
    -> Helps you manage containerized applications in different deployment environments  
    >    * physical env  
    >    * cloud env  
    >    * virtual env  
    
 * Problem-Solution case study
    * Why did K8S rise so fast?
    * What problems does it solve?

    -> Trend form monolith to microservices  
    -> Increased usage of containers(100s or 1000s of containers)  
    -> Demand for a proper way of managing those hundreds of containers  

* What features do orchestration tools offer?  
    -> __High Availability__ or no downtime  
    -> __Scalability__ or High Performance  
    -> __Disaster recovery__ - backup and restore (if something happens to data centre then there is a mechanism to get the backup of those data)

### Kubernetes Components  
=======

![alt text][Kube_comp]  
##### Node: 
Physical server or worker machine 

##### Pod:  
![alt text][Comp_pod]
-> Smallest unit of K8s  
-> Abstraction over container(replacable because you can use any container like docker or anything)  
> You can only interact with the Kuberentes layer  

-> Usually 1 application per pod(you can run more than one)  
-> Each pod gets its own IP address (networking layer) can communicate between other pods using these IP address  
-> New IP address on re-creation (due to server or node malfunctions or the application inside the pod gets crashed)  

##### Services and Ingress:  
![alt text][Comp_service]  
-> permanent IP address  
-> lifecycle of pod and service NOT connected so if a pod dies or recreates in this case we can still use service and the IP address  
 
You would also want your service to be accesible to the browser so you want an External service
and you would not want your database to be open service and for that you would create known as internal service.
![alt text][service_external]  
As from the image you can see the url is not very practical one, you would want the ip address of your node ip address and the port number but not a good way, you would want some https(secured) and your own domain name and for that kubernetes has component called **Ingress** 
![alt text][Comp_ingress]  









[Kube_comp]: ./images/Components.png "Kubernetes Components"
[Comp_pod]: ./images/Pod.png "Pod"
[Comp_service]: ./images/service.png "Service"
[Comp_ingress]: ./images/service3.png "Ingress"
[service_external]: (./images/service2.png | width=50%) "Internal External"