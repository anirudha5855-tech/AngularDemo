pipeline {
    agent any
    tools {
        nodejs "NodeJs"
    }
    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage("InstallPakage") {
            steps {
                bat "npm ci"
            }
        }
        stage("Test") {
            steps {
                bat "npx ng test --no-watch --no-progress --browsers=ChromeHeadless"
            }
        }
        stage("Build") {
            steps {
               bat "npx ng build --configuration production"     
            }
        }
    }
    post {
        success {
            echo "Angular application build successfully"
        }
        failure {
            echo "Build Failed"
        }
    }
}