pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh 'docker build -t springboot-demo .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f springboot-container || true
                docker run -d -p 8081:8080 --name springboot-container springboot-demo
                '''
            }
        }
    }

    post {
        success {
            echo "Application deployed on http://localhost:8081"
        }
    }
}
