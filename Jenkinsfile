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
                    echo "Testing SonarQube token availability"
                    if [ -n "$SONAR_TOKEN" ]; then
                      echo "Sonar token loaded successfully"
                    else
                      echo "Sonar token not found"
                      exit 1
                    fi
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Hello from Jenkins pipeline'
            }
        }
    }
}
