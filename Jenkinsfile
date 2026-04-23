pipeline {
    agent any

    environment {
        IMAGE = "typinggame"
        CONTAINER = "typinggame"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh '/usr/bin/docker build -t $IMAGE .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                /usr/bin/docker rm -f $CONTAINER || true
                /usr/bin/docker run -d -p 8081:80 --name $CONTAINER $IMAGE
                '''
            }
        }
    }
}
