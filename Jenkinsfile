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
                    -t docker.io/bunyakorngoko/prac-jenkins:latest \
                    -t docker.io/bunyakorngoko/prac-jenkins:${env.BUILD_NUMBER} \
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
                        docker login -u \$DOCKER_USERNAME -p \$DOCKER_PASSWORD docker.io
                        docker push docker.io/bunyakorngoko/prac-jenkins:${env.BUILD_NUMBER}
                    """
                }
            }
        }
    }
}
