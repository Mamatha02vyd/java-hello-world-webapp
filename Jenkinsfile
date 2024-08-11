pipeline {
    agent any
    environment {
        TOMCAT_URL = 'http://54.211.1.4:8080/manager/text' 
        TOMCAT_CREDENTIALS_ID = 'tomcat' 
    }

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
                script {
                    def warFile = '**/target/*.war'

                    deploy adapters: [tomcat9(credentialsId: TOMCAT_CREDENTIALS_ID, url: TOMCAT_URL, path: '')],
                            contextPath: '/java-hello-world',
                            war: warFile
                }
            }
        }
    }
}
