pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script{
                    build()
                }
            }
        }

        stage('Deploy to DEV') {
            steps {
                script{
                    deploy("DEV", 1010) // 1010
                }
            }
        }

        stage('Tests on DEV') {
            steps {
                script{
                    test("DEV")
                }
            }
        }

        stage('Deploy to STG') {
            steps {
                script{
                    deploy("STG", 1020) // 1020
                }
            }
        }

        stage('Tests on STG') {
            steps {
                script{
                    test("STG")
                }
            }
        }

        stage('Deploy to PRD') {
            steps {
                script{
                    deploy("PRD", 1030) // 1030
                }
            }
        }

        stage('Tests on PRD') {
            steps {
                script{
                    test("PRD")
                }
            }
        }
    }
}

def deploy(String enviroment, int port) {
    echo "Deployment to ${enviroment} has started ..."
    bat "pm2 delete ${enviroment}"
    bat "pm2 start -n \"${enviroment}\" index.js -- ${port}"
}

def test(String enviroment) {
    echo "Testing on ${enviroment} has started ..."
    bat "npm test"
}

def build(){
    echo 'Building of node application is starting ...'
    bat "ls"
    bat "npm install"

}