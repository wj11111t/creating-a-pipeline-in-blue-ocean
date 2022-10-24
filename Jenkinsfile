pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          environment {
            CI = 'true'
          }
          steps {
            sh './jenkins/scripts/test.sh'
          }
        }

        stage('Test2') {
          steps {
            sh 'echo "this is test2"'
          }
        }

        stage('Test3') {
          steps {
            echo 'this is test3'
          }
        }

      }
    }

    stage('Deliver') {
      steps {
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/deliver.sh'
      }
    }

  }
}