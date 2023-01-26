pipeline {
    agent any

    stages {
        stage ('Build docker image') {
            steps {
                script {
                    dockerapp = docker.build("catalanmatheus/kube-news:${env.BUILD_ID}", "-f ./src/Dockerfile ./src")
                }
            }
        }
        stage ('Push docker image') {
            steps {
                script {
                    // docker.withDockerRegistry()
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
                        dockerapp.push('laster')
                        dockerapp.push(${env.BUILD_ID})

                    }
                }
            }
        }
    }
}