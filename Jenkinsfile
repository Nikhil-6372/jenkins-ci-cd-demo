pipeline {
    agent any

    environment {
        IMAGE_NAME = 'nikhil6372/jenkins-ci-cd-demo'
    }

    stages {
        stage('Build Image') {
            steps {
                script {
                    docker.build("${nikhil6372/jenkins-ci-cd-demo}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry(credentialsId: 'dockerhub-credentials') {
                    script {
                        docker.image("${nikhil6372/jenkins-ci-cd-demo}").push()
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
