# filfilio-assignment
Step 1. create a GKE cluster for Application deployment 

Step 2. setup a client machine and connect to GKE cluster for perform all action on cluster ( use service account json key which have rights to perform required tasks )

Step 3. create the redis deployment/service files for deploy the app on k8s .

Step 4 . first deploy the redis app and expose as ClusterIP ( service type clusterip is the default setting if we did't specify the service type manually ) 
note down the redis service clusterip ( it will need in counter deployment for connection )

Step 5. create the counter application deployment file and expose as NodePort or LoadBalancer
Note : in deployment file use redis service clusterip as REDIS_URL "redis://10.36.5.118"
image= tarunbhardwaj/flask-counter-app

##Adding autoscale and apache benchmark rate change##
A) using below comand to change current status of autoscaler and update minium and maximum Replicas num
(1)#kubectl edit hpa counter
(2)#kubectl edit hpa redis
B) Now we can check pods via below command
#kubectl get pods


Step 6. now deploy the counter application and hit the loadbalancer ip with port "5000"

Final Step : test the application with apache benchmark using below command .

$ab -l -c 100 -t 10 http://http://35.227.90.252:5000
