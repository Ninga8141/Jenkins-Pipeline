pipeline {
    agent any

    environment {
        IMAGE_NAME = "ninga8141/myapp:latest"
        CONTAINER_NAME = "myapp"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                echo "🔹 Building Docker image..."
                sh "docker build -t $ninga8141/myapp:latest ."
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "🚀 Deploying container..."
                sh """
                    # Stop and remove old container if it exists
                    docker rm -f $myapp || true

                    # Run new container
                    docker run -d --name $myapp -p 5000:5000 $ninga8141/myapp:latest
                """
            }
        }

        stage('Verify Container') {
            steps {
                echo "🔹 Listing running containers..."
                sh "docker ps"
            }
        }
    }

    post {
        success {
            echo "✅ Docker container is running successfully!"
        }
        failure {
            echo "❌ Pipeline failed. Check the Jenkins logs."
        }
    }
}

