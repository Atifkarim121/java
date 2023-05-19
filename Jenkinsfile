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

        stages {
        stage('Deployment') {
            steps {
                script {
                    // SSH into the target EC2 instance
                    sshagent(credentials: ['3.218.207.21']) {
                        sh '''
                           
                            # Start the application
                            ssh -i ubuntu-jenins.pem ubuntu@3.218.207.21 sudo systemctl start HelloWorld.java
                        '''
                    }
                }
    }
}

