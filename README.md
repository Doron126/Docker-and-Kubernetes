# **Containerization-with-Docker-and-Kubernetes**
## **Overview**
## **Thecnologies Used**
## **Instructions**
1. Set up an Ubuntu server.
2. Set up Docker enviorement:
   "sudo apt update"
   Set the option to download with https:
     "sudo apt install -y apt-transport-https ca-certificates curl software-properties-common"
   Download and add the Docker key:
     "curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -"
   Adding Docker repository to the sources of the machine:
     "sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   Refresh the repositories:
     "sudo apt update"
   Installing Docker:
     "sudo apt install -y docker-ce"
   Verify that Docker runs properly with hello-world image:
     "sudo docker run hello-world"
3. Pull and Run Nginx on Docker:
   "sudo docker pull nginx"
   "sudo docker run -d -p 80:80 nginx"
   Verify by entering the URL: http://VM-IP

4. Set up K3 with the installation script:
   "curl -sfL https://get.k3s.io | sh -"
   Verify:
   "sudo kubectl get nodes"

5. Deploy nginx containers on Kubernetes pods:
   use the configuration file attached to this Git repository
   "sudo kubectl apply -f nginx-deployment.yaml"

6. Install helm, and Prometheus and Grafana with helm and set them:
   "sudo snap install helm --classic"
   "helm repo add prometheus-community https://prometheus-community.github.io/helm-charts"
   "helm repo add grafana https://grafana.github.io/helm-charts"
   "helm repo update"
   "sudo helm install prometheus prometheus-community/prometheus --kubeconfig /etc/rancher/k3s/k3s.yaml"
   "helm install grafana grafana/grafana"
   Make Prometheus and Grafana accesible to other computers in your enviorement:
     "kubectl patch svc prometheus-server -n default -p '{"spec": {"type": "NodePort"}}'"
   See the port:
     "kubectl get svc prometheus-server -n default"
     "kubectl get svc grafana -n default"





   
