pipeline {
    environment {
        DockerhubUri = 'https://index.docker.io/v1/'
        DockerhubCred = 'Dockerhub'
        DockerhubBuildTag = 'pwang009/azure-vote-app'
    }
    agent any
    stages {
        stage('Deploy Image') {
            steps {
                script {
                    dir("$WORKSPACE/azure-vote") {
                        image = docker.build DockerhubBuildTag + ":$BUILD_NUMBER"
                        docker.withRegistry( '', DockerhubCred ) {
                            image.push()
                        }
                    }
                }
            }
        }
    }
}
