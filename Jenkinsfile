pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Build') {
      steps {
        withMaven(maven: 'Maven') {
          bat 'mvn clean install'
        }

      }
    }
    stage('Results') {
      steps {
        realtimeJUnit(testResults: '**/target/surefire-reports/TEST-*.xml')
        archiveArtifacts 'target/*.jar'
      }
    }
  }
}