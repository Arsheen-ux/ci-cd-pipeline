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
            post {
                success {
                    emailext (
                        to: 'arsheenk88@gmail.com',
                        subject: "Build ${env.BUILD_NUMBER} - Unit and Integration Tests - Success",
                        body: "Unit and integration tests for Build ${env.BUILD_NUMBER} were successful.",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: 'arsheenk88@gmail.com',
                        subject: "Build ${env.BUILD_NUMBER} - Unit and Integration Tests - Failure",
                        body: "Unit and integration tests for Build ${env.BUILD_NUMBER} failed.",
                        attachLog: true
                    )
                }
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
            post {
                success {
                    emailext (
                        to: 'arsheenk88@gmail.com',
                        subject: "Build ${env.BUILD_NUMBER} - Security Scan - Success",
                        body: "Security scan for Build ${env.BUILD_NUMBER} was successful.",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: 'arsheenk88@gmail.com',
                        subject: "Build ${env.BUILD_NUMBER} - Security Scan - Failure",
                        body: "Security scan for Build ${env.BUILD_NUMBER} failed.",
                        attachLog: true
                    )
                }
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
                subject: "Build ${env.BUILD_NUMBER} - Overall Success",
                body: "Build ${env.BUILD_NUMBER} was successful.",
                attachLog: true
            )
        }
        failure {
            emailext (
                to: 'arsheenk88@gmail.com',
                subject: "Build ${env.BUILD_NUMBER} - Overall Failure",
                body: "Build ${env.BUILD_NUMBER} failed.",
                attachLog: true
            )
        }
    }
}
