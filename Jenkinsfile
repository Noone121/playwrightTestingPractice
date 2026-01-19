pipeline {
    agent any
    tools {
        nodejs 'node18'
    }

    stages {

         stage('Checkout') {
      steps {
        checkout scm
      }
    }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
                bat 'npx playwright install'
            }
        }
        stage('Run Playwright Tests') {
            steps {
                bat 'npx playwright test'
            }
        }
    }

  post {
    always {
      archiveArtifacts artifacts: 'playwright-report/**', fingerprint: true
    }
  }
}