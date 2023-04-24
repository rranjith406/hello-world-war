pipeline {
    agent any

    stages {
        stage('Checkout src') {
            steps {
                echo 'Java-Maven-war-project '
                echo "Branch_Name: ${env.GIT_BRANCH}" 
<<<<<<< HEAD
                //echo "${env.BRANCH_NAME}"
                //echo "${env.GIT_BRANCH}"//This will give me the Branch name
                git 'https://github.com/rranjith406/hello-world-war.git'
                sh 'ls -lrt'
                dir('dist') {
              		//sh 'mvn clean install -DskipTests'
              		echo 'cd to dist folder'
              		sh 'ls -lrt'
                }
=======
                git 'https://github.com/rranjith406/hello-world-war.git'
                sh 'ls -lrt'
>>>>>>> master
            }
        }
        stage('Build Stage') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test Stage') {
            steps {
<<<<<<< HEAD
                sh 'mvn clean test'
=======
                sh 'mvn test'
>>>>>>> master
            }
        }
        stage('Deploy Stage') {
            steps {
<<<<<<< HEAD
                echo 'This is Deploy stage (TBD)'
                sh 'echo Build ${BUILD_NUMBER}'
=======
                sshagent(['tomcat-id']) {
                    sh 'pwd'
                    dir('target') {
                        sh 'ls -lrt'
              		    sh 'mv hello-world-war-1.0.0.war hello-world-war-1.0.0-${BUILD_NUMBER}.war'
              		    sh 'scp -o StrictHostKeyChecking=no hello-world-war-1.0.0-${BUILD_NUMBER}.war ubuntu@172.31.32.178:/opt/tomcat/webapps'
                    }
                    
                }
>>>>>>> master
            }
        }
    }
}
