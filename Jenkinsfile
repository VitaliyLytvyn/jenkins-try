#!/usr/bin/env groovy

pipeline {
    agent any
    environment {
        // Define environment variables here
        NEW_VERSION = '1.3.0'
    }
    parameters {
        string(name: 'APP_NAME', defaultValue: 'MyApp', description: 'Name of the application')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'test', 'prod'], description: 'Deployment environment')
        booleanParam(name: 'ENABLE_FEATURE_X', defaultValue: true, description: 'Enable Feature X?')
    }
    stages {
        stage('build') {
            steps {
                script {
                    echo "Building the application..."
                    echo "Building version ${NEW_VERSION}"
                }
            }
        }
        stage('test') {
            when {
                expression { params.ENABLE_FEATURE_X }
            }
            steps {
                script {
                    echo "Testing the application..."
                }
            }
        }
        stage('deploy') {
            steps {
                script {
                    echo "Deploying the application..."
                    echo "Deploying the application: ${params.APP_NAME} to ${params.ENVIRONMENT} environment"
                    // Example of using credentials
                    withCredentials([
                        usernamePassword(credentialsId: 'docker_hub_id', 
                                            usernameVariable: 'USERNAME', 
                                            passwordVariable: 'PASSWORD')]) {
                        sh "echo Deploying with username: ${USERNAME} and password: ${PASSWORD}"
                    }
                }
            }
        }
    }
}
