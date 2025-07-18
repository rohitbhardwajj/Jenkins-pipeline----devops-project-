# 🛠️ CI/CD Pipeline for TaskVault using Jenkins

This pipeline is written in **Jenkins Declarative syntax** and automates the end-to-end process of **building, testing, and deploying** the `TaskVault` project using Docker and Jenkins.

---

## 🔧 Agent

The pipeline runs on a Jenkins agent labeled:


---

## 📦 Stages Explained

### 1. 🧑‍💻 Code

Clones the source code from the GitHub repository:

Repository: https://github.com/rohitbhardwajj/TaskVault.git
Branch: main


---

### 2. 🏗️ Build

Builds a Docker image using the `Dockerfile` in the root directory:

```bash
docker build -t rohit20000/todo-img:latest .




3. 📤 Push
Pushes the Docker image to DockerHub:

Uses Jenkins credentials with ID: dockerHub

Logs in and pushes the image



docker login -u $dockerHubUser -p $dockerHubPassword
docker push rohit20000/todo-img:latest



4. ✅ Test
A placeholder test step for now:



echo 'Test successful'
Can be expanded later with real unit or integration tests.

5. 🚀 Deploy
Runs the Docker container on port 5173:



docker run -d -p 5173:5173 rohit20000/todo-img:latest
📌 Notes
Ensure the Jenkins agent has Docker installed and running.

Replace dockerHub with the actual Credentials ID from your Jenkins.

Modify the Test stage later to include automated testing scripts.

You can expose environment variables, ports, or use Docker Compose as needed.

✅ Done! Now your pipeline takes care of everything from pulling code ➜ building Docker image ➜ pushing to DockerHub ➜ deploying the app!
