pipeline {
    agent java

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
    }
}
