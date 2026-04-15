pipeline {
    agent any

    environment {
        SONAR_TOKEN = credentials('sonar-token')
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
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
                    java -version
                    mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:4.0.0.4121:sonar \
                      -Dsonar.projectKey=jenkins-test \
                      -Dsonar.host.url=http://localhost:9000 \
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
