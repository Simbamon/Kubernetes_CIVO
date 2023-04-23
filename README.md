# Kubernetes CIVO

## Setting up the fast-api app
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