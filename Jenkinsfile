pipeline {
    agent any
    
    
    stages {
        stage('Checkout') {
            steps {
              checkout scmGit(branches: [[name: '*/main']], extensions: [cleanBeforeCheckout()], userRemoteConfigs: [[credentialsId: '25ccef62-d1ea-4da4-812b-980dfbca4119', url: 'https://github.com/braemma2013/Midclass-project.git']])
            }
        }
        
        stage('Build') {
            steps {
              git branch: 'main', credentialsId: '25ccef62-d1ea-4da4-812b-980dfbca4119', url: 'https://github.com/braemma2013/Midclass-project.git'
            }
        }
        
        
        stage('post build') {
            steps {
              ansiblePlaybook become: true, disableHostKeyChecking: true, installation: 'Ansible', inventory: 'hosts.ini', playbook: 'flask.yml'
            }
        }
    }
 }















