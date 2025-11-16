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
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: '06a41492-8765-49c4-91f6-b759260140f0', 
                        usernameVariable: 'MONGO_USER',
                        passwordVariable: 'MONGO_PASSWORD'
                    )
                ]) {
                    echo 'Starting the MongoDB container and the internal network'
                    echo "Validación: El usuario de MongoDB es: ${env}"
                    sh 'docker compose up -d'
                }
            }
        }
    }
    
}



