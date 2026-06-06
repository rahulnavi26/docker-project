pipeline {
agent any

```
stages {

    stage('Clone Repository') {
        steps {
            git branch: 'main',
                url: 'https://github.com/rahulnavi26/https://github.com/rahulnavi26/docker-project.git'
        }
    }

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t fastapi-app .'
        }
    }

    stage('Run Container') {
        steps {
            sh '''
            docker stop fastapi-container || true
            docker rm fastapi-container || true
            docker run -d --name fastapi-container -p 8000:8000 fastapi-app
            '''
        }
    }
}

post {
    success {
        echo 'Pipeline executed successfully!'
    }

    failure {
        echo 'Pipeline failed!'
    }
}
```

}
