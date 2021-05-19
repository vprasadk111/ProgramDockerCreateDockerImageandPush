pipeline {
    agent {
        docker { image 'vprasadk/programdockercreatedockerimageandpush:latest' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'python --version'
            }
        }
    }
}
