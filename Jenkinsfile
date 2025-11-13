pipeline {
    agent any
    
    environment {     
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-login') 
    } 
    
    stages {
        stage('Login to DockerHub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                echo 'Login Completed'
            }
        }
        
        stage('Build and Deploy') {
            steps {
                sh """
                cd /home/mohamed-sarhan
                ansible-playbook ansible.yml
                """
            }
        }
    }
    
}

