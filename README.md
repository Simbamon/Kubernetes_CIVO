# Kubernetes CIVO

## Setting up the fast-api app
### Creating Virtual Environment (Python)
- Type this command in terminal
  ```bash
  $ python -m venv ./venv
  $ ls
  $ source ./venv/bin/activate
  ```
- Install the requirements
  ```bash
  pip install -r requirements.txt
  ```

## Pushing Docker Container to Docker Hub
### Building Docker Image
- Run this command to build image in docker
  ```bash
  docker build -t {DOCKER_UID}/{DOCKER_IMAGE_NAME}:{TAG} .
  ```
- (Optional) If you want to test the build, you can run this following command
  ```bash
  docekr run -p {PORT_NUMBER}:{CONTAINER_PORT_NUMBER} {DOCKER_IMAGE_NAME}
  ```
### Pushing to Docker Hub
- Create repository in Docker Hub
- Login to docker in terminal
- Push the container you just built from the previous step
  ```bash
  docker push {DOCKER_UID}/{DOCKER_IMAGE_NAME}:{TAG}
  ```

## Creating Kubernetes environment
### Launching K8S Cluster
- Visit this [website](https://www.civo.com/) and login
- Launch Kubernetes Cluster
  - Kubernetes Cluster name
  - Nodes (3 for this project)
  - Firewall - Kubernetes access from my IP only
  - Size (Small for this project)
  - CNI (Default for this project)
  - Marketplace (Traefik-v2-nodeport, metrics-server for this project)
- Wait for the Kubernetes Cluster to be provisioned (Takes couple minutes)
### Authenticating to Cluster
- Download Kubeconfig file
- Set environment variable
  ```bash
  export KUBECONFIG={KUBECONFIG_FILE_DIRECTORY}
  ```
- Check the nodes
  ```
  kubectl get nodes
  ```
### Deploy Applicaiton to the Cluster
- Apply the yaml files
  ```bash
  kubectl apply -f .
  ```
- It will set up deployment, service and ingress  
  Check the pods, deployments
- (Optional) Expose the deployment - LoadBalancer
  ```bash
  kubectl expose deployment <YOUR_DEPLOYMENT_NAME> --port=<PORT_NUMBER> --type=LoadBalancer
  ```