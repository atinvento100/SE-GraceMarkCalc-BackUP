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
        sh 'set -x'
        sh 'npm run dev'
        sh 'sleep 1'
        sh 'echo $! > .pidfile'
        sh 'set +x'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh 'set -x'
        sh 'kill $(cat .pidfile)'
      }
    }
    }
}
