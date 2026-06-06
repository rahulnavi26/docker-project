pipeline {
agent any

stages {

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t fastapi-app .'
        }
    }

    stage('Stop Existing Container') {
        steps {
            sh '''
            docker stop fastapi-container || true
            docker rm fastapi-container || true
            '''
        }
    }

    stage('Run Container') {
        steps {
            sh '''
            docker run -d \
            --name fastapi-container \
            -p 8000:8000 \
            fastapi-app
            '''
        }
    }
}

post {
    success {
        echo 'Deployment Successful!'
    }

    failure {
        echo 'Deployment Failed!'
    }
}

}
