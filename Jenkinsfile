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
stage('Build Project') {
steps { sh 'mvn clean install -DskipTests' }
}
stage('Selenium Test') {
steps { sh 'mvn test' }
}
}
}
post {
success { echo 'All Selenium tests passed!' }
failure { echo 'Selenium test failed.' }
}
}
