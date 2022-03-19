pipeline {
    agent any
    tools {
    maven 'Maven3.8.4'
    }
    stages {
        stage('Check-out') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/pra31de/javawebapp.git']]])
            }
        }
        stage('Build') {
            steps { 
                sh 'mvn clean install -f pom.xml'
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-deployer', path: '', url: 'http://65.0.106.203:8080')], contextPath: null, war: '**/*.war'
            }
        }
    }
}  
