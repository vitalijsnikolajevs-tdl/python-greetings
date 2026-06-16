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
            }
        }

        stage('deploy-to-stg') {
            steps {
                echo 'Deploying to stg'
            }
        }

        stage('tests-on-stg') {
            steps {
                echo 'Testing on stg'
            }
        }

        stage('deploy-to-prod') {
            steps {
                echo 'Deploying to prod'
            }
        }

        stage('tests-on-prod') {
            steps {
                echo 'Testing on prod'
            }
        }
    }
}