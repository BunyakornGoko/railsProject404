
node {
  stage('Build') {
    echo 'Building...'
  }

  stage('Test') {
    echo 'Running tests...'
  }

  stage('Deploy') {
    echo 'Deploying...'
  }

  if (currentBuild.result == 'SUCCESS') {
    echo 'Pipeline executed successfully!'
  } else {
    echo 'Pipeline execution failed!'
  }
}
