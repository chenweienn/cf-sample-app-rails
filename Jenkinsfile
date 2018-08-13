pipeline {
    agent any
    stages {
        stage('test') {
            steps {
                echo "AHA!"
            }
        }
        stage('test2') {
            steps {
                sh 'cf plugins'
            }
        }
    }
}
