pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'Building micro-service...'
            }
        }
        stage('deploy-dev') {
            steps {
                deploy("DEV")
            }
        }
        stage('test-dev') {
            steps {
                echo 'Running tests on DEV against micro-service...'
            }
        }
        stage('deploy-stg') {
            steps {
                deploy("STG")
            }
        }
        stage('test-stg') {
            steps {
                echo 'Running tests on STG against micro-service...'
            }
        }
        stage('deploy-prd') {
            steps {
                deploy("PRD")
            }
        }
        stage('test-prd') {
            steps {
                echo 'Running tests on PRD against micro-service...'
            }
        }
    }
}

def deploy(String environment){
    echo "Running tests on ${environment} against micro-service..."
}