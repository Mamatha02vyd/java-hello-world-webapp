pipeline {
    agent any
    tools {
        maven 'Maven3'  
        jdk 'JDK11'     
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy to Remote Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://34.205.73.231:8080/manager/text')],
                       contextPath: '/java-hello-world', war: '**/*.war'
            }
        }
    }
}
