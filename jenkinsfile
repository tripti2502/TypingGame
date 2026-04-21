pipeline {
    agent any

    environment {
        IMAGE = "typinggame"
        CONTAINER = "typinggame"
    }

    stages {

        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker rm -f $CONTAINER || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d -p 8081:80 --name $CONTAINER $IMAGE
                '''
            }
        }
    }
}
