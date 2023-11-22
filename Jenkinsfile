pipeline {
    agent any

    stages {
        stage('Build app') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/shrutikalani19/jenkinsPipeline.git']])
            }
        }
        
        stage('Build Docker Image'){
            steps{
                script{
                    bat 'docker build -t jenkinsdocker .'
                }
            }
        }
        
        stage('Rename Image Tag'){
            steps{
                script{
                    bat 'docker tag jenkinsdocker shrutikalani19/jenkinsdockerapp:image1'
                }
            }
        }
        
        stage('Push Image to docker Hub'){
            steps{
                script{
                    bat 'docker login -u shrutikalani19 -p Shruti@docker19'
                    bat 'docker push shrutikalani19/jenkinsdockerapp:image1'
                }
            }
        }
    }
}
