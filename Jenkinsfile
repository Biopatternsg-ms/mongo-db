pipeline {
    agent any

    environment {
        NETWORK_NAME = 'general-network'
    }

    stages {
        stage('Prepare Network') {
            steps {
                echo "Verifing network"
                sh "docker network create ${NETWORK_NAME} || true"
            }
        }

        stage('Run MongoDB Service') {
            withCredentials([
                credentialsId: 'mongo-db-credentials',
                passwordVariable: 'MONGO_PASSWORD', 
                usernameVariable: 'MONGO_USER'    
            ]) {
                steps {
                    echo 'Starting the MongoDB container and the internal network'
                    sh 'docker compose up -d'
                }
            }
        }
    }
}



