pipeline {
    agent any

    environment {
        IMAGE_NAME = 'yourdockerhubusername/jenkins-ci-cd-demo'
    }

    stages {
        stage('Build Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry(credentialsId: 'dockerhub-credentials') {
                    script {
                        docker.image("${IMAGE_NAME}").push()
                    }
                }
            }
        }

        stage('Run Container') {
            steps {
                sh "docker run -d -p 5000:5000 ${IMAGE_NAME}"
            }
        }
    }
}
