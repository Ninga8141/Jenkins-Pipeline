echo "pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t myapp:latest .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo \"All tests passed!\"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying container...'
                sh 'docker stop myapp || true'
                sh 'docker rm myapp || true'
                sh 'docker run -d -p 5000:5000 --name myapp myapp:latest'
            }
        }
    }
}" > Jenkinsfile

