  
pipeline {
  agent {
    docker {
      image 'node'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Install packages') {
      steps {
        sh 'npm install'
        sh 'pwd'
        sh 'ls -la'
      }
    }

    stage('Test') {
      steps {
        sh 'npm run test -- --coverage --watchAll=false'
      }
    }

    stage('Linter') {
      steps {
        sh 'npm run lint'
      }
    }
    stage('Build/Deploy'){
      steps {
        sh 'npm run build'
        sh 'npm install -g serve'
        sh 'serve -s build'
      }
    }
  }
  environment {
    CI = 'true'
  }
}
