pipeline {
    agent any
    environment {     
             DOCKERHUB_CREDENTIALS= credentials('dockerhub-login') 
            } 
    stages {
        stage('login-dockerhub') {
            steps {
                    sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo -S docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        echo 'Login Completed'
            }
        }
        stage('Test') {
            steps {
                //
            }
        }
        stage('Deploy') {
            steps {
                //
            }
        }
    }
}

