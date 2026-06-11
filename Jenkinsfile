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
                bat "docker build -t %IMAGE_NAME%:%TAG% ."
            }
        }

     stage('Push Image to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: DOCKER_CREDS,
                    usernameVariable: "DOCKER_USER",
                    passwordVariable: "DOCKER_PASS"
                )]) {

                    bat '''
                    docker login -u %DOCKER_USER% -p %DOCKER_PASS%
                    docker push %IMAGE_NAME%:%TAG%
                    docker logout
                    '''
                }
            }
        }

   

    stage('Verify Deployment') {
        steps {

            bat '''
            withCredentials([file(credentialsId: KUBE_CONFIG, variable: "KUBECONFIG")]) {

                     bat '''
                    set KUBECONFIG=%KUBECONFIG%

                    kubectl config current-context
                    kubectl get nodes

                    kubectl create namespace website --dry-run=client -o yaml | kubectl apply -f -
                    kubectl apply -f namespace.yaml
                    kubectl apply -f deployment.yaml
                    kubectl apply -f service.yaml
                        

                    kubectl set image deployment/k8sstatic-web-deployment ^
                    k8sstatic-webs=%IMAGE_NAME%:%TAG% -n website

                    kubectl rollout status deployment/k8sstatic-web-deployment -n website
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
