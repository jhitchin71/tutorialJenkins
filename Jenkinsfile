pipeline {
    agent any
    parameters {
        booleanParam(name: 'Refresh',
                    defaultValue: false,
                    description: 'Read Jenkinsfile and exit.')
            }
    stages {
        stage('update apt cache') {
            steps {
                sh 'sudo apt update'
            }
        }
        stage('install apache') {
            steps {
                sh 'sudo apt install apache2 -y'
            }
        }   
        stage('prune') {
            steps {
                sh 'sudo docker system prune -a -f'
            }
        }
        stage('unit test') {
            steps {
                sh 'python3 -m pytest ./prime/tests/test_unit.py'
            }
        }
        stage('Build') {
            steps {
                sh 'sudo docker-compose build'
            }
        }
    }
}
