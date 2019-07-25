pipeline {
  agent { docker 'maven:3.5-alpine' }
  stages {
    stage ('Checkout') {
      steps {
        git 'https://github.com/atrillanes1972/spring-petclinic.git'
        }
    }
    stage ('Build') {
      sh 'mvn clean package'
      junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
  }
}
