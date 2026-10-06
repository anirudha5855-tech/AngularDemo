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
                // bat "npx ng test --no-watch --no-progress --browsers=ChromeHeadless"
                echo "Testing"
            }
        }
        stage("Build") {
            steps {
               bat "npx ng build --configuration production"     
            }
        }
        stage("Diploy") {
            steps {
                bat "del /q /s c:\\inetpub\\wwwroot\\angularapp\\*"
                bat "xcopy /E /Y /I dist\\* c:\\inetpub\\wwwroot\\angularapp\\"
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