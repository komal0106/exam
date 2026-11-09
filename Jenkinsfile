pipeline {
    agent any
    stages {

        stage('Build') {
            steps {
               
                bat "docker build -t mypythonimage:latest ."
            }
        }

        stage('Login') {
            steps {
                echo "Logging in to Docker Hub..."
            
                bat "docker login -u komal0106 -p guddu2006"
            }
        }

        stage('Push') {
            steps {
                echo "Pushing Docker Image to Docker Hub..."
                bat "docker tag mypythonimage komal0106/week9repo:latest"
                bat "docker push komal0106/week9repo:latest"
            }
        }

        stage('Deploy') {
            steps {
            
                bat "kubectl apply -f deployment.yaml --validate=false"
                bat "kubectl apply -f service.yaml"
            }
        }

    }

    post {
        success {
            echo "deployed successfully"
            
        }

        failure {
            echo "deployment failed"
          
        }
    }
}

