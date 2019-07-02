To build the docker image from docker file.

docker build -it tomcatimage .

To run a image as a container run the docker-compose.yml file 

*********************************************************************************************************************
docker-compose -f dokcer-compose.yml up -d 

or

Kompose is a conversion tool for Docker Compose to container orchestrators such as Kubernetes (or OpenShift)

Installing kompose in ubuntu machine:
# Linux
Step1: curl -L https://github.com/kubernetes/kompose/releases/download/v1.17.0/kompose-linux-amd64 -o kompose
Step2: chmod +x kompose
Step3: sudo mv ./kompose /usr/local/bin/kompose

After installation run below commands to convert docker compose file to kubernetes yaml file.

- kompose convert -f docker-compose.yml

One deployment.yaml, service.yaml and presistent-volumes.yaml will be created.

With that yaml files we can deploy pods and services in kubernetes environment.

*********************************************************************************************************************

To deploy run the below steps from kubernetes master:

To run tomcat in pods-
kubectl apply -f tomcat-claim0-presistentvolumeclaim.yaml
kubectl apply -f tomcat-service.yaml
kubectl apply -f tomcat-deployment.yaml

To run mongodb in pods-
kubectl apply -f mongo-deployment.yaml
kubectl apply -f mongo-service.yaml

**********************************************************************************************************************

To check the pods are up and running 

kubectl get pods (or) kubectl get pods --all-namespaces -o wide

To check the services are up and running

kubectl get services (or) kubectl get services --all-namespaces -o wide

*********************************************************************************************************************