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
                deploy("DEV", 1010)
            }
        }
        stage('test-dev') {
            steps {
                test("DEV")
            }
        }
        stage('deploy-stg') {
            steps {
                deploy("STG", 2020)
            }
        }
        stage('test-stg') {
            steps {
                test("STG")
            }
        }
        stage('deploy-prd') {
            steps {
                deploy("PRD", 3030)
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
    bat "npm install"
}

def deploy(String environment, int port){
    echo "Deployment to ${environment} has started..."
    bat "npx pm2 start index.js --name \"books-${environment}\" -- ${port}"
}

def test(String environment){
    echo "Running tests on ${environment} against micro-service..."
}