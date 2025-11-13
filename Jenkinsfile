pipeline {
    agent any

    environment {     
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-login') 
    } 

    stages {
        stage('Login to DockerHub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                echo '✅ Login Completed'
            }
        }

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build and Deploy') {
            steps {
                sh """
                cd $WORKSPACE
                ansible-playbook ansible.yml
                """
            }
        }
    }

    post {
        always {
            sh 'docker logout || true'
        }
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
