pipeline {
    agent any
    stages {
        stage ('Git-Checkout') {
            steps {
                git credentialsId: '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', url: 'https://github.com/Atifkarim121/java.git'
                echo "Checkout successful"
            }
        }

        stage ('Build') {
            steps {
                bat label: '', script: 'mvn verify'
                bat label: '', script: 'mvn clean install'
                echo "Build successful"
            }
        }
    }
}
