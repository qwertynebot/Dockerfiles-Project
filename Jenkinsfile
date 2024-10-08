pipeline {
    agent any

    environment {
        // Укажіть шлях до вашого репозиторію Git
        GIT_REPO_URL = 'https://your-git-repo-url.git'
        // Укажіть ім'я гілки, якщо це необхідно (наприклад, main, master)
        GIT_BRANCH = 'main'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Клонуємо репозиторій
                git branch: "${GIT_BRANCH}", url: "${GIT_REPO_URL}"
            }
        }

        stage('Deploy Frontend') {
            steps {
                script {
                    // Застосовуємо маніфест для фронтенду
                    sh 'kubectl apply -f front.yaml'
                }
            }
        }

        stage('Deploy Backend') {
            steps {
                script {
                    // Застосовуємо маніфест для бекенду
                    sh 'kubectl apply -f back.yaml'
                }
            }
        }
    }

    post {
        always {
            // Виведення поточного стану подів після кожного розгортання
            sh 'kubectl get pods'
        }
        success {
            echo 'Deployment completed successfully.'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
