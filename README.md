
# This project implements a full CI/CD pipeline, automated infrastructure provisioning, and containerized deployment for the **Todo-List-nodejs** application.
## packages
* git

* docker

* docker-compose

* kubectl (minikube)

* cronie

* ansible (for local vm)

* mongodb




## Part 1 – Docker & GitHub Actions

### 1. Clone the Repository

```bash
git clone https://github.com/diaaqassem/Todo-List-nodejs
cd Todo-List-nodejs
```

### 2. Configure `.env`

* Update the `.env` file with your own MongoDB database connection.

### 3. Dockerization

* Files:

  * `Dockerfile` → root directory
  * `.dockerignore` → root directory

### 4. CI Pipeline with GitHub Actions

* Workflow file location: `.github/workflows/app-ci.yml`
* Adds a CI pipeline that builds the image and pushes it to a private Docker registry** whenever changes are pushed to the `master` branch.
  * Generate Token For EC2 instance

---

##  Part 2 – VM Setup Conf in EC2 instance by VM on Local by Using Ansible

* in Linux VM (AWS EC2).
* Add your public SSH key to `/home/ec2-user/.ssh/authorized_keys`.

### 2. Ansible Configuration

* Directory: `ansible/`

  * `hosts` → contains the VM’s IP.
  *  `ansible.cfg` → contain conf.
  * `playbook.yml` → installs and configures Docker on the VM (amazon linux).

### 3. Run the Playbook

```bash
cd ansible
ansible-playbook playbook.yml
```



## Part 3 – Docker Compose & Auto Update

### 1. Deploy Application

* Directory: `docker-compose/`

  * `docker-compose.yml` → defines the application and health checks.

### 2. Run the Application

```bash
cd docker-compose
docker compose up -d
```

### 3. Auto Updates

* A *cron job* checks for new image updates every 10 minutes:

```
*/10 * * * * cd "/home/ec2-user/Todo-List-nodejs/docker-compose/" && docker compose pull && docker compose up -d
```

* Cron job is lightweight, simple, and does not require additional containers.
* or using tool **Watchtower**.

---

##  Part 4 – Bonus: Kubernetes + ArgoCD

### 1. Install Kubernetes

### 2. Kubernetes Manifests

* Directory: `k8s/`

  * `deployment.yaml` → defines the application deployment.
  * `service.yaml` → exposes the service via NodePort.

### 3. Apply Kubernetes Manifests

```bash
kubectl apply -f k8s/
```

### 4. (Optional) ArgoCD for Continuous Delivery

* Install ArgoCD in the cluster.
* Connect it to the GitHub repo to continuously sync Kubernetes manifests.
* Application file: `k8s/application.yaml`.

---


Prepared as part of the **DevOps Internship Assessment**.

---


## Screenshots

![225232515-4c100b6b-52e4-40f8-a6d4-85e30dc2f5e7](https://github.com/Ankit6098/Todos-nodejs/assets/92246613/487f548f-7ca6-4183-9443-c88c9f79c3f0)
![225232960-da554f1f-ba4a-41f8-9856-edaebe339d76](https://github.com/Ankit6098/Todos-nodejs/assets/92246613/25515d2e-1d72-498d-8044-59a01c6b9127)
![225238829-05433362-5b16-454c-92d5-5e536fe6912e](https://github.com/Ankit6098/Todos-nodejs/assets/92246613/316d15ca-1fe8-4581-80b1-fc316340bba6)
![225239140-226f8eae-d8b8-4055-8a68-d85d523c2422](https://github.com/Ankit6098/Todos-nodejs/assets/92246613/44a0c418-449e-446f-8a8e-3c4e14fca8bf)
![225239221-caf86f3d-ef17-4d18-80a6-c72123ff5444](https://github.com/Ankit6098/Todos-nodejs/assets/92246613/2ee90ab0-95d4-44f4-80ac-b17b088ac1ce)
![225239406-98b7ba7d-df97-4d27-bb66-596a32187d87](https://github.com/Ankit6098/Todos-nodejs/assets/92246613/960ff353-1ce9-4ef8-94e4-10af09184fd2)
![225239841-4b5d77f0-4a54-4339-b6b3-b6a1be6776b5](https://github.com/Ankit6098/Todos-nodejs/assets/92246613/f5ffc3b8-480f-4d11-9a0b-c469e3c17e8e)


---

