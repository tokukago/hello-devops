pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code checked out by Jenkins'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                sh 'ansible-playbook -i inventory.ini deploy-hello.yml'
            }
        }

        stage('Verify') {
            steps {
                sh 'docker exec web1 ls -l /tmp/hello-devops-1.0.0.jar'
            }
        }
    }
}
