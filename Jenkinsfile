pipeline {
    agent any

    environment {
        SONAR_TOKEN = credentials('sonar-token')
    }

    stages {
        stage('Checkout Test') {
            steps {
                echo 'Jenkinsfile loaded successfully from GitHub'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                sh '''
                    mvn clean verify sonar:sonar \
                      -Dsonar.projectKey=jenkins-test \
                      -Dsonar.host.url=http://host.docker.internal:9000
                      -Dsonar.login=$SONAR_TOKEN
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage completed'
            }
        }
    }
}
