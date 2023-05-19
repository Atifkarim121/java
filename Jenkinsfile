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

        stage('Deploy') {
            steps {
                sh '''
                    sudo systemctl stop your-app
                    java -cp target/jb-hello-world-maven-0.1.0.jar hello.HelloWorld
                    sudo systemctl start your-app
                '''
            }
        }
    }
}
