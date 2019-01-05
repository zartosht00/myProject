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
      input{
      message "Press Ok to continue"
      submitter "user1,user2"
      parameters {
      string(name:'username', defaultValue: 'user', description: 'Username of the user pressing Ok')
      }
      steps {
        sh "mvn -version"
        sh 'mvn clean compile'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
    stage('Production') {
      steps {
        sh 'mvn package'
      }
      post {
        success {
          echo "Only when we haven't failed running the first stage"
        }
        failure {
          echo "Only when we fail running the first stage."
        }
      }
      options {
        timeout(time: 60, unit: 'MINUTES')
      }
    }
  }
}
