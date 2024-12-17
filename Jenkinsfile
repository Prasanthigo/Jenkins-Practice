pipeline {
    agent { node { label 'agent-1' } }  // Run on any available Jenkins agent

    environment {
        PROJECT_NAME = "my-sample-project"
        BUILD_DIR = "build"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out the code..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building the project..."
                sh '''
                mkdir -p ${BUILD_DIR}
                echo "Build completed for ${PROJECT_NAME}" > ${BUILD_DIR}/output.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh '''
                echo "Running some unit tests..."
                sleep 2
                echo "Tests completed successfully!"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the application..."
                sh '''
                echo "Deploying ${PROJECT_NAME}..."
                sleep 1
                echo "Deployment complete."
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Check the logs for errors."
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
