stage('SonarQube Analysis') {
    steps {
        sh '''
            mvn clean verify sonar:sonar \
              -Dsonar.login=$SONAR_TOKEN
        '''
    }
}
