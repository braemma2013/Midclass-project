pipeline {
    agent any
    environment {
        FLASK_APP = 'Flask_web_app.py'
    }
    tools {
        git 'Default'
    }
    stages {
        stage('Clone Repository') {
            steps {
              git branch: 'main', credentialsId: '25ccef62-d1ea-4da4-812b-980dfbca4119', url: 'https://github.com/braemma2013/Midclass-project.git'
            }
        }
        
        stage('Install packages') {
            steps {
               sh 'pip install venv'
               sh 'source venv/bin/activate && pip install flask'
               sh 'chmod -R 755 venv'
            }
        }
        
        stage('Build') {
            steps {
              sh 'echo "Building app"'
            }
        }
        
        stage('post build') {
            steps {
              ansiblePlaybook become: true, disableHostKeyChecking: true, installation: 'Ansible', inventory: 'hosts.ini', playbook: 'flask.yml'
            }
        }
    }
 }















