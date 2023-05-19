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
                SOURCE_PRIVATE_KEY = credentials(' /home/ubuntu/.ssh/id_rsa')
                TARGET_EC2_IP = '3.218.207.21'
                TARGET_PRIVATE_KEY = credentials('/home/ubuntu/.ssh/id_rsa')
            }

            steps {
                sh "scp -i ${.ssh/id_rsa} your-app.jar ubuntu-jenins.pem ubuntu@${44.197.218.22}:~/"
                sh "ssh -i ${.ssh/id_rsa} ubuntu-jenins.pem ununtu@${3.218.207.21} 'scp ~/your-app.jar ubuntu@${3.218.207.21}:~/ && java -jar your-app.jar &'"
            }
        }
    }
}
