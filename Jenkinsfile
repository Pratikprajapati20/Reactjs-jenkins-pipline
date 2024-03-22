pipeline {
    agent any
    
    stages{
        stage("Code Clone"){
            steps{
                echo "cloning the code"
                git url:"https://github.com/Pratikprajapati20/Git-Tutorial-Devops.git",branch:"main"
            }
        }
        
        stage("build"){
            steps{
                echo "building the code"
                sh "docker build -t my-react-app ."
            }
        }
        
        stage("push to docker hub"){
            steps{
                echo "pushing the image to docker hub"
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                    sh "docker tag my-react-app ${env.dockerHubUser}/my-react-app:latest"
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                    sh "docker push ${env.dockerHubUser}/my-react-app:latest"
                }
            }
        }
        
        stage("Deploy"){
            steps{
                echo "Deplying the container"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}