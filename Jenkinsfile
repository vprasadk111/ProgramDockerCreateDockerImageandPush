pipeline {
    agent {
        docker { image 'vprasadk/programdockercreatedockerimageandpush:latest' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'docker run -p 5000:5000 -d vprasadk/programdockercreatedockerimageandpush:latest'
            }
        }
    }
}
