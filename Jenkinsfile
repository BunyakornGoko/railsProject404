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

    stage('Deploy') {
      steps {
        docker run -d -p 3001:80 --name goko404-service registry-1.docker.io/bunyakorngoko/prac-jenkins:${env.BUILD_NUMBER}
      }
    }
  }
}
