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
                sh 'mvn clean package'
                ansiblePlaybook playbook: 'ansible/deploy.yml', inventory: 'ansible/hosts.ini'
            }
        }
    }
}

