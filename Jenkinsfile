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
                echo Building Docker Image
                docker build -t vinay314/cicd-e2e:1 .
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                    echo Logging into Docker Hub...
                    echo "$PASSWORD" | docker login -u "$USERNAME" --password-stdin

                    echo Pushing Docker Image...
                    docker push vinay314/cicd-e2e:1
                    '''
                }
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
