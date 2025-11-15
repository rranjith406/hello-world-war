pipeline {
    agent any
    stages {
        stage('SCM checkout') {
            steps {
                echo 'Checking out remote repo to Jenkins Local Workspace'
                git branch: 'master', url: 'https://github.com/ranjith-vedansh/java-hello-world-war.git'
            }
        }
        stage('Build Stage') {
            steps {
                echo 'Building WAR file from source code'
                sh 'mvn clean package'
                sh 'ls -lrt target'
            }
        }
        stage('Test Stage') {
            steps {
                echo 'Executing Unit Tests'
                // sh 'mvn test'
            }
        }
        stage('Deploy Stage') {
            steps {
                echo 'Deploying WAR to remote Web Server'

                sshagent(['ec2-ssh-creds']) {
                    // Example Deployment (update with your server details)
                    //sh 'scp target/*.war ubuntu@13.233.145.108:/opt/tomcat/webapps/'
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@13.233.145.108 ls -lrt'
                    sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@13.233.145.108:/opt/tomcat/webapps/'
                    echo '✅ Copy completed successfully.'
		            sh 'ssh ubuntu@13.233.145.108 "sudo systemctl restart tomcat"'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed'
        }
        failure {
            echo 'Pipeline execution failed'
        }
    }
}
