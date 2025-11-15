pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Project cloned automatically by Jenkins'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh './mvnw test'
            }
        }

        stage('Package') {
            steps {
                echo 'Building jar...'
                sh './mvnw clean package'
            }
        }

        stage('Finished') {
            steps {
                echo 'CI pipeline completed successfully!'
            }
        }
    }
}
