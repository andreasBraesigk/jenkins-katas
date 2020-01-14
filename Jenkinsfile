pipeline {
  agent any
  stages {
    stage('parallel execution') {
      parallel {
        stage('Say hello') {
          steps {
            sh 'echo "hello world"'
          }
        }

        stage('build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'ci/build-app.sh'
          }
        }

      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts 'app/build/libs/'
      }
    }

  }
}