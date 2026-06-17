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
                sh 'docker pull vnikolajevs/python-greetings-app:latest'
                sh 'docker compose stop greetings-app-dev'
                sh 'docker compose rm -f greetings-app-dev'
                sh 'docker compose up -d greetings-app-dev'
            }
        }

        stage('tests-on-dev') {
            steps {
                echo 'Testing on dev'
                sh 'docker run --rm vnikolajevs/api-tests:latest run greetings-dev'
            }
        }

        stage('deploy-to-stg') {
            steps {
                echo 'Deploying python microservice to stg environment'
                sh 'docker pull vnikolajevs/python-greetings-app:latest'
                sh 'docker compose stop greetings-app-stg'
                sh 'docker compose rm -f greetings-app-stg'
                sh 'docker compose up -d greetings-app-stg'
            }
        }

        stage('tests-on-stg') {
            steps {
                echo 'Testing on stg'
                sh 'docker run --rm vnikolajevs/api-tests:latest run greetings-stg'
            }
        }

        stage('deploy-to-prod') {
            steps {
                echo 'Deploying python microservice to prod environment'
                sh 'docker pull vnikolajevs/python-greetings-app:latest'
                sh 'docker compose stop greetings-app-prod'
                sh 'docker compose rm -f greetings-app-prod'
                sh 'docker compose up -d greetings-app-prod'
            }
        }

        stage('tests-on-prod') {
            steps {
                echo 'Testing on prod'
                sh 'docker run --rm vnikolajevs/api-tests:latest run greetings-prod'
            }
        }
    }
}