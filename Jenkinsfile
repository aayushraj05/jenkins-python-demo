pipeline {
    agent any  // Runs on any available agent

    stages {
        stage('Checkout Code') {
            agent { label 'built-in' }  // Runs on the main Jenkins agent (default)
            steps {
                git branch: 'main', url: 'https://github.com/aayushraj05/jenkins-python-demo'
            }
        }

        stage('Create Python File') {
            agent { label 'built-in' }  // Runs on the main Jenkins agent
            steps {
                sh '''
                echo "print('Hello from Jenkins!')" > script.py
                '''
            }
        }

        stage('Run Python Script') {
            agent { label 'built-in' }  // Runs on the main Jenkins agent
            steps {
                sh 'python3 script.py'
            }
        }

        stage('Clean Workspace') {
            agent { label 'built-in' }  // Runs on the main Jenkins agent
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

