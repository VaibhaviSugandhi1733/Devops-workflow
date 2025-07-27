
```markdown
# 🚀 DevOps CI/CD Workflow: Jenkins + Docker + Ansible + EC2

This project demonstrates a complete **CI/CD pipeline** using:
- 🐙 GitHub (source code repository)
- 🐳 Docker (containerization)
- ☸️ DockerHub (image registry)
- 🧩 Jenkins (automation server)
- 🤖 Ansible (remote configuration management)
- 💻 AWS EC2 (deployment target)

---

## 📌 Project Objective

To automate the full cycle of:
1. Pulling application code from GitHub
2. Building a Docker image
3. Pushing the image to Docker Hub
4. Using Ansible to deploy the containerized app on an EC2 instance

---

## 🧰 Tech Stack

| Tool        | Purpose                            |
|-------------|------------------------------------|
| GitHub      | Version Control                    |
| Jenkins     | Automation Server                  |
| Docker      | Image Building & Containerization  |
| DockerHub   | Image Registry                     |
| Ansible     | Remote Deployment to EC2           |
| EC2 (Ubuntu)| App Hosting Server                 |

---

## 🗂️ Repository Structure

```

devops-workflow/
├── app/
│ └── index.html # Sample web app content (static)
├── Dockerfile # Dockerfile to build the application image
├── Jenkinsfile # CI/CD pipeline definition for Jenkins
├── ansible/
│ ├── deploy.yml # Ansible playbook to deploy app on EC2
│ └── inventory.ini # Inventory file with EC2 IP and SSH info
└── README.md # Project documentation
````

---

## ⚙️ CI/CD Pipeline Workflow

```mermaid
graph LR
A[GitHub Repo Push] --> B[Jenkins Clone Repo]
B --> C[Build Docker Image]
C --> D[Push to DockerHub]
D --> E[Run Ansible Playbook]
E --> F[Deploy Docker Container on EC2]
````

---

## ✅ Step-by-Step Setup

### 1. 🔧 Clone the Project

```bash
git clone https://github.com/VaibhaviSugandhi1733/devops-workflow.git
cd devops-workflow
```

### 2. 🐳 Install & Run Jenkins (Docker)

```bash
docker run -d --name jenkins \
  -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts
```

### 3. 🔑 Configure Jenkins

* Install suggested plugins
* Create credentials for:

  * DockerHub
  * SSH private key to EC2

### 4. 📝 Jenkinsfile

Jenkins pipeline stages:

* Clone GitHub repo
* Build Docker image
* Push image to DockerHub
* Run Ansible playbook for deployment

### 5. 🚀 Setup EC2 Instance (Ubuntu)

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```

### 6. ⚙️ Configure Ansible on Jenkins Host

```bash
sudo apt install ansible -y
```

Update `ansible/inventory.ini`:

```ini
[web]
<EC2-IP> ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/key.pem
```

Update `ansible/deploy.yml` to pull and run Docker image from DockerHub.

---

## 🧪 Trigger the Pipeline

* Push code to GitHub or trigger Jenkins manually
* Jenkins executes the pipeline:

  * 🏗️ Builds image
  * 📤 Pushes to DockerHub
  * 🔧 Runs Ansible to deploy on EC2

---

## 🌐 Final Result

Access your deployed app in the browser at:

```
http://<EC2-Public-IP>
```

---

## 📈 Future Enhancements

* Add Slack or Email notifications
* Deploy to Kubernetes via Ansible
* Use Terraform to provision EC2 automatically
* Integrate with GitHub Webhooks for automatic triggers

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---

## 📜 License

This project is licensed under the MIT License.

---



Special thanks to all the open-source tools that made this pipeline possible.

---

```


