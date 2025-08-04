# ⚙️ CI/CD Pipeline for React.js App using Jenkins

This project demonstrates how to automate the build and deployment process for a React.js application using **Jenkins**. The pipeline includes stages for pulling the source code, installing dependencies, running tests, building the project, and deploying it to a web server.

---

## 🚀 Project Overview

- **Frontend**: React.js  
- **CI/CD Tool**: Jenkins  
- **Build Automation**: Shell scripting & Jenkins pipeline  
- **Deployment**: NGINX or any static file server  
- **Version Control**: GitHub

---

## 🧱 Pipeline Stages

1. **Source Code Checkout**
2. **Dependency Installation**
3. **Code Linting / Formatting**
4. **Run Tests (Optional)**
5. **Build React App**
6. **Deploy to Server (Local or Remote)**

---

## 📂 Folder Structure

```bash
Reactjs-jenkins-pipline/
├── react-app/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
├── Jenkinsfile
└── README.md

```

🔧 Prerequisites
  - Jenkins installed on your machine or server
  - Node.js & npm installed
  - React app code inside the react-app/ folder
  - GitHub webhook (optional for automation)

🛠️ Setup Instructions
---
```bash
git clone https://github.com/Pratikprajapati20/Reactjs-jenkins-pipline.git
cd Reactjs-jenkins-pipline
```
2. Configure Jenkins
Create a New Item → Pipeline
In the pipeline configuration:
  - Connect the repository
  - Set up webhook for automated builds (optional)
  - Use the provided Jenkinsfile for pipeline script

#3. Sample Jenkinsfile
---
```bash
pipeline {
  agent any

  stages {
    stage('Checkout Code') {
      steps {
        git 'https://github.com/Pratikprajapati20/Reactjs-jenkins-pipline.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        dir('react-app') {
          sh 'npm install'
        }
      }
    }

    stage('Build React App') {
      steps {
        dir('react-app') {
          sh 'npm run build'
        }
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying the build...'
        // Add deployment commands here
      }
    }
  }
}
```


