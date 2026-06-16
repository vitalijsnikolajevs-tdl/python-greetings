pipeline {
    agent any

    stages {

        stage('build-docker-image') {
            steps {
                echo 'Building docker image'
            }
        }

        stage('deploy-to-dev') {
            steps {
                echo 'Deploying to dev'
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