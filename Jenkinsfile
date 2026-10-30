pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Verify WAR') {
            steps {
                sh 'ls -lh target/myapp.war'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/myapp.war'
            echo 'Build successful'
        }

        failure {
            echo 'Build failed'
        }
    }
}

