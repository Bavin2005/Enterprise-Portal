pipeline {
    agent any
    environment {
        COMPOSE_PROJECT_NAME = "minienterpriseportal"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Pipeline triggered by merge to: ${env.GIT_BRANCH}"
                checkout scm
            }
        }
        stage('Setup Environment') {
            steps {
                withCredentials([file(credentialsId: 'portal-env-file', variable: 'ENV_FILE')]) {
                    sh """
                        cp "\${ENV_FILE}" .env
                    """
                }
                echo 'Environment file ready'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker images...'
                sh 'docker-compose build'
                echo 'All images built successfully'
            }
        }


        stage('Deploy') {
            steps {
                sh '''
                    echo "Removing any conflicting containers..."
                    docker rm -f portal_mongodb portal_backend1 portal_backend2 portal_frontend 2>/dev/null || true

                    echo "Stopping old containers..."
                    docker-compose down

                    echo "Starting updated containers..."
                    docker-compose up -d

                    echo "Reconnecting Jenkins to portal network..."
                    docker network connect minienterpriseportal_portal_network jenkins 2>/dev/null || true

                    echo "Waiting for health checks..."
                    sleep 20

                    echo "Container status:"
                    docker-compose ps

                    echo "Cleaning up old unused images..."
                    docker image prune -f
                '''
            }
        }
    }

    post {
        always {
            sh 'rm -f .env'
        }

        success {
            echo '''
            ================================================
               DEPLOYMENT SUCCESSFUL
               Your app is live with the latest changes!
            ================================================
            '''
        }

        failure {
            echo '''
            ================================================
               PIPELINE FAILED
               The previous version is still running.
               Check the stage logs above for the error.
            ================================================
            '''
        }
    }
}
