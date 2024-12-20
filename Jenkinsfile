pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Run the Python code
               bat 'javac Hello.java'
            }
        }
        stage('Run') {
            steps {
               bat 'java Hello'
            }
        }
    }
}
