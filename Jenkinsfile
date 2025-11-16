pipeline {
    agent { label 'docker-host' }

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
                steps {
                    withCredentials([
                        credentialsId: 'mongo-db-credentials',
                        passwordVariable: 'MONGO_PASSWORD', 
                        usernameVariable: 'MONGO_USER'    
                    ]) {
                        echo 'Starting the MongoDB container and the internal network'
                        sh 'docker compose up -d'
                    }
                }
            }
        }
    }
}



