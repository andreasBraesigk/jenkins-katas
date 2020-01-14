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
            archiveArtifacts 'app/build/libs/'
            sh 'ls -l'
            deleteDir()
            sh 'ls -l'
          }
        }

      }
    }

  }
}