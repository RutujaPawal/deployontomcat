pipeline {
    agent any 
    
    tools {
        maven 'Maven3'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/RutujaPawal/deployontomcat.git']]])
            }
        }      
        stage ('Build') {
            steps {
                sh 'mvn clean install'           
            }
        } 
    }
}
