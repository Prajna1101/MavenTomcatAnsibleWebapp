pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Prajna1101/MavenTomcatAnsibleWebapp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
         stage('Deploy') {
            steps {
                sh 'ansible-playbook -i ansible/hosts.ini ansible/deploy.yml'
            }
        }
    }
}

