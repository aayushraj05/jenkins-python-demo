pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            agent { label 'built-in' }
            steps {
                git branch: 'main', url: 'https://github.com/aayushraj05/jenkins-python-demo'
            }
        }

        stage('Create Python File') {
            agent { label 'built-in' }
            steps {
                sh '''
                echo "print('Hello from Jenkins!')" > script.py
                '''
            }
        }

        stage('Run Python Script') {
            agent { label 'built-in' }
            steps {
                sh 'python script.py'  // Using 'python' instead of 'python3'
            }
        }

        stage('Clean Workspace') {
            agent { label 'built-in' }
            steps {
                sh 'rm -f script.py'
            }
        }
    }
    
    post {
        success {
            echo "✅ Pipeline executed successfully!"
        }
        failure {
            echo "❌ Pipeline failed!"
        }
    }
}
