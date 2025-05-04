pipeline {
  agent any

  environment {
    MY_VARIABLE = "Hello, World!"
  }

  stages {
    stage('Build') {
      steps {
        echo 'Building...'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying...'
      }
    }
  }

  post {
    success {
      echo 'Pipeline executed successfully!'
    }

    failure {
      echo 'Pipeline execution failed!'
    }
  }
}
