pipeline {
    agent {
        docker {
            image 'node:14'
            args '-p 5000:5000'
        }
    }
    environment {
        CI = 'true' 
    }
    stages {
        stage('Build') {
            steps {
                
                sh 'npm install --prefix frontend'
                sh 'npm install'
                sh 'pwd'
                
            }
        }
        
        stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
            sh 'npm test --prefix frontend'  
        
        
      }
    }

    }
}
