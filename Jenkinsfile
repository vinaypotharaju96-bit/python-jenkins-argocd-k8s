pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vinaypotharaju96-bit/python-jenkins-argocd-k8s.git'
            }
        }

        stage('Build Docker') {
            steps {
                sh '''
                echo Build Docker Image
                docker build -t vinaydockerhub/cicd-e2e:1 .
                '''
            }
        }

        stage('Push the artifacts') {
            steps {
                sh '''
                echo Push Docker Image
                docker push vinaydockerhub/cicd-e2e:1
                '''
            }
        }

        stage('Checkout K8S manifest SCM') {
            steps {
                sh 'echo Checkout K8S repo step'
            }
        }

        stage('Update K8S manifest & push to Repo') {
            steps {
                sh 'echo Update manifest step'
            }
        }
    }
}
