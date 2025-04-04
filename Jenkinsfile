pipeline {
    agent any

    triggers { pollSCM('*/1 * * * *') }

    stages {
        stage('build') {
            steps {
                buildApp()
            }
        }
        stage('deploy-dev') {
            steps {
                deploy("DEV")
            }
        }
        stage('test-dev') {
            steps {
                test("DEV")
            }
        }
        stage('deploy-stg') {
            steps {
                deploy("STG")
            }
        }
        stage('test-stg') {
            steps {
                test("STG")
            }
        }
        stage('deploy-prd') {
            steps {
                deploy("PRD")
            }
        }
        stage('test-prd') {
            steps {
                test("PRD")
            }
        }
    }
}

def buildApp(){
    echo 'Building micro-service...'
}

def deploy(String environment){
    echo "Deployment to ${environment} has started..."
}

def test(String environment){
    echo "Running tests on ${environment} against micro-service..."
}