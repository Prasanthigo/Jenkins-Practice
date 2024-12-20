pipeline {
    agent { node { label 'Agent-1' } }  // Run on any available Jenkins agent

    environment {
        PROJECT_NAME = "my-sample-project"
        BUILD_DIR = "build"
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    
        

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out the code..."
                checkout scm
                sh 'printenv'
            }
        }
        stage('Example') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
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
        stage('Example1') {
            environment { 
                AUTH = credentials('centos-agent-1') 
            }
            steps {
                sh 'printenv'
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
        always { 
            echo 'I will always say Hell again!'
        }
    }
}
