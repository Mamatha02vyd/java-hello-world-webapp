pipeline {
    agent any
    environment {
        TOMCAT_URL = 'http://3.85.210.224:8080'
        TOMCAT_CREDENTIALS = credentials('tomcat-remote-credentials')
    }

    tools {
        maven 'Maven3'  
        jdk 'JDK11'     
    }
    stages {
        stage ('Checkout') {
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
                script {
                    def warFile = '**/target/*.war'
                    deploy adapters: [tomcat10(credentialsId: TOMCAT_CREDENTIALS, path: '', url: TOMCAT_URL)],
                            contextPath: '/java-hello-world',
                            war: warFile
                }
            }
        }
    }
}
