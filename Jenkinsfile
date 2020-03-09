pipeline {
  agent any
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/van34/node-app-docker-ci-cd.git', branch: 'master')
      }
    }
stage('Sonarqube') {
    environment {
        scannerHome = tool 'sonarqubescaner'
    }
    steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
    
      }
    }

  }
}
