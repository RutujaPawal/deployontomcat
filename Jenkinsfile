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
        stage('deploy the war file'){
            sshagent(['deployer']) {
                  sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@3.108.220.117:/opt/apache-tomcat-8.5.84/webapps'
              }
        }
            
    }
}
