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

      post {
        failure {
              mail to: 'cb.en.u4cse18245@cb.students.amrita.edu',
                 cc : 'cb.en.u4cse18245@cb.students.amrita.edu'
                subject: "FAILED: Build ", 
                body: """Build failed 
                Build $BUILD_NUMBER failed.Go to $BUILD_URL for more info."""
        }
    
    success{
            mail to: 'cb.en.u4cse18245@cb.students.amrita.edu',
                 cc : 'cb.en.u4cse18245@cb.students.amrita.edu'
                subject: "SUCCESSFUL: Build ", 
                body: """Build Successful 
                Build $BUILD_NUMBER failed.Go to $BUILD_URL for more info."""
        }
        
    aborted{
            mail to: 'cb.en.u4cse18245@cb.students.amrita.edu',
                 cc : 'cb.en.u4cse18245@cb.students.amrita.edu'
                subject: "ABORTED: Build ", 
                body: """Build was aborted 
                Build $BUILD_NUMBER failed.Go to $BUILD_URL for more info."""
        }
    }

    }
}
