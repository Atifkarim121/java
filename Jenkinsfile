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
                    sudo  -S systemctl stop your-app
                    java -cp target/your-app.jar hello.HelloWorld
                    sudo  -S systemctl start your-app
                '''
            }
        }
    }
}
