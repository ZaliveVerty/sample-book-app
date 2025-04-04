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
                test("BOOKS", "DEV")
            }
        }
        stage('deploy-stg') {
            steps {
                deploy("STG", 2020)
            }
        }
        stage('test-stg') {
            steps {
                test("BOOKS", "STG")
            }
        }
        stage('deploy-prd') {
            steps {
                deploy("PRD", 3030)
            }
        }
        stage('test-prd') {
            steps {
                test("BOOKS", "PRD")
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
    git branch: 'main', poll: false, url: 'https://github.com/ZaliveVerty/sample-book-app.git'
    bat "npm install"
    bat "npx pm2 delete \"books-${environment}\" || exit 0"
    bat "npx pm2 start index.js --name \"books-${environment}\" -- ${port}"
}

def test(String test_set, String environment){
    echo "Testing ${test_set} test set on ${environment} against micro-service..."
    git branch: 'main', poll: false, url: 'https://github.com/ZaliveVerty/api-automation.git'
    bat "npm install"
    bat "npm run ${test_set} ${test_set}_${environment}"
}