pipeline {
    agent any
    
    tools {
        maven 'MavenInstallation' // Name of the Maven installation configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Atifkarim121/java.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Deployment') {
            environment {
                SOURCE_EC2_IP = '44.197.218.22'
                SOURCE_PRIVATE_KEY = credentials('/home/ubuntu/.ssh/id_rsa')
                TARGET_EC2_IP = '3.218.207.21'
                TARGET_PRIVATE_KEY = credentials('/home/ubuntu/.ssh/id_rsa')
            }

            steps {
                sh "scp -i ${SOURCE_PRIVATE_KEY} your-app.jar ubuntu-jenkins.pem ubuntu@${SOURCE_EC2_IP}:~/"
                sh "ssh -i ${TARGET_PRIVATE_KEY} ubuntu-jenkins.pem ubuntu@${TARGET_EC2_IP} 'scp ~/your-app.jar ubuntu@${TARGET_EC2_IP}:~/ && java -jar your-app.jar &'"
            }
        }
    }
}

