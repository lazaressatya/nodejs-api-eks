pipeline {
agent any

```
tools {
    nodejs "node"
}

environment {
    IMAGE_NAME = "lazares/node-api"
    TAG = "v1.0-${BUILD_NUMBER}"

    AWS_DEFAULT_REGION = "us-east-1"

    DOCKER_CREDS = "dockerhub-creds"

    GIT_URL = "https://github.com/lazaressatya/nodejs-api-eks.git"

    HELM_RELEASE = "node-api"
    NAMESPACE = "production"
}

stages {

    stage('Checkout Code') {
        steps {
            git branch: 'main', url: "${GIT_URL}"
        }
    }

    stage('Install Dependencies') {
        steps {
            bat 'npm install'
        }
    }

    stage('Run Tests') {
        steps {
            bat 'npm test'
        }
    }

    stage('Build Docker Image') {
        steps {
            bat '''
            docker build -t %IMAGE_NAME%:%TAG% .
            '''
        }
    }

    stage('Push Image to Docker Hub') {
        steps {

            withCredentials([
                usernamePassword(
                    credentialsId: "${DOCKER_CREDS}",
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )
            ]) {

                bat '''
                echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin

                docker push %IMAGE_NAME%:%TAG%

                docker tag %IMAGE_NAME%:%TAG% %IMAGE_NAME%:latest

                docker push %IMAGE_NAME%:latest

                docker logout
                '''
            }
        }
    }

    stage('Deploy using Helm') {
        steps {

            bat '''
            helm upgrade --install %HELM_RELEASE% .\\node-api ^
            --namespace %NAMESPACE% ^
            --create-namespace ^
            --set image.repository=%IMAGE_NAME% ^
            --set image.tag=%TAG%
            '''
        }
    }

    stage('Verify Deployment') {
        steps {

            bat '''
            kubectl get pods -n %NAMESPACE%

            kubectl rollout status deployment/%HELM_RELEASE% -n %NAMESPACE%
            '''
        }
    }
}

post {

    success {
        echo 'Deployment Successful'
    }

    failure {
        echo 'Pipeline Failed'
    }

    always {
        cleanWs()
    }
}
```

}
