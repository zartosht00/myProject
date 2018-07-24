pipeline {
  agent { label 'jslave_4 Core Linux Slave1' }
  tools {
    maven 'M3'
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
