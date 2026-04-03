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
                  echo 'Running tests...'
                  sh 'echo "All tests passed!"'
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