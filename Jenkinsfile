pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/harish1817v/Springbootdockerdemo2.git'
            }
        }
        stage('Build Application') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t springbootdocker .'
            }
        }
        stage('Run Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
    post {
        success {
            echo "Build Successful ✅"
        }
        failure {
            echo "Build Failed ❌"
        }
    }
}
