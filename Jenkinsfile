pipeline {
  agent {
    node {
      label 'slave_tuantq'
    }
  }
  environment {
    FRONTEND_GIT = 'https://github.com/saonam/myfirstProject.git'
    FRONTEND_BRANCH = 'master'
  }
  stages {
    stage('Build Android') {
      steps {
        sh 'echo "test jenkins moi" > /tmp/jenkins.txt'
      }
    }
  }
}
