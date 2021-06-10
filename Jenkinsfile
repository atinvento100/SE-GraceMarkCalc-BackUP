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
        sh 'set -x'
        sh 'npm start &'
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
