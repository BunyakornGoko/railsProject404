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

     stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DOCKER_CREDENTIALS', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                sh """
                        docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD registry-1.docker.io
                        docker push registry-1.docker.io/bunyakorngoko/prac-jenkins:${env.BUILD_NUMBER}
                      """
                }
            }
        }
  }
}
