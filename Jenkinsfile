pipeline {
    agent any

    environment {
        // Define your Docker Hub credentials ID here
        DOCKER_CREDENTIALS_ID = 'docker-hub-credentials'
        IMAGE_NAME = 'veerudsai/todolist-app'
        IMAGE_TAG = "${env.BUILD_ID}"
        // SonarQube installation name defined in Jenkins
        SONAR_SCANNER_HOME = tool 'SonarQubeScanner'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from Git
                checkout scm
            }
        }

        stage('Dependency Check') {
            steps {
                echo 'Running NPM Audit for Vulnerability/Security Checks...'
                // Install dependencies
                bat 'npm install' // use 'sh' if on Linux/macOS Jenkins
                // Run npm audit. Using --audit-level=high so it doesn't fail on minor issues.
                // Depending on the environment, you might use OWASP Dependency-Check plugin instead.
                bat 'npm audit --audit-level=high' 
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Running SonarQube Analysis...'
                withSonarQubeEnv('SonarQube') { // 'SonarQube' should match the server name in Jenkins settings
                    // Use 'sh' on Linux, 'bat' on Windows
                    bat "${SONAR_SCANNER_HOME}\\bin\\sonar-scanner.bat"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker Image...'
                script {
                    // Build the Docker image
                    dockerImage = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                echo 'Pushing Docker Image to Registry...'
                script {
                    // Ensure you have configured 'docker-hub-credentials' in Jenkins
                    docker.withRegistry('', DOCKER_CREDENTIALS_ID) {
                        dockerImage.push()
                        dockerImage.push('latest') // Also tag and push as latest
                    }
                }
            }
        }

        stage('Deploy to Azure Web App') {
            steps {
                echo 'Deploying to Azure Web App for Containers...'
                // You can use the Azure Web App plugin or Azure CLI here
                // Example using Azure CLI:
                // bat 'az webapp config container set --name YourWebAppName --resource-group YourResourceGroup --docker-custom-image-name ${DOCKER_REGISTRY}/${IMAGE_NAME}:${IMAGE_TAG}'
                echo 'Deployment step placeholder - Ensure Azure CLI is configured.'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed. Cleaning up workspace...'
            cleanWs()
        }
        success {
            echo 'CI/CD Pipeline executed successfully!'
        }
        failure {
            echo 'CI/CD Pipeline failed. Please check the logs.'
        }
    }
}
