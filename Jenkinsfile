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
      agent {
        docker {
          image 'saonam/jenkins_android:v1'
        }
      }
      steps {
        git(url: FRONTEND_GIT, branch: FRONTEND_BRANCH)
        sh 'cd android && ./gradlew assembleRelease'
        sh 'echo "test jenkins build android" > /tmp/jenkins.txt'
        stash(name: 'frontend', includes: 'app/build/outputs/apk/release/**')
      }
    }
    stage('Signing APK') {
      steps {
        dir("frontend") {
            unstash "frontend"
        }

        sh 'ls -l > /tmp/jenkins_tmp.txt'
      }
    }
  }
}
