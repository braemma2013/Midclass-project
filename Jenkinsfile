pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/BOMAURIEL/Flaskapp.git']]])
            }
        }
        
        stage('Starting Ansible') {
            steps {
      ansiblePlaybook credentialsId: 'fireubuntu', disableHostKeyChecking: true, inventory: '/var/lib/jenkins/workspace/jenkins-pipe/hosts.ini', playbook: '/var/lib/jenkins/workspace/jenkins-pipe/deploy2.yml'
            }
        }
    }
 
}
