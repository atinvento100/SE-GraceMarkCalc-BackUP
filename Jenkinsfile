pipeline {
    agent {
        docker {
            image 'node:14'
            args '-p 3000:3000'
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
        sh 'pwd'
        
      }
    }

    // stage('Deliver') {
    //   steps {
        
    //     sh 'set -x'
    //     sh 'npm run dev'
    //     sh 'sleep 1'
    //     sh 'echo $! > .pidfile'
    //     sh 'set +x'
    //     input 'Finished using the web site? (Click "Proceed" to continue)'
    //     sh 'set -x'
    //     sh 'kill $(cat .pidfile)'
    //   }
    // }
    }
}
