pipeline {
    agent any

    stages {
        stage('Deploy HTML') {
            steps {
                sshagent(['apache-deploy-key']) {
                    script {
                        echo 'Deploying Hello.html to remote Apache server...'
                        // Copy the file to the remote server
                       sh 'scp Hello.html user@remote-server:/var/www/html/'
                    }
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    echo 'Verifying Hello.html deployment on remote server...'
                    // Verify the file is served correctly
                    sh 'curl http://remote-server/Hello.html'
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed. Check the logs for more details.'
        }
    }
}
