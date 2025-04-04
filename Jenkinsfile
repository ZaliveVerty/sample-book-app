pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                build()
            }
        }
        stage('deploy-dev') {
            steps {
                deploy("DEV")
            }
        }
        stage('test-dev') {
            steps {
                deploy("DEV")
            }
        }
        stage('deploy-stg') {
            steps {
                deploy("STG")
            }
        }
        stage('test-stg') {
            steps {
                deploy("STG")
            }
        }
        stage('deploy-prd') {
            steps {
                deploy("PRD")
            }
        }
        stage('test-prd') {
            steps {
                deploy("PRD")
            }
        }
    }
}

def build(){
    echo 'Building micro-service...'
}

def deploy(String environment){
    echo "Deployment to ${environment} has started..."
}

def test(String environment){
    echo "Running tests on ${environment} against micro-service..."
}