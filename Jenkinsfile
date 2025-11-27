pipeline {
    enviroment{
        DOCKERHUB_CREDENTIALS = credentials('copy jenkins id for dockerhub cred')
    }
    agent {
         label 'km'
    }
    stages {
        stage('git') {
            steps {
                git 'link'
                //
            }
        }
        stage('docker') {
            steps {
               sh 'sudo docker login -u $(DOCKERHUB_CREDENTIALS_USR) -p $(DOCKERHUB_CREDENTIALS_PSW)'
               sh 'sudo docker build /home/ubuntu/jenkins/workspace/jobname -t intellipaat/2025'
               sh 'sudo docker push intellipaat/2025'
                //
            }
        }
        stage('k8s') {
            steps {
                sh 'kubectl apply -f deploy.yml'
                sh 'kubectl apply -f service.yml'
                //
            }
        }
    }
}