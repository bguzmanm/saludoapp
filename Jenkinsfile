pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'JDK17'
    }
    stages {
        stages('Clonar') {
            steps {
                git url 'https://github.com/bguzmanm/saludoapp.git'
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