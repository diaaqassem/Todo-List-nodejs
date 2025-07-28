

📝 To-Do List nodeJs

The to-do list application is a web-based application that allows users to create and manage a list of tasks. The user interface consists of a form to add new tasks, a list of all tasks, and controls to mark tasks as complete or delete them.

To create the application, Node.js is used to set up the server and handle the logic of the application. Express.js is used to create the routes for the application, allowing the user to interact with the application through a web browser. EJS is used to create the views for the application, allowing the user to see the list of tasks and the form to add new tasks. CSS is used to style the application, making it visually appealing and easy to use.

MongoDB and Mongoose are used to store the tasks in a database, allowing the user to add, delete, and update tasks as needed. Nodemon is used to monitor changes to the code and automatically restart the server, making it easy to develop and test the application.

When the user adds a new task using the form, Node.js and Express.js handle the request and store the task in the database using Mongoose. When the user views the list of tasks, EJS displays the tasks from the database in a list on the web page. When the user marks a task as complete or deletes a task, Node.js and Express.js handle the request and update the database using Mongoose.

Overall, the todo list application using Node.js, Express.js, EJS, CSS, JavaScript, MongoDB, Mongoose, and Nodemon can be a great way to create a functional and interactive web application that allows users to manage their tasks online. With the right combination of technologies, it is possible to create an application that is both functional and aesthetically pleasing, making it easy for users to manage their tasks in a convenient and efficient way.

Technologies Used: NodeJS, ExpressJS, EJS, CSS, JavaScript, Nodemon, MongoDB, Mongoose.
## Demo

Under process...

## Features

- Create, Update, and Delete Tasks: Enable users to create new tasks, update existing tasks (e.g., mark as completed, edit task details), and delete tasks they no longer need.
- Task Categories provides Implement the ability for users to categorize their tasks into different categories (e.g., work, personal, shopping) or assign labels/tags to tasks for better organization and filtering.
- MongoDb to store your the user data
## Run Locally

This project implements a full CI/CD pipeline, automated infrastructure provisioning, and containerized deployment for the **Todo-List-nodejs** application.

---

## ** Part 1 – Docker & GitHub Actions**

### **1. Clone the Repository**

```bash
git clone https://github.com/diaaqassem/Todo-List-nodejs
cd Todo-List-nodejs
```

### **2. Configure `.env`**

* Update the `.env` file with **your own MongoDB database connection**.

### **3. Dockerization**

* **Files:**

  * `Dockerfile` → root directory
  * `.dockerignore` → root directory

### **4. CI Pipeline with GitHub Actions**

* **Workflow file location:** `.github/workflows/docker-build-push.yml`
* Adds a CI pipeline that builds the image and pushes it to a **private Docker registry** whenever changes are pushed to the `master` branch.
  * Generate Token For EC2 instance

---

## ** Part 2 – VM Setup Conf in EC2 instance by VM on Local by Using Ansible**

* in **Linux VM** (AWS EC2).
* Add your **public SSH key** to `/home/ec2-user/.ssh/authorized_keys`.

### **2. Ansible Configuration**

* **Directory:** `ansible/`

  * `hosts` → contains the VM’s IP.
  *  `ansible.cfg` → contain conf.
  * `playbook.yml` → installs and configures Docker on the VM (amazon linux).

### **3. Run the Playbook**

```bash
cd ansible
ansible-playbook -i playbook.yml
```

---

## ** Part 3 – Docker Compose & Auto Update**

### **1. Deploy Application**

* **Directory:** `docker-compose/`

  * `docker-compose.yml` → defines the application and health checks.

### **2. Run the Application**

```bash
cd docker-compose
docker compose up -d
```

### **3. Auto Updates**

* A **cron job** checks for new image updates every 10 minutes:

```
*/10 * * * * cd "/home/ec2-user/Todo-List-nodejs/docker-compose/" && docker compose pull && docker compose up -d
```

* Cron job is lightweight, simple, and does not require additional containers.
* or using tool **Watchtower**.

---

## ** Part 4 – Bonus: Kubernetes + ArgoCD**

### **1. Install Kubernetes**

### **2. Kubernetes Manifests**

* **Directory:** `k8s/`

  * `deployment.yaml` → defines the application deployment.
  * `service.yaml` → exposes the service via NodePort.

### **3. Apply Kubernetes Manifests**

```bash
kubectl apply -f k8s/
```

### **4. (Optional) ArgoCD for Continuous Delivery**

* Install ArgoCD in the cluster.
* Connect it to the GitHub repo to continuously sync Kubernetes manifests.
* **Application file:** `k8s/application.yaml`.

---

---

### ****

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

