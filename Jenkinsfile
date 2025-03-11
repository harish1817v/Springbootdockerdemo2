pipeline {
    agent any

    environment {
        IMAGE_NAME = 'springbootdockerdemo2-springbootapp'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/harish1817v/Springbootdockerdemo2.git'
            }
        }

        stage('Build Application') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Docker Compose') {
            steps {
                sh 'docker-compose up --build -d'
            }
        }

        stage('Post Build Cleanup') {
            steps {
                sh 'docker ps -a'
            }
        }
    }

    post {
        success {
            echo 'Build and Deployment Successful 🎯'
        }
        failure {
            echo 'Build Failed ❌'
        }
    }
}
