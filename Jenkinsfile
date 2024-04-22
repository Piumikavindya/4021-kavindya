pipeline {
    agent any
    stages {
        stage ('SCM Checkout'){
            steps{
                retry(3){
                  checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Piumikavindya/4021-kavindya']])
                }
            }
      
        }
         stage('Build Docker Image'){
            steps {
                sh 'docker build -t piumikavindya/4021-kavindya:%BUILD_NUMBER% .'
            }
        
        }
         stage('Docker Image Run'){
            steps{
                sh 'docker run -d -p 5000:3000 piumikavindya/4021-kavindya:%BUILD_NUMBER%'
         }
        }
        stage('Show Running Containers'){
      steps{
        sh 'docker ps'
      }
    }
    
    }
}