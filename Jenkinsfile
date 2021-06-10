pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim'
            args '-p 5000:5000'
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
                sh 'cd ..'
                sh 'npm install'
                
            }
        }
        
        stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'pwd'
        
      }
    }

    stage('Deliver') {
      steps {
        sh 'cd frontend'
        sh 'npm run build'
        sh 'cd ..'
        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
    }
}
