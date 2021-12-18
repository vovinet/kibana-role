pipeline {
    agent any

    stages {
        stage('Change work directory') {
            steps {
                sh 'mkdir kibana_role'
                sh 'cd kibana_role'
            }
        }
        stage('Fetch source code') {
            steps {
                git branch: 'main', credentialsId: 'kisa2', url: 'git@github.com:vovinet/kibana-role.git'
            }
        }
        stage('Install prerequisites') {
            steps {
                sh 'pip3 install -r test-requirements.txt'
            }
        }
        stage('Run molecule') {
            steps {
                sh 'molecule test --scenario-name lite'
            }
        }
    }
}
