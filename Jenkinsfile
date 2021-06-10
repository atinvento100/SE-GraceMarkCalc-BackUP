pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true' 
    }
    stages {
        stage('Build') {
            steps {
                sh 'cd frontend'
                sh 'npm install'
                sh 'cd..'
                sh 'npm install'
                
            }
        }
        
        stage('Test') {
      environment {
        CI = 'true'
      }
      
    }
    }
}