#!/usr/bin/env groovy

pipeline {
    agent any
    environment {
        // Define environment variables here
        NEW_VERSION = '1.3.0'
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
