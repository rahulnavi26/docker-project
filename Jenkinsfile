pipeline {
agent any

stages {

    stage('Build Backend Docker Image') {
        steps {
            sh 'docker build -t fastapi-app ./backend'
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

    stage('Run Backend Container') {
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
        echo 'Backend Deployment Successful!'
    }

    failure {
        echo 'Backend Deployment Failed!'
    }
}

}
