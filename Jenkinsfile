pipeline {
  agent any

  environment {
    MY_VARIABLE = "Hello, World!"
  }

  stages {
    stage('Build') {
            steps {
          // สร้าง Docker image
          sh """
              docker build --rm \
              -f Dockerfile \
              -t registry-1.docker.io/bunyakorngoko/prac-jenkins \
              -t registry-1.docker.io/bunyakorngoko/prac-jenkins:${env.BUILD_NUMBER} \
              .
          """
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
