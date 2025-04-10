pipeline {
    agent any

    environment {
        LANG = 'en_US.UTF-8'
        LC_ALL = 'en_US.UTF-8'
    }

    tools {
        maven 'Maven' // Match this with your Jenkins Maven installation
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Aditi-Sinha-2003/MymavenWebApp01.git'
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
                sh 'ansible-playbook playbook.yml -i hosts.ini'
            }
        }
    }
}
