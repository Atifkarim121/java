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
    stage('Deploy') {
            steps {
                sshagent(['your-ssh-credentials-id']) {
                    sh '''
                        ssh -o StrictHostKeyChecking=no -i /path/to/your/key.pem ec2-user@your-ec2-instance-ip 'sudo systemctl stop your-app'
                        scp -i /path/to/your/key.pem target/your-app.jar ec2-user@your-ec2-instance-ip:/path/to/deployment/folder/
                        ssh -o StrictHostKeyChecking=no -i /path/to/your/key.pem ec2-user@your-ec2-instance-ip 'sudo systemctl start your-app'
                    '''
                }
            }
        }
    
    }
    
}
