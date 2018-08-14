#!/usr/bin/env groovy
pipeline {
    agent none
    environment {
        API = 'api.system.10.193.26.253.sslip.io'
        CRED = credentials('cf-uaa-admin-cred')
    }
    stages {
        stage('Build') {
            agent {
                docker { image 'node:8.11.3' }
            }
            steps {
                sh 'npm --version'
            }
        }
        stage('cf push') {
            agent {
                docker { image 'chenweien/ubuntu-with-cf' }
            }
            steps {
                sh 'cf login -a $API --skip-ssl-validation -u $CRED_USR -p $CRED_PSW -o wayne-org -s wayne-space'
                sh '''
                    cf zero-downtime-push rails-by-jenkins -f manifest.yml -p .'
                    cf apps
                '''
            }
        }
    }
}
