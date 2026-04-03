pipeline {
      agent any

      triggers {
          githubPush()
      }

      stages {
          stage('Checkout') {
              steps {
                  checkout scm
                  echo 'Code checked out from GitHub'
              }
          }

          stage('Build') {
              steps {
                  echo 'Building...'
                  sh 'echo "Build triggered by GitHub webhook at $(date)"'
              }
          }

          stage('Test') {
              steps {
                  echo 'Running Python checks...'
                    sh 'python3 -m py_compile test.py'
                    sh 'python3 test.py'
              }
          }

          stage('Deploy') {
              steps {
                  echo 'Deploying...'
                  sh 'echo "Deploy step completed"'
              }
          }
      }

      post {
          success {
              echo 'Pipeline succeeded!'
          }
          failure {
              echo 'Pipeline failed!'
          }
          always {
              echo 'Cleaning up...'
          }
      }
  }