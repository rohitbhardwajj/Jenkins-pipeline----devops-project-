This pipeline is written in Jenkins Declarative syntax and automates the end-to-end process for building, testing, and deploying the TaskVault project.

🔧 Agent
The pipeline runs on a Jenkins agent labeled agent-vinod.

📦 Stages Explained
1. Code 🧑‍💻
Clones the source code from the GitHub repository:




https://github.com/rohitbhardwajj/TaskVault.git (branch: main)
2. Build 🏗️
Builds a Docker image using the Dockerfile in the root directory:




docker build -t rohit20000/todo-img:latest .
3. Push 📤
Pushes the built Docker image to DockerHub:

Uses Jenkins credentials stored with ID: dockerHub

Logs in and pushes the image:




docker login -u $dockerHubUser -p $dockerHubPassword
docker push rohit20000/todo-img:latest
4. Test ✅
A basic test stage for now:




echo 'Test successful'
Can be expanded to include actual test commands.

5. Deploy 🚀
Runs the Docker container on port 5173:




docker run -d -p 5173:5173 rohit20000/todo-img:latest
📌 Note
Ensure the Jenkins agent has Docker installed.

Replace dockerHub credential ID with your actual Jenkins credentials ID if needed.

Consider enhancing the Test stage with real unit/integration tests.

