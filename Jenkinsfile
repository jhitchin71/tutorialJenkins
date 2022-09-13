pipeline {
    agent any
    parameters {
        booleanParam(name: 'Refresh',
                    defaultValue: false,
                    description: 'Read Jenkinsfile and exit.')
            }
    stages {
           
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
        stage('Integration Test') {
            steps {
                sh 'python3 -m pytest ./main/tests/test_unit.py'
            }
        }
        stage('Build') {
            steps {
                sh 'sudo docker-compose build'
                
             }
        }
        stage('Deploying') {
            steps {
             sh 'sudo ssh -i /home/ubuntu/.ssh/JH_912 -o StrictHostKeyChecking=no ubuntu@172.31.2.230'
             sudo apt install apache2 -y
            }
        }
    }
}
