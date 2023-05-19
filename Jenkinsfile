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

        stage ('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '0ec60cd3-c147-467b-bc23-ceabd7954e28', path: '', url: 'http://localhost:8081/')], contextPath: 'jenkins_calci', onFailure: false, war: '**/*.war'
                echo "Deploy successful"
            }
        }
    }
}
