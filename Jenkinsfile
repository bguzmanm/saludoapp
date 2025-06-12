pipeline {
    agent any

    tools {
        maven 'maven'
        jdk 'JDK17'
    }

    stages {
        stage('Clonar') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/bguzmanm/saludoapp.git']]])
            }
        }

        stage('Compilar') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Probar') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Empaquetar') {
            steps {
                sh 'mvn package'
            }
        }

        post {
            success {
                echo '🎉 El build fue exitoso'
            }
            failure {
                echo '💥 El build falló'
            }
        }
    }
}