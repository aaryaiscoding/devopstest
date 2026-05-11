pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/aaryaiscoding/devopstest.git'
            }
        }

        stage('Check Java and Maven') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Install Chrome & Xvfb') {
            steps {
                sh '''
                    sudo apt-get update
                    sudo apt-get install -y google-chrome-stable xvfb
                '''
            }
        }

        stage('Run Selenium Tests with Display') {
            steps {
                sh '''
                    Xvfb :99 -screen 0 1920x1080x24 &
                    export DISPLAY=:99
                    mvn clean test
                '''
            }
        }
    }

    post {
        success {
            echo 'All Selenium tests passed!'
        }
        failure {
            echo 'Selenium test failed.'
        }
    }
}
