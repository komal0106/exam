pipeline {
    agent any
    stages {

        stage('Build Docker Image') {
            steps {
               
                bat "docker build -t mypythonimage:latest ."
            }
        }

        stage('Docker Login') {
            steps {
                echo "Logging in to Docker Hub..."

                bat "docker login -u komal0106 -p guddu2006"
            }
        }

        stage('Push Docker Image to Docker Hub') {
            steps {
                echo "Pushing Docker Image to Docker Hub..."

                bat "docker push komal0106/week9repo:latest"
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
               

                bat "kubectl apply -f deployment.yaml --validate=false"
                bat "kubectl apply -f service.yaml"
            }
        }

        
    }

    post {
        success {
            echo "PIPELINE COMPLETED SUCCESSFULLY!"
            
        }

        failure {
            echo "PIPELINE FAILED!"
          
        }
    }
}

