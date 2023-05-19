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
                    ls -la target # List files in the target directory
                    java -cp target/your-app.jar hello.HelloWorld
                '''
            }
        }
    }
}

