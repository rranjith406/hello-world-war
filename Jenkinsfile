pipeline {
    agent any

    stages {
        stage('Checkout src') {
            steps {
                echo 'Java-Maven-war-project '
                echo "Branch_Name: ${env.GIT_BRANCH}" 
                git 'https://github.com/rranjith406/hello-world-war.git'
                sh 'ls -lrt'
            }
        }
        stage('Build Stage') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test Stage') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy Stage') {
            steps {
                sshagent(['tomcat-id']) {
                    sh 'pwd'
                    dir('target') {
                        sh 'ls -lrt'
              		    sh 'mv hello-world-war-1.0.0.war hello-world-war-1.0.0-${BUILD_NUMBER}.war'
              		    sh 'scp -o StrictHostKeyChecking=no hello-world-war-1.0.0-${BUILD_NUMBER}.war ubuntu@172.31.32.178:/opt/tomcat/webapps'
                    }
                    
                }
            }
        }
    }
}
