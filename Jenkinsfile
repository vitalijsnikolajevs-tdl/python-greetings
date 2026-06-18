def deploy(environment) {
    sh 'docker pull vnikolajevs/python-greetings-app:latest'
    sh "docker compose stop greetings-app-${environment}"
    sh "docker compose rm -f greetings-app-${environment}"
    sh "docker compose up -d greetings-app-${environment}"
}

def runTests(environment) {
    sh 'docker pull vnikolajevs/api-tests:latest'
    sh "docker run --network=host --rm vnikolajevs/api-tests:latest run greetings greetings_${environment}"
}

pipeline {
    agent any

    stages {

        stage('build-docker-image') {
            steps {
                echo 'Building python-greetings docker image'
                sh 'docker build -t vnikolajevs/python-greetings-app:latest .'

                echo 'Pushing python-greetings image to docker hub'
                sh 'docker push vnikolajevs/python-greetings-app:latest'
            }
        }

        stage('deploy-to-dev') {
            steps {
                echo 'Deploying python microservice to dev environment'
                script {
                    deploy('dev')
                }
            }
        }

        stage('tests-on-dev') {
            steps {
                echo 'Testing on dev'
                script {
                    runTests('dev')
                }
            }
        }

        stage('deploy-to-stg') {
            steps {
                echo 'Deploying python microservice to stg environment'
                script {
                    deploy('stg')
                }
            }
        }

        stage('tests-on-stg') {
            steps {
                echo 'Testing on stg'
                script {
                    runTests('stg')
                }
            }
        }

        stage('deploy-to-prod') {
            steps {
                echo 'Deploying python microservice to prod environment'
                script {
                    deploy('prod')
                }
            }
        }

        stage('tests-on-prod') {
            steps {
                echo 'Testing on prod'
                script {
                    runTests('prod')
                }
            }
        }
    }
}