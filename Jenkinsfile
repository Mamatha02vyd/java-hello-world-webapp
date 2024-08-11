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
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: '34.205.73.231')], contextPath: '/opt/tomcat/webapps/', war: '**/*.war'
                }
            }
        }
    }

