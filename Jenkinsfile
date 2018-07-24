pipeline {
  agent any
  tools {
    maven 'Maven 3'
  }
  stages {
    stage('checkout') {
      steps {
        git 'https://github.com/mfhoss/myProject.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean compile'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
