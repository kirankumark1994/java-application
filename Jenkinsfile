pipeline {
   agent any
    environment {
        PATH = "/opt/apache-maven-3.9.3/bin:${PATH}"
    } 
    stages {
        stage('checkout') {
            steps {
                // Checkout the source code from our version control system#############
                // Here our version control system is git.####################
                git 'https://github.com/kirankumark1994/java-application.git'
                
            }
        }
        
        stage('Build') {
            steps {
                //Build the project using maven ###############
                sh 'mvn clean package'
            }
        }
        stage('Deployment') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-user', path: '', url: 'http://52.90.31.37:8080/')], contextPath: null, war: '**/*.war'
               // deploy adapters: [tomcat9(credentialsId: 'tomcat-user', path: '', url: 'http://3.86.85.190:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
