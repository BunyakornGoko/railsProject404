pipeline {
    agent any
    stages {
        stage('list file') {
            steps { 
                sh 'ls -l'
                sh 'ls -l'
            }
        }
        stage('Build Docker Image') {
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
                withCredentials([usernamePassword(credentialsId: 'DOCKER_CREDENTIALS', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh """
                        echo \$DOCKER_USERNAME
                        echo \$DOCKER_PASSWORD | sed 's/./*/g'
                        echo \$DOCKER_PASSWORD | docker login --username \$DOCKER_USERNAME --password-stdin docker.io
                        docker push registry-1.docker.io/bunyakorngoko/prac-jenkins:${env.BUILD_NUMBER}
                    """
                }
            }
        }
    }
}
