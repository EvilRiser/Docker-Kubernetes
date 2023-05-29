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
****

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
<br> <br> <br>

Now the problem is how to use DB URL since we use DB as some environmnet variable and then build it, if the db name changes then we have to update the ip and again we have to rebuild it and it becomes very tedious process for that we have 
  
##### ConfigMap:  
-> external configuration of your application (like url of database or any other database you use)  
In Kubernetes you just connect this to pod and it will get the data from configmap  
and now once you change your image you don't have to rebuild it  

##### Secret:  
Now you can't store you secret data(user name password/certificates) in plane string format for that you have a service called secrets    
-> used to store secret data  
-> base64 encoded  
 > **_Note_**: The built-in security mechanism is not enabled by default!  

-> Use it as environment variables or as a properties file  

<br> <br>

Now comes the topic of data storage, we might have some data or some data might be generated and what if the server fails it might lose data and that can be problematic and inconvenient. You want something which is consistant and in Kubernetes we have something called Volumes.  

##### Volume:  
-> Storage can be on local machine or some remote or outside of the K8s cluster(cloud storage)  

Now if the pod or DB restarts the data is persisted.  
Consider Storage as an add-on plugin because K8s doesn't manage data persistance, it is your duty to store the backup replicating and managing it.  









[Kube_comp]: ./images/Components.png "Kubernetes Components"
[Comp_pod]: ./images/Pod.png "Pod"
[Comp_service]: ./images/service.png "Service"
[Comp_ingress]: ./images/service3.png "Ingress"
[service_external]: ./images/service2.png  "Internal External"