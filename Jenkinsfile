pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/braemma2013/Midclass-project.git']]])
            }
        }
        
        stage('Starting Ansible') {
            steps {
      ansiblePlaybook become: true, disableHostKeyChecking: true, installation: 'Ansible', inventory: 'hosts.ini', playbook: 'flask.yml'
            }
        }
    }
 
}















