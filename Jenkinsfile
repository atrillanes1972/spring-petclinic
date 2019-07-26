podTemplate(yaml: """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: docker
    image: docker:1.11
    command: ['cat']
    tty: true
    volumeMounts:
    - name: dockersock
      mountPath: /var/run/docker.sock
  volumes:
  - name: dockersock
    hostPath:
      path: /var/run/docker.sock
"""
pipeline {
  agent { docker 'maven:3.5-alpine' }
  stages {
    stage ('Checkout') {
      steps {
        git 'https://github.com/atrillanes1972/spring-petclinic.git'
        }
    }
    stage ('Build') {
      steps {
      sh 'mvn clean package'
      junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
  }
}
