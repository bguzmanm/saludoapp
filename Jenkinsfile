pipeline {
    agent any
    tools {
        maven 'Maven 3.9.10'
        jdk 'openjdk 24.0.1'
    }
    stages {
        stages('Clonar') {
            steps {
                git 'https://github.com/bguzmanm/saludoapp.git'
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