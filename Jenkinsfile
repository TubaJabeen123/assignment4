pipeline {
    agent any

    stages {
        stage('Deploy HTML') {
            steps {
                script {
                    echo 'Deploying Hello.html to Apache server...'
                    // Assuming Hello.html is already in your repository
                    // Copy the Hello.html file to the Apache web server root
                    sh 'cp Hello.html /var/www/html/'
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    echo 'Verifying Hello.html deployment...'
                    // Use curl to check if the HTML file is accessible via Apache
                    sh 'curl http://localhost/Hello.html'
                }
            }
        }

        stage('Restart Apache') {
            steps {
                script {
                    echo 'Restarting Apache server to apply changes...'
                    // Restart Apache to ensure the new file is served
                    sh 'sudo systemctl restart apache2'
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up resources...'
            // Optional: Perform any cleanup steps if needed
        }
        success {
            echo 'Hello.html successfully deployed and served!'
        }
        failure {
            echo 'Deployment failed. Check the logs for details.'
        }
    }
}
