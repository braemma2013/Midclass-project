pipeline {
    agent any
    
    
    stages {
        stage('Checkout') {
            steps {
              checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/braemma2013/Midclass-project.git']])
            }
        }
        
        stage('Build') {
            steps {
              sh 'python3 Flask_web_app.py'
            }
        }
        
        
        stage('post build') {
            steps {
              ansiblePlaybook become: true, disableHostKeyChecking: true, installation: 'Ansible', inventory: 'hosts.ini', playbook: 'flask.yml'
            }
        }
    }
 }















