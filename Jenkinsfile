pipeline {
  agent any

   tools {nodejs "node"}

    environment {
        IMAGE_NAME = "lazares/node-api"
        TAG = "v1.0-${BUILD_NUMBER}"
        AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
        AWS_DEFAULT_REGION = 'us-east-1'

        // Jenkins credentials IDs
        DOCKER_CREDS = "dockerhub-creds"
        KUBE_CONFIG  = "kubeconfig-file"

        // GitHub Repo
        GIT_URL = "https://github.com/lazaressatya/nodejs-api-eks.git"
    }

    stages {

        stage('Checkout Code from GitHub') {
            steps {
                git branch: "main", url: "${GIT_URL}"
            }
        }
     
    stage('Node JS Build') {
      steps {
        sh 'npm install'
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
         
     stage('Deploy to Kubernetes') { 
        steps  {
            
             sh ''' kubectl apply -f manifests/namespace.yaml 
                    kubectl apply -f manifests/deployment.yaml 
                    kubectl apply -f manifests/service.yaml 
                    kubectl apply -f manifests/ingress.yaml 
                    kubectl apply -f manifests/hpa.yaml 
                    kubectl apply -f manifests/servicemonitor.yaml 
                    kubectl apply -f manifests/ne tworkpolicy.yaml 
                    kubectl rollout status deployment/node-api -n production 
                '''
        }
      }
    }
}