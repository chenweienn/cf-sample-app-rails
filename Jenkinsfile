pipeline {
    agent any
    stages {
        stage('cf login') {
            steps {
                cf login -a api.system.10.193.26.253.sslip.io --skip-ssl-validation -u admin -p VH0839o04wT_nZCV6zGLX60ELSCnvNOa -o wayne-org -s wayne-space
            }
        }
        stage('cf push') {
            steps {
                sh 'cf zero-downtime-push rails-by-jenkins -f manifest.yml -p .'
            }
        }
        stage('cf apps') {
            steps {
                sh 'cf apps'
            }
        }
    }
}
