pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Example: sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Example: sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                // Example: sh 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Example: sh 'bandit -r .'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Example: sh 'deploy-to-staging.sh'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Example: sh 'run-staging-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                // Example: sh 'deploy-to-production.sh'
            }
        }
    }

    post {
        success {
            emailext (
                to: 'arsheenk88@gmail.com',
                subject: "Build ${env.BUILD_NUMBER} - Success",
                body: "Build ${env.BUILD_NUMBER} was successful.",
                attachLog: true
            )
        }
        failure {
            emailext (
                to: 'arsheenk88@gmail.com',
                subject: "Build ${env.BUILD_NUMBER} - Failure",
                body: "Build ${env.BUILD_NUMBER} failed.",
                attachLog: true
            )
        }
    }
}
